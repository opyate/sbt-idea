Requirements
------------

* [sbt](https://github.com/harrah/xsbt/wiki) 0.11.2. NOTE: For sbt 0.7.x version of the plugin, see [branch sbt-0.7](https://github.com/mpeltonen/sbt-idea/tree/sbt-0.7)


Installation
------------

Add the following lines to ~/.sbt/plugins/build.sbt or PROJECT_DIR/project/plugins.sbt

    resolvers += "sbt-idea-repo" at "http://mpeltonen.github.com/maven/"

    addSbtPlugin("com.github.mpeltonen" % "sbt-idea" % "1.0.0")

Usage
-----

### Basic project

Use the `gen-idea` sbt task to create Idea project files.

### Project with dependencies

If you have two sbt projects A and B, and A depends on B, then use the `gen-idea` sbt task on Project A to create Idea project files for both projects.

The projects need to be set up in the following way:

*Project A:*

    import sbt._

    object A extends Build {
      lazy val A = Project("A", file(".")) aggregate(B) dependsOn(B)
      lazy val B = RootProject(file("../B"))
    }

*Project B:*

    import sbt._

    object B extends Build {
      lazy val B = Project("B", file("."))
    }

### Sources and javadocs

By default, classifiers (i.e. sources and javadocs) of dependencies are loaded if found and references added to Idea project files. If you don't want to download/reference them, use command 'gen-idea no-classifiers'.

Configuration settings
----------------------

TODO...

License
-------

Licensed under the New BSD License. See the LICENSE file for details.
