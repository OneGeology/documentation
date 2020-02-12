Welcome to OneGeology documentation!
==================================================

This Documentation provides detailed instuctions on

- How to provide data to the OneGeology Portal
- Using the OneGeology Portal
- Using data from OneGeology on other platforms

Contents:

.. toctree::
   :maxdepth: 1
   :glob:

   overview
   providingdata
   portal
   appendices
   authors

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

Documenting the Documentation
=============================

This documentation is written in ReStructured Text hosted on GitHub pages, built using Sphinx via Gitub Actions CI/CD. 

To setup 

- follow Sphinx quickstart
- save to GitHub repo
- edit repo settings to enable GitHub pages from gh-pages branch. 
- Create .github/workflows/gh-pages.yml

.. code-block:: bash
		
	name: github pages

	on:
  push:
    branches:
      - master

	jobs:
		make-pages:
		  runs-on: ubuntu-latest
		  steps:
		  - uses: actions/checkout@v1

		  - name: select python version
		    uses: actions/setup-python@v1
		    with:
		      python-version: '3.7'

		  - name: install dependencies
		    run: |
		      python -m pip install --upgrade pip
		      python -m pip install sphinx
		      python -m pip install sphinx_rtd_theme
		  - name: build documentation
		    run: |
		      cd docs
		      make html
		      touch _build/html/.nojekyll
		  - name: deploy
		    uses: peaceiris/actions-gh-pages@v2
		    env:
		      ACTIONS_DEPLOY_KEY: ${{ secrets.ghpagesdk }}
		      PUBLISH_BRANCH: gh-pages
		      PUBLISH_DIR: docs/_build/html
			  
- Create SSH keys in Linux/Putty
- In repo settings>deploy add a=deply key such as "ghpagesdk" and copy/paste public key hash
- In repo settings>secrets add a secret key with same name "ghpagesdk" and copy/paste private key hash. 
- make a commit to the master brach and should all be working. 

## Source files

Original documentation was a collection of rst and html files. THe rst files were copied and merged together to the current format in this repository. HTML files were convertef using pandoc as below:

::

   pandoc --extract-media=appendixb -s -t rst http://www.onegeology.org/wmsCookbook/appendixB.html -o appendixb.rst


