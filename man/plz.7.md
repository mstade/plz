plz
===

Synopsis
--------

This is the design document for plz, the friendly helper. Plz is a tool used to automate some of the common tasks of project development, no matter what the project is. No doubt a lofty goal, which means care must be taken in the design of plz so it doesn't overstep its boundaries.

This document attempts to explain the overarching design principles that govern the development of plz.

Description
-----------

Plz does:

- Download files, and move them around
- Execute programs (in context)
- Read and understand documentation

Plz does not:

- Manage dependencies
- Know what a version is
- Care what the context is
- Require configuration files

Plz has many things in common with package management tools; however, such such programs often tend to dictate structure and impose constraints on projects to the point where they require significant buy-in. For instance, most have specific configuration files, often expressed in or based upon a programming language. Plz does not do this, but rather inspects the project to learn what it is and what plz can do to help.

Plz does have to impose *some* constraints, in order for this to be possible. For instance, it assumes that documentation is in plain text format. It also assumes that the plain text can be parsed into [Markette] documents. From this, it can analyze the documentation and try to understand the structure and properties of the project.

[Markette]: https://github.com/mstade/markette

The documentation is also used as a way to extend plz. Like many other CLI applications, its interface is a host program that delegates operations to other programs. These other programs may not always be known to plz beforehand, and might be discovered when plz learns about the project. An example of this may be a software project, which has a test suite. While reading about the project, plz may learn that there is in fact a test suite, and how to execute it and collect the results from it. Plz is a really fast learner.

This method of extending plz, is why it isn't inherently a package manager, but could be used as one. This extensibility is also what makes plz usable in many kinds of projects, and isn't specific to a subset of technologies or situations.

Plz is also not a build tool, however it can execute such tools within the context of a project. Generally, a project should be able to explain how to build itself. What plz does, is to realize that not all projects are made equal, but that many projects may share characteristics. Thus, one of the features of plz is to download things that can be executed as though it was run from the project's root folder. Plz is designed to follow general CLI conventions, so will understand things such as background processes, streams, signal handling, options parsing, permissions, etc.

Plz doesn't know what it's executing, but it promises to always do so in a consistent and deterministic manner. This greatly simplifies the automation of project tasks.

Plz doesn't really dictate what the programs it is executing should do, nor how they should do their work; but it does try to set a precendence in terms of what makes a good CLI program. Plz is idealistic in thinking that the world would be a better place if more programs would take care to understand humans, the way plz tries to.

See also
--------

TBD