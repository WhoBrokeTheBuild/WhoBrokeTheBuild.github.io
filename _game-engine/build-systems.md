---
layout: post
title: Build Systems
excerpt: An overview of C++ Build Systems, and the reasons behind choosing CMake.
date: 2020-05-06 00:00:00 -0400
category: game-engine
tags: 
- Game Engine
- Programming
- C++
- CMake
- Git
---

A logical first step when building a complex software project, like a Game Engine, is choosing a build system. This post will lay out my requirements, and then go through the build systems that I've tried.

The code used in all of the examples for this section can be found here:  
[https://github.com/WhoBrokeTheBuild/build-systems/tree/main](https://github.com/WhoBrokeTheBuild/build-systems/tree/main)


## Requirements

* **Cross-Platform**, support for Linux, Windows, OSX. Preferably native support.
* **External Dependency Management**, support for finding and/or building the libraries needed by the engine.
* **Target Dependency Chains**, support multiple libraries and executables, linked together in specific ways.
* **Tests**, support for building and running unit tests, integration tests, etc.
* **Asset Management**, support for processing and/or copying assets such as shaders, textures, models, etc.
* **Packaging**, support for adding packaging targets to build `.deb`, `.zip`, etc.
* **Performance**, how fast can it configure the project and build my software.
* **Distributed Configuration**, support for distributing build system code throughout the project folder structure. Not being limited to one build file for everything.
* **Includes/Macros**, support for re-using build system code for all demos, libraries, etc.
* **Run Targets**, support for adding targets to run the demos, tests, etc. Preferably with the ability to run them through tools like `gdb`, `valgrind`, etc.
* **Conditionals**, support for some form of an `if` statement, used to add targets if certain tools or libraries are found, and to add config based on your Operating System.

## [Make](/game-engine/build-systems-make.html)

## Autotools

## Meson

## Visual Studio

## CMake

{% include game-engine-series.html %}