---
autogenerated: true
title: Overview of Fiji's source code
layout: page
categories: Development
description: test description
---

This page will give you an idea how Fiji's source code is organized. Every directory referred to is relative to the Fiji root, i.e. the directory into which you [cloned fiji.git](Git_mini_howto#Cloning).

The Fiji launcher
-----------------

The [Fiji Launcher](Fiji_Launcher) is now called *ImageJ launcher* and lives {% include github org='imagej' repo='imagej-launcher' label='in its own repository' %}. It is [built by Travis CI](https://travis-ci.org/imagej/imagej-launcher).

The plugins
-----------

The plugins served from Fiji's update site are all [Open Source](Why_Closed-Source_Is_Wrong). The source code lives {% include github org='fiji' repo='' label='on GitHub' %}, in repositories reflecting the name of the *.jar* file generated from the source code. Example: the source code for *Fiji\_Plugins.jar* lives in https://github.com/fiji/Fiji_Plugins.

The only special rule applies for plugins whose file names end in an underscore: that underscore will be stripped. Example: the sources of *Arrow\_.jar* are stored in https://github.com/fiji/Arrow.

All of our plugins are maintained as [Maven](Maven) projects; this allows developers to build the code with their integrated development environment of choice.

Plugins maintained in Maven projects consist of

1.  a pom.xml file in the top-level directory
2.  the Java sources in the *src/main/java/* directory, and
3.  the *plugins.config* file in *src/main/resources/*

If the plugin sources contain unit tests, their sources are in *src/test/java/* so that the generated test classes will not be included in the final *.jar* file.

Libraries
---------

Most libraries are available as regular [Maven](Maven) dependencies (you can [search for them on Maven Central](http://search.maven.org/)).

Submodules
----------

Fiji used to maintain relationships with projects developed outside the *fiji.git* repository via Git submodules. This proved too cumbersome and too unintuitive for the affected parties.

All submodule couplings are now replaced by proper [Maven](Maven) dependency management.

The Fiji Build system
---------------------

Fiji used to have its home-brewn build system. We switched to using [Maven](Maven) in 2012, though.

For convenience, there is a {% include github org='scijava' repo='minimaven' label='""Mini Maven""' %} project that allows building Fiji without a full-blown Maven; however, for serious development, real Maven, or even better, Eclipse or Netbeans is recommended.

For backwards-compatibility, *Mini Maven* can be called via **./Build.sh** in the top-level directory of a *fiji.git* checkout. Despite the name, it does not really build anything, but only draws in all Fiji components as [Maven](Maven) dependencies.

The *bin/* directory
--------------------

Quite a few tasks -- such as committing a new submodule or sources for a plugin, or releasing a new version of Fiji -- are performed by scripts. These scripts live in the *<Fiji-root>/bin/* subdirectory.

Some of these scripts are shell scripts, others are Jython scripts with special {% include wikipedia title='Shebang (Unix)' text='shebang'%} lines which trigger them to be called with the current Fiji launcher.


