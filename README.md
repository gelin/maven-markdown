[Maven Site Plugin](https://maven.apache.org/components/plugins/maven-site-plugin/) is able to generate HTML pages from files with [Markdown](https://en.wikipedia.org/wiki/Markdown) markup.
This is an example how to use it.

Main ideas
----------

* Markdown files should have `.md` extension and be placed under `src/site/markdown` folder and it's subfolders.
* Maven Site Plugin together with [Doxia module for Markdown](https://maven.apache.org/doxia/doxia/doxia-modules/doxia-module-markdown/) do the work. Run `mvn site` to generate.
* Each `.md` file is transformed into corresponding `.html` file, so links between pages should be set to URLs ending with `.html`.

See [pom.xml](pom.xml) file.

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

Multimodule project
-------------------

`mvn site` command generates a separate site for each Maven module.
To bring all modules together to one bigger site you should, for example, run `mvn site:stage` command.
It will produce the solid site of all modules in `target/staging` folder.

You need to define [\<distributionManagement\>](https://maven.apache.org/pom.html#Site_Distribution) section in [pom.xml](pom.xml) for `site:stage` to work.

An Maven reporting plugins runs separately for each module.
But then, during preparation of multimodule site the Maven reports are additionally run in a special aggregate mode to bring together and summarize report values from each module.
Not all report plugins work here correctly.
The report plugins require special configuration for aggregate mode, it's done differently for different plugins.

On multimodule site the menu for the module is merged from menu of the parent module and the current module.
Some care on inheritance of each menu item is required here.

> With `mvn site:deploy` command Maven is even able to upload site to a remote server.

See [Maven documentation](https://maven.apache.org/plugins/maven-site-plugin/examples/multimodule.html) for more details.