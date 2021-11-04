---
title: PSI, Landing Page
altLangPage: /fr/
dateModified: 2021-08-06
description: "Home page describing all the components of the Canada.ca theme, named GCWeb."
lang: en
---

{::nomarkdown}
<div class="row">
	<div class="col-md-7 col-lg-8">
		<p>The page templates and design patterns below comprise a reference implementation of the <a href="https://design.canada.ca">Canada.ca design system</a>, including the mandatory requirement of the Content and Information Architecture (C&amp;IA) Specification. Government of Canada departments and agencies can contribute additional patterns and templates via <a href="https://github.com/wet-boew/GCWeb">GCWeb github repository</a>.</p>
	</div>
	<div class="col-xs-12 col-md-auto pull-right">
		<p><a href="https://github.com/wet-boew/GCWeb/archive/v9.5.0.zip" class="btn btn-primary">Download GCWeb theme <strong>v9.5.0</strong></a><br />
			<small>(<time>{{ page.dateModified | %F }}</time> - <a href="https://github.com/wet-boew/gcweb/releases/tag/v9.5.0">Release notes</a>)</small></p>
	</div>
</div>

<ul class="colcount-md-2">
	<li><a href="docs/index.html">GCWeb v5 Summary and others technical notes</a></li>
	<li><a href="docs/implementing.html">Implementing GCWeb</a></li>
	<li><a href="#components">Components</a></li>
	<li><a href="#templates">Templates</a></li>
	<li><a href="méli-mélo/méli-mélo-en.html">Méli-mélo features</a></li>
	<li><a href="thématique/gc-thématique-en.html">GC promotional thematic</a></li>
	<li><a href="#sitesglobal">Sites and global functionality</a></li>
</ul>

<p><small>Found an C&amp;IA implementation issue or you want to contribute at their development, let us know by submiting <a href="https://github.com/wet-boew/GCWeb/issues/new?title=C&amp;IA%20implementation%20error:%20">GCweb issue</a>, sending <a href="https://github.com/wet-boew/GCWeb/pulls">pull request</a> or by participating at one of our <a href="https://wet-boew.github.io/wet-boew-documentation/index-en.html#wet-boew-code-sprint">WET-BOEW weekly Tuesday code sprint</a>.</small></p>

{:/}

## Projects

### Regulatory Metadata Labelling
The regulatory metadata labelling project aims to reqork the way that public servants deal with regulations and regulatory changes.

The project will have long lasting effects on the way that regulatory work is conducted.

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
