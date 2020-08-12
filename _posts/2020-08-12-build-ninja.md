---
published: true
title: Ninja (build tool)
tags: build make
---
> Where other build systems are high-level languages, Ninja aims to be an assembler. - [The Ninja build system](https://ninja-build.org/manual.html)

# [Ninja](https://github.com/ninja-build/ninja)
Some explicit non-goals:
- convenient syntax for writing build files by hand. You should generate your ninja files using another program. This is how we can sidestep many policy decisions.
- built-in rules. Out of the box, Ninja has no rules for e.g. compiling C code.
- build-time customization of the build. Options belong in the program that generates the ninja files.
- build-time decision-making ability such as conditionals or search paths. Making decisions is slow.



> When we first started porting Chrome away from just Windows, we intended to use Scons to build Chrome on all our platforms. But early on in development I discovered that Scons, despite its admirable goals of correctness and ease of use, was quite slow — it could take 40 seconds from starting Scons before it decided to build some source... I eventually ported our Linux build to plain Makefiles... Build performance is a combination of many factors: the build system needs to compute what needs to be done, the compiler takes time to compile files, the linker takes time to link. Each of these can be improved;...Makefiles got our incremental builds down to a handful (10-20) of seconds... I thought I'd try making a very simple build system; conceptually very similar to Make, but without hardly any features. And with just some preliminary profiling I got the Chrome build startup to under one second. - [Ninja, a new build system](http://neugierig.org/software/chromium/notes/2011/02/ninja.html)
