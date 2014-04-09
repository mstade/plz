plz
===

This is the design document for plz, the friendly helper. Plz is a tool used to automate some of the common tasks of project development, no matter what the project is. No doubt a lofty goal, which means care must be taken in the design of plz so it doesn't overstep its boundaries.

Plz is a:

- File manager
- Downloader of things
- Runner of things

Plz is *not* a:

- Package manager
- Build tool
- Programming tool

These things seem very counter intuitive. How can plz be both a file manager and downloader of things, while not being a package management system? How can it not be a build tool if its stated goal is to automate common things?

It is true that plz aims to please, and will download things and place things in places, where they probably should be. However, these are the primitive tasks of a package manager, which is generally much more opinionated. Plz will put files where you tell it to; it won't tell you where the files are placed and then let you [deal with it]. If you don't explicitly tell it, it will figure it out implicitly.

[deal with it]: http://i.imgur.com/xe2OsXx.gif

Plz does not, by itself, know how to build anything. Indeed, plz just represents knowledge of how to download things and put things in places. Those things may well be things that build other things, presumably from the things in your project, however that's up to the build thing. Plz will download this for you, and place it where you want it, and then if you so ask it will also run the thing, with all necessary paths in place such that the thing can make reasonable assumptions about what's going on. Because plz is designed to run in UNIX like environments, it also knows how to be nice and stream input and ouput, and make sure relevant flags and what not are passed along as they should.

While plz lends itself well to programming projects, it does not assume the project has anything to do with programming. In fact, so long as your project is a folder, that contains files and possibly other folders, it will gladly perform tasks you ask of it. The only thing plz requires, is a bit of documentation, such that it can understand what it needs to understand about your projects.

This is the core tenet of plz: it acts on human readable documentation. Plz is configured through documentation, that contain just enough structure so as to be meaningful. It assumes the documentation is written in [Markette], or a sufficiently compatible format – if it looks and smells like Markette, plz can probably make sense of it.

[Markette]: https://github.com/mstade/markette