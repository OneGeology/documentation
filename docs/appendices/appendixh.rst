==============================================================
Using the MS4W Apache http server as a reverse proxy to Tomcat
==============================================================

.. container::
   :name: outer_container

   .. container::
      :name: content

      .. container:: fullwidth

         .. rubric:: Appendix H: Using the MS4W Apache http server as a
            reverse proxy to Tomcat
            :name: appendix-h-using-the-ms4w-apache-http-server-as-a-reverse-proxy-to-tomcat
            :class: technical_progress_side_menu

         To serve a OneGeology WMS through the OneGeology Portal that
         service must be served using port 80; the default port for any
         http web service. If you are already serving another web
         service on port 80 on the same server (such as a GeoNetwork
         spatial data metadata catalogue for example), then you will
         need to use a different port number for the existing service.
         In itself this shouldn’t be too difficult to do, however this
         might cause problems for your customers due to restrictive
         firewall rules that prevent them consuming any web service not
         served on the standard web port number. One way around this is
         to merge the services together; another possibility (as
         detailed below) is to use the Apache HTTP web server as a
         reverse proxy, that is, to handle all requests to the second
         service as if that service was coming from the MS4W Apache
         service. The user is thus unaware that there is more than one
         web service. Each service proxied in this way runs on a
         separate port number, and may still be accessed directly on
         that port (depending on your configuration), but it is also
         available as if it were running on port 80.

         `Comprehensive information on configuring
         Apache <http://httpd.apache.org/docs/2.2/urlmapping.html>`__
         (http://httpd.apache.org/docs/2.2/urlmapping.html).

         The first step is to change the `port
         numbers <http://www.iana.org/assignments/port-numbers>`__
         (http://www.iana.org/assignments/port-numbers) on which your
         other web servers work; in this example we have two other web
         services (a Tomcat based web service which we will run on port
         8080, and a jetty based web service which we will run on port
         8008). Note that both these ports are recognized alternate
         ports for http traffic but they may not be open to such traffic
         in your corporate firewall.

         Now we need to edit the Apache HTTP server httpd.conf file. If
         you have installed the MS4W apache http server as part of the
         ms4w-and-exemplar-data.zip download this would be located at:
         c:\ms4w\Apache\conf\httpd.conf.

         Check that the following modules are uncommented (by removing
         the # sign from the line start).

         Change

         | #LoadModule proxy_module modules/mod_proxy.so
         | #LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
         | #LoadModule proxy_http_module modules/mod_proxy_http.so

         To:

         | LoadModule proxy_module modules/mod_proxy.so
         | LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
         | LoadModule proxy_http_module modules/mod_proxy_http.so

         Note, we have used mod_proxy here as it is included with the
         Apache HTTP Server binaries, but you could use other proxy
         modules such as mod_jk if desired.

         Now you need to add or uncomment the following directives (as
         appropriate for your configuration file); we suggest adding
         these directives at the end of the file for clarity.

         | TraceEnable off
         | #Important for security!!

         | ProxyRequests Off
         | #This sets up the reverse proxy, if ’ ProxyRequests On’ is
           set you have a forward proxy.

         ProxyPreserveHost On

         Now for each service (or set of pages within a service) that
         you wish to proxy you need to add the following set of
         directives:

         A <Proxy> or a <ProxyMatch> block to restrict access to your
         resources, a ProxyPass directive (to map that web service into
         the local server URL space), and a ProxyPassReverse directive
         (which lets Apache adjust the URL in the Location,
         Content-Location and URI headers on HTTP redirect responses).

         Examples:

         #. Adding a reverse proxy to the BRGM OneGeology Europe
            connector for WP6 WMS. This connector runs on the Tomcat
            server running on port 8080, but will appear to be running
            as part of the Apache http service running on port 80.

            | <Proxy /1GEconnector>
            | Order deny,allow
            | Allow from all
            | </Proxy>

            ProxyPass /1GEconnector http://localhost:8080/1GEconnector

            ProxyPassReverse /1GEconnector
            http://localhost:8080/1GEconnector

         #. Adding a reverse proxy to our Jetty web service which is
            running a GeoNetwork catalogue. The Jetty service is running
            on port 8008 but will appear to be running as part of the
            Apache http service running on port 80. You would normally
            be able to use ’ localhost’ or ’ 127.0.0.1’ to specify a web
            service running on the same physical server as your Apache
            web server, but in this instance Jetty has been configured
            to only accept requests from the server IP (194.66.252.156).

            | <Proxy /geonetwork>
            | Order deny,allow
            | Allow from all
            | </Proxy>

            ProxyPass /geonetwork http://194.66.252.156:8008/geonetwork

            ProxyPassReverse /geonetwork
            http://194.66.252.156:8008/geonetwork

         #. Adding a reverse proxy to our Jetty web service which is
            running an Intermap mapping client (used by the GeoNetwork
            catalogue). The Jetty service is running on port 8008 but
            will appear to be running as part of the Apache http service
            running on port 80.

            | <Proxy /intermap>
            | Order deny,allow
            | Allow from all
            | </Proxy>

            ProxyPass /intermap http://194.66.252.156:8008/intermap

            ProxyPassReverse /intermap
            http://194.66.252.156:8008/intermap

         #. Adding a reverse proxy to our cocoon service, which we need
            to run our WFS. The cocoon service runs on the Tomcat server
            running on port 8080, but will appear to be running as part
            of the Apache http service running on port 80. In this
            example we are using a ProxyMatch block, which allows us to
            use a regular expression to map the allowable paths to
            cocoon.

            | <ProxyMatch http://[^/]*/cocoon/*>
            | Order deny,allow
            | Allow from 127.0.0.1
            | </ProxyMatch>

            ProxyPass /cocoon http://127.0.0.1:8080/cocoon/

            ProxyPassReverse /cocoon http://127.0.0.1:8080/cocoon/

         That’s it as far as the Apache http server is concerned, but
         you may also wish to configure your other web servers so that
         they always proxy their http content through Apache

         To do this in Tomcat, you need to modify a Connector block in
         the server.xml configuration file as below:

         Change:

         | <Connector
         | port=“8080”
         | protocol=“HTTP/1.1”
         | connectionTimeout=“20000”
         | redirectPort=“8443” />

         To:

         | <Connector
         | port=“8080”
         | protocol=“HTTP/1.1”
         | connectionTimeout=“20000”
         | redirectPort=“8443”
         | proxyName=“yourserver.org”
         | proxyPort=“80” />

         ProxyName: is the domain name or IP of the standard (Apache
         HTTP Server) web service and can be omitted if you are running
         your Tomcat service on the same server as the http service.

         To do this in Jetty you need to make a similar change in the
         jetty.xml file
