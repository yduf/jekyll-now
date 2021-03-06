---
published: true
title: FUSE Filesystem
tags: software filesystem
---
> FUSE (Filesystem in Userspace) is an interface for userspace programs to export a filesystem to the Linux kernel. The FUSE project consists of two components: the fuse kernel module (maintained in the regular kernel repositories) and the libfuse userspace library (maintained in this repository). libfuse provides the reference implementation for communicating with the FUSE kernel module. - [libfuse](https://github.com/libfuse/libfuse)

## [Pros/cons](https://unix.stackexchange.com/a/4170/192991)

## Mounting special
- [Automount](https://www.linux.com/news/automounting-fuse-filesystems/)
- [fstab](https://stackoverflow.com/questions/1554178/how-to-register-fuse-filesystem-type-with-mount8-and-fstab)

## [Building your own filesystem](https://github.com/libfuse/libfuse/#building-your-own-filesystem)

libfuse offers two APIs: a "high-level", synchronous API, and a "low-level" asynchronous API. In both cases, incoming requests from the kernel are passed to the main program using callbacks. 
- When using the high-level API, the callbacks may work with file names and paths instead of inodes, and processing of a request finishes when the callback function returns. 
- When using the low-level API, the callbacks must work with inodes and responses must be sent explicitly using a separate set of API functions.

The documentation of the API functions and necessary callbacks is mostly contained in the files:
- [include/fuse.h](https://github.com/libfuse/libfuse/blob/master/include/fuse.h) (for the high-level API)
- and [include/fuse_lowlevel.h](https://github.com/libfuse/libfuse/blob/master/include/fuse_lowlevel.h) (for the low-level API). 

An autogenerated html version of the API is available in the [doc/html](http://libfuse.github.io/doxygen) directory. 

## Tutorials
- [Develop your own filesystem with FUSE](https://developer.ibm.com/technologies/linux/articles/l-fuse/) - [archived](https://web.archive.org/web/20180216233455/https://www.ibm.com/developerworks/linux/library/l-fuse/)
- [Writing a FUSE Filesystem: a Tutorial](https://www.cs.nmsu.edu/~pfeiffer/fuse-tutorial/)
- [Writing a FUSE filesystem in Python](http://thepythoncorner.com/dev/writing-a-fuse-filesystem-in-python/)
	- [Writing a FUSE filesystem in Python](https://www.stavros.io/posts/python-fuse-filesystem/)
    	- [fusepy 3.0.1 ](https://pypi.org/project/fusepy/)
    	- [python-fuse](https://github.com/libfuse/python-fuse)
- [Write a filesystem with FUSE](https://engineering.facile.it/blog/eng/write-filesystem-fuse/)

- [Option Parsing](https://github.com/libfuse/libfuse/wiki/Option-Parsing) - You may parse the arguments and manually tell FUSE about them or you may ask FUSE to parse the command line for you.
	- [hello.c](https://libfuse.github.io/doxygen/hello_8c.html)
	- [FUSE option](https://man.openbsd.org/FUSE_ARGS_INIT.3)
		- [fuse_opt_parse()](https://libfuse.github.io/doxygen/fuse__opt_8h.html#a539ef1f571c34f516c60c4cbe2901c0e)
	- [Options](http://manpages.ubuntu.com/manpages/precise/man8/mount.fuse.8.html#options)
		- [default options (fuse_parse_cmdline())](https://man.openbsd.org/fuse_parse_cmdline.3#fuse_parse_cmdline)

## Example FUSE
- [MirrorFS](https://github.com/Manel18/MirrorFS) - Just mirror the operations done on the mount directory to another directory.
- [trapexit/mergerfs](https://github.com/trapexit/mergerfs) - a union filesystem geared towards simplifying storage and management of files across numerous commodity storage devices. It is similar to mhddfs, unionfs, and aufs.

## [Documentation]((https://www.cs.hmc.edu/~geoff/classes/hmc.cs137.202001/homework/fuse/fuse_doc.html))
- [**init**](https://www.cs.hmc.edu/~geoff/classes/hmc.cs137.202001/homework/fuse/fuse_doc.html#init-args) - The initialization function accepts a fuse_conn_info structure, which can be used to investigate and control the system's capabilities.
- [**readdir**](https://www.cs.hmc.edu/~geoff/classes/hmc.cs137.202001/homework/fuse/fuse_doc.html#readdir-details) - Return one or more directory entries (struct dirent) to the caller. This is one of the most complex FUSE functions.

## [Debugging tips](https://stackoverflow.com/a/15443069/51386)
There are a couple features of FUSE that can make it difficult to debug: it normally runs in the background (which means it detaches from stdin/out) and is multithreaded (which can introduce race conditions and is more complicated to debug with gdb). Luckily, both features can be disabled (see [**doc**](https://www.cs.hmc.edu/~geoff/classes/hmc.cs137.202001/homework/fuse/fuse_doc.html):
- Use the -d or -f switch to keep your application in the foreground. This will make your printf lines work.
- Use the -s switch to disable multithreading. Disabling multithreading will limit performance, but will also hide certain bugs (race conditions), simplify the use of gdb, and ensure printf output is readable (when multiple threads call printf at about the same time their output can get mixed up).

### [FUSE MODULES (STACKING)](http://manpages.ubuntu.com/manpages/precise/man8/mount.fuse.8.html#fuse%20modules%20(stacking))

Modules are filesystem stacking support to high level API. Filesystem modules can be built into libfuse or loaded from shared object.

## Version
see also Fuse [Changelog](https://github.com/libfuse/libfuse/blob/master/ChangeLog.rst)

Latest version is 3, bug fix + API clean up

{% highlight bash %}
sudo apt-get install libfuse3-dev
{% endhighlight %}

using a previous version may lead to warning:
{% highlight bash %}
fuse: warning: library too old, some operations may not not work
{% endhighlight %}

## Perf
 
> We start with a detailed explanation of FUSE's design and implementation - [Performance and Resource Utilization of FUSE User-Space File Systems](https://dl.acm.org/doi/fullHtml/10.1145/3310148)

- [To FUSE or Not to FUSE: Performance of  User-Space File Systems](https://www.usenix.org/system/files/conference/fast17/fast17-vangoor.pdf)

## Binding
- **Crystal** [Papierkorb/fuse](https://github.com/aljelly/fuse) / redefined struct incorreclty generated by libgen
- **Dlang** [fuse.d](https://code.dlang.org/packages/fuse-d) / [github](https://github.com/seeseemelk/fuse-d) 
	- [dfuse (umaintained)](https://github.com/dlang-community/dfuse)
