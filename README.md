[Maven Site Plugin](https://maven.apache.org/components/plugins/maven-site-plugin/) is able to generate HTML pages from files with [Markdown](https://en.wikipedia.org/wiki/Markdown) markup.
This is example how to use it.

Main ideas
----------

* Markdown files should have `.md` extension and be placed under `src/site/markdown` folder and it's subfolders.
* Maven Site Plugin together with [Doxia module for Markdown](https://maven.apache.org/doxia/doxia/doxia-modules/doxia-module-markdown/) do the work. Run `mvn site` to generate.
* Each `.md` file is transformed into corresponding `.html` file, so links between pages should be set to URLs ending with `.html`.

See [pom.xml](pom.xml) file for details and comments.

mvn site
--------

`mvn site` command creates the module site in `target/site` folder.
These are static HTML pages which can be served by any HTTP server. 
