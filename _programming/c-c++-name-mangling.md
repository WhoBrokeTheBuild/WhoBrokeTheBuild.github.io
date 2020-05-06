---
layout: post
title: Name Mangling
excerpt: A simple explanation of C++ name mangling.
date: 2016-06-28 00:00:00 -0400
category: programming
tags: 
- Programming
- C
- C++
---

Something you've probably heard of if you've ever written any mixed C++/Assembly code 
is Name Mangling. You probably learned that, to call any C++ functions from Assembly 
code you need to append an extern "C" like so:

```c
extern "C" func();
```

But what exactly is Name Mangling, and what does it look like? We're going to do a
little experiment to find out. Take this code, and compile it as both C and C++ code,
like so:

```c
#include <stdio.h>

void doSomething()
{
    printf("Hello, World\n");
}

int main(int argc, char** argv) 
{
    doSomething();
}
```

```shell
$ gcc -o testc test.c
$ g++ -o testcpp test.cpp
```

Now we're going to get the dissassembly of each, and look for our function "doSomething"

```shell
$ objdump -d testc
```

In this mess of information you'll probably find something like this:

```
0000000000400540 <doSomething>:
  400540:	55                   	push   %rbp
  400541:	48 89 e5             	mov    %rsp,%rbp
...
```

That is the function you wrote in C, converted to assembly, using the exact name that you 
gave it. Now lets do the same for the C++ one.

```shell
$ objdump -d testcpp
```

You'll probably find something that looks similiar to this:

```
0000000000400600 <_Z11doSomethingv>:
  400600:	55                   	push   %rbp
  400601:	48 89 e5             	mov    %rsp,%rbp
...
```

So, the reason C++ does this is to allow a few things. The first is called function
overloading, which allows you to use several functions of the same name, so long as they
have different parameters / return values. The second is template functions, which are
functions generated using C++'s metaprogramming `template<class T>` directive. And finally,
it allows for functions to be worked into classes, so you could have two functions named
the same thing but belonging to different classes (which is really just an extension of
function overloading). 

The downside is that you can't know what the function is called anymore. So if you 
wanted to call the function from assembly code, you wouldn't be able to reliabily, even
if you looked up the name that C++ generated for that section, it's liable to change.
This is easily worked around however, by adding the extern "C" before the function name
as we mentioned before, which causes the function definition to be treated the same as 
it would be in C. This disables the ability for function overloading though.

So that is a further look into C++'s name mangling.