---
layout: post
title: "Building a Game Engine"
excerpt: An introduction to building a Game Engine for fun and ~profit~ practice.
date: 2020-05-05 22:00:00 -0400
tags: 
- Game Engine
- Programming
- OpenGL
- DirectX
- Vulkan
- C++
- Python
- CMake
- Git
- Linux
- Windows
- OSX
---

If you are writing a Game Engine in 2020, it's likely for one of three reasons:

* You want to learn how they work
* You are making a very unique game, that needs a specialized engine
* You haven't figured out how to install Unreal Engine (here's a [link](https://docs.unrealengine.com/en-US/GettingStarted/Installation/index.html))

I fall into the first bucket.

Like many people, I've always loved tearing things apart to see what makes them tick. Game Engines are complex pieces of software, that require many techniques not found in other modern software. Things such as: manual memory management, high amounts of parallelization, and access to low-level graphics/audio/input APIs. 

This blog will catalogue my attempts to make a Game Engine from scratch. The choices I make, the reasons behind them, the things that went poorly. I, in no way shape or form, claim to be an expert on the subject. However I have a healthy interest, and a lot of experience as a hobbiest.

The engine will be written in `C++`, and the scripting will be done in `Python 3`.

The build system will be written in `CMake`.

The engine will be cross platform, compiling for `Linux`, `Windows`, `OSX`, and ideally `Android`.

The intent is to support `OpenGL` as the primary graphics API, with additional support for `DirectX` and `Vulkan`.

The windowing framework will be `SDL2`, which will also be used for the keyboard/mouse/controller input.

As with all of my previous attempts at writing an engine, it will be named `Dusk`.

[https://github.com/WhoBrokeTheBuild/Dusk](https://github.com/WhoBrokeTheBuild/Dusk)