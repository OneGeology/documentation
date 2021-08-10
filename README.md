# OneGeology documentation for users and service providers.

Source files are written in [reStructuredText](http://docutils.sourceforge.net/rst.html) and built into HTML pages using the [readthedocs](http://www.readthedocs.org) documentation generator automatically.

If you have Docker installed you can use the example Dockerfile.sphinx to build the documentation locally.

```
# To build the container
docker build -f Dockerfile.sphinx -t sphinxrtd .

# To build the documentation using the built container
cd docs
docker run --rm -v $PWD:/docs sphinxrtd make html
```

Documentation is published to https://onegeology.github.io/documentation/

This documentation replaces old documentation on http://www.onegeology.org and the separate WMS, WFS and WCS Cookbook PDF's.
