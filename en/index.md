---
title: PSI, Landing Page
altLangPage: /fr/
dateModified: 2021-11-04
description: "Home page describing all the components of the Canada.ca theme, named GCWeb."
lang: en
---

Welcome to the landing page for the Public Sector Innovation team!

We are a group of public servants looking to revolutionize the way that work is done in the public service. We are going to innovate!

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum consectetur malesuada feugiat. Suspendisse potenti. Suspendisse auctor nec tortor sed varius. Sed eu orci lobortis, commodo libero eu, facilisis tortor. Vestibulum sed neque dapibus, molestie sem et, blandit augue. Sed in accumsan magna. Donec in neque quis lacus dictum commodo vitae ut est. Proin in consectetur leo. In ultricies rutrum libero, in malesuada nisi auctor eu. In malesuada, ligula nec bibendum elementum, odio nisi consequat neque, vitae posuere metus odio nec erat. Donec sit amet nisi volutpat, lobortis magna ut, elementum libero. Vestibulum semper eu nibh dictum vestibulum. Sed tempor eget metus non malesuada. Nullam semper nunc ut neque pretium, sit amet suscipit sapien fermentum. Curabitur consectetur sagittis gravida.

<a href="./partnership" class="btn btn-primary">Work with <strong>US!</strong></a>

* [Projects](#projects)
* [Lessons Learned](#lessons-learned)
* [Parnership](./partnership)
* [Work With Us!](./contact)

## Projects

### Regulatory Metadata Labelling
The regulatory metadata labelling project aims to reqork the way that public servants deal with regulations and regulatory changes. The project will have long lasting effects on the way that regulatory work is conducted!

To find out more about the project or look at some of the results view the links below:
* Demonstration
	* [Demonstration (Authentication Required, Please Contact)](https://dev.psinnovation.com/)
* Code
	* [Open Source Code](https://www.github.com)
* Dataset
	* [Open Data Set](https://open.canada.ca/en)

## Developping for GCWeb

Install NodeJS

### Building GCweb

* Build a local development version: `grunt` or `grunt debug`
* Run code quality check: `grunt test`
* Build production files: `grunt dist`
* Compile and assemble méli-mélo:
	* Run local: `grunt méli-mélo`
	* Run from compiled dist: `grunt méli-mélo-runLocal`
	* Run from wet-boew sites : `grunt méli-mélo-remote`
* Regenerate site web content: `grunt site-contents`
	* `_data/components.json`
	* `_data/sites.json`
	* `_data/templates.json`
	* `_wetboew-demos/**`

### Run GCWeb wetsite locally

Ensure that you have builded GCWeb first

After your are running docking container or the docker composer you will be able to access your local website at: `http://localhost:4000`

Build Dockerfile locally

```
docker build -t jekyll-with-env-options .
```

Run your image
```
grunt debug

docker run -it --rm -v "$PWD":/usr/src/app -p "4000:4000" --env JEKYLL_OPTIONS='--config _config.yml,_localJekyll.yml' jekyll-with-env-options
```

#### alternative with docker-compose

This version leverage the remote theme wet-beoew/gcweb-jekyll. This equivalent if you run with gh-pages through your own GCWeb repository.

```
docker-compose up
```

### Run the continous integration and deployment script locally

Install ACT - [https://github.com/nektos/act](https://github.com/nektos/act)

Github fork needed:

* [wet-boew/gcweb](https://github.com/wet-boew/gcweb)
* [wet-boew/gcweb-jekyll](https://github.com/wet-boew/gcweb-jekyll)
* [wet-boew/gcweb-compiled-demos](https://github.com/wet-boew/gcweb-compiled-demos)
* [wet-boew/themes-dist](https://github.com/wet-boew/themes-dist)
* [wet-boew/themes-cdn](https://github.com/wet-boew/themes-cdn)

Run the continuous deployment script

```
act -f deploy-gcweb -s my_token=<XXXXXXXXXXXXXX> -s my_username="<GITHUB USERNAME>" - my_email="<GITHUB HANDLE>@users.noreply.github.com" -a <GITHUB HANDLE>
```

Where:
* `<GITHUB USERNAME>`: Your name, like "John Doe"
* `<GITHUB HANDLE>`: Your github id
* `<XXXXXXXXXXXXXX>`: Your personal access token with access to public repository

### Refresh your github pages with the latest theme changes

You can make a commit to your site and it will get regenerated with the latest version of the jekyll theme. Alternatively, the following curl command will told github to regenerate your site.

```
curl -u <GITHUB HANDLE>:<XXXXXXXXXXXXXX> -X POST https://api.github.com/repos/<GITHUB HANDLE>/<GITHUB REPOSITORY>/pages/builds
```

Where:
* `<GITHUB HANDLE>`: Your github id
* `<XXXXXXXXXXXXXX>`: Your personal access token with access to public repository
* `<GITHUB REPOSITORY>`: Your web site github repository, like "jekyll-website"

Note: A manual update is required if you have specified a version for your jekyll remote theme in your `config.yml` file.
