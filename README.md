# OneGeology documentation for users and service providers.

The source files in this repository are used to build documentation for OneGeology users and service providers which is published to https://onegeology.github.io/documentation/.

Source files are written in [reStructuredText](http://docutils.sourceforge.net/rst.html) and built into HTML pages using the [Sphinx](https://www.sphinx-doc.org) documentation generator with the [Read the Docs](http://www.readthedocs.org) theme.

Some of the reStructuredText was converted from pre-existing HTML files using pandoc as below:

```sh
pandoc --extract-media=appendixb -s -t rst https://onegeology.org/wmsCookbook/appendixB.html -o appendixb.rst
```

## Building the documentation locally

If you have Docker installed you can use the example Dockerfile.sphinx to build the documentation locally. 

```sh
# To build the container
docker build -f Dockerfile.sphinx -t sphinxrtd .

# To build the documentation using the built container
cd docs
docker run --rm -v $PWD:/docs sphinxrtd make html
```

Otherwise you should follow the [Sphinx documentation](https://www.sphinx-doc.org) to set up a local build system and then add the sphinx_rtd_theme.

## Publication of changes to main site

The source reStructuredText files are transformed using Sphinx via Gitub Actions CI/CD to web pages hosted on GitHub pages. When changes are merged into the master branch the [GitHub Actions](https://github.com/features/actions) configured in [.github/workflows/gh-pages.yml](.github/workflows/gh-pages.yml) create the content of the [gh-pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#publishing-sources-for-github-pages-sites) branch.

### Process for initial set up of publishing workflow

- follow Sphinx quickstart
- save to GitHub repo
- edit repo settings to enable GitHub pages from gh-pages branch. 
- Create [.github/workflows/gh-pages.yml](.github/workflows/gh-pages.yml)		  
- Create SSH keys in Linux/Putty
- In repo settings>deploy add a=deply key such as "ghpagesdk" and copy/paste public key hash
- In repo settings>secrets add a secret key with same name "ghpagesdk" and copy/paste private key hash. 
- make a commit to the master brach and should all be working. 

