Example code from the [OpenGL 4.0 Shading Language Cookbook][cookbook]
=========================================================

Example programs from David Wolff's [OpenGL 4.0 Shading Language Cookbook][cookbook], 1st Edition.  The source code has been forked from the author's original repository just before it was updated for the second edition.  This repository is for folks having the first edition.

Requirements
-------------
To build these examples, you'll need:

* The latest version of the Unofficial OpenGL Software Development Kit ([GLSDK][]).
* [premake4][] from [Industrious One][].
* [GLM][] 0.9.3+, in order to build the examples in Chapter 8.  The latest version of _GLSDK_ includes version 0.9.4 of _GLM_.  Updating to a higher version of _GLM_ is easy but isn't mandatory. Download the latest version of _GLM_.  Remove the existing `glm` directory in _GLSDK_ and replace it with the contents of the _GLM_ archive.  Make sure to change the directory name to just `glm`.
  
Compiling the examples
----------------------
These examples have been fully tested on Windows with [MSYS2][] and Visual Studio 2010 Express.

1.  Install the _GLSDK_ by following the instructions on their web site.  In the process, you'll also install _premake4_.  For our purposes, only three libraries in the SDK need to be built: _glload_, _freeglut_ and _glimg_.  Here's a gist:
    +  Go to `GLSDK` directory and run `premake4 gmake` or `premake4 vs2010`.
    +  Now go to `glload` directory and run `make`. Do the same for `freeglut` and `glimg` directories.
2.  You've the GLSDK ready; now edit `premake4.lua` in this repository's root directory to make the variable `glsdk_lua` point to your _GLSDK_'s `links.lua` file.
3.  Run `premake4 gmake` to create the make files (or) `premake4 vs2010` to generate the project and solution files.
4.  Run `make` if you've MSYS2. If you chose Visual Studio then open the solution, and build!

If you've a problem with any of these, [report issues][] accordingly.

From the Author
===============

Changes from the book
------------------------
At the time the book was written, I thought that using _Qt_ would make the examples quite portable and easy to compile within _Qt Creator_.  Unfortunately, _Qt Creator_ has changed since the time of the writing of the book.  It has become more unwieldy to install, and in my experience has become extremely slow to boot. In addition, it is not widely used.

Secondly, since the time of the book's writing, I have experienced problems with _GLEW_ under a 4.0 core profile.  When doing some research it appears that there are some fundemental issues with _GLEW_ and core profiles.

Due to the above issues, and to make the code more available and hopefully easier to use, I have ported the code over to use _GLLoad_ and _FreeGLUT_ via the _GLSDK_.

The major changes are listed below:
* Dropped dependence on _Qt_.
* Uses _FreeGLUT_, _GLM_, _GLLoad_, and _GLImage_ via the _GLSDK_.
* Dropped dependence on _libnoise_ for Chapter 8 examples.  Instead, uses the noise functions available in _GLM_ > 0.9.3.

TODO
----
* Currently, the noise examples (Chapter 8) don't look quite right due to the move to _GLM_.  Fix noise examples (chapter 8) to look better.

[GLM]: http://glm.g-truc.net
[GLSDK]:  http://glsdk.sourceforge.net
[premake4]:  http://premake.github.io/
[Industrious One]: http://industriousone.com/premake
[MSYS2]: http://www.sourceforge.net/p/msys2/wiki/MSYS2%20installation/
[ghcookbook]:  http://github.com/daw42/glslcookbook
[cookbook]: http://www.packtpub.com/opengl-4-0-shading-language-cookbook/book
[report issues]: http://github.com/legends2k/glslcookbook/issues
