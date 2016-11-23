[Maven Site Plugin](https://maven.apache.org/components/plugins/maven-site-plugin/) is able to generate HTML pages from files with [Markdown](https://en.wikipedia.org/wiki/Markdown) markup.
This is example how to use it.

Main ideas
----------

* Markdown files should have `.md` extension and be placed under `src/site/markdown` folder and it's subfolders.
* Maven Site Plugin together with [Doxia module for Markdown](https://maven.apache.org/doxia/doxia/doxia-modules/doxia-module-markdown/) do the work. Run `mvn site` to generate.
* Each `.md` file is transformed into corresponding `.html` file, so links between pages should be set to URLs ending with `.html`.

See [pom.xml](pom.xml) file for details.

mvn site
--------                                                                                         

`mvn site` command creates the module site in `target/site` folder.
These are static HTML pages which can be served by any HTTP server. 

Skin
----

Default Maven site skin looks too oldy. To add another skin ([Fluido](http://maven.apache.org/skins/maven-fluido-skin/), which uses [Twitter Bootstrap](https://en.wikipedia.org/wiki/Bootstrap_(front-end_framework))) you need to create [site.xml](src/site/site.xml) file in `src/site` folder with some definitions.

Menu
----

Skin have some parameters. Most important are to configure left side and top bar and menu.

It's possible to add standard Maven reports (like dependencies, tests, checkstyle or anymore [configured](https://maven.apache.org/pom.html#Reporting) for the project) to the menu. It's possible to add links to submodules or parent project in multimodule Maven project. It's possible to add links to any pages (generated from Markdown) to the menu. Also menu allows to add any external links into an "External Links" submenu.

See some examples in [site.xml](src/site/site.xml).

See more details in [skin](http://maven.apache.org/skins/maven-fluido-skin/) and [site descriptor](http://maven.apache.org/doxia/doxia-sitetools/doxia-decoration-model/decoration.html) documentation.

