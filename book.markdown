# Why learn C?

It drives the world and is the foundation to pretty much everything in the modern programming world.  C programmers have built most of the major tools, applications, programming langauges using it.

|Compilers|Virtual Machines|Operating Systems|Databases|Tools|Embedded|
|:---:|:---:|:---:|:---:|:---:|:---:|
|C++  |AWK       |Android|DB2          |Animation     |Appliances |
|D    |BrainFuck |BSD    |MySQL        |Drawing       |Controllers|
|GO   |.NET      |iOS    |MS SQL Server|Game Engines  |Drivers    |
|LUA  |JAVA      |Linux  |Oracle       |Web Browsers  |Firmware   |
|JAI  |Javascript|Mac OS |PostgreSQL   |Machinery     |
|ODIN |PERL      |Solaris|             |Data Pipelines|
|RUST |PHP       |Unix   |             |Robotics      |
|SWIFT|Python    |Windows|             |Shell         |
|     |R         |       |             |Vehicles      |

C is also extremely portable which is why it drives so many things.  The GCC compiler supports 70+ platforms and several architectures.  All of the code examples and C sources in this document will be largely focused on Linux and Windows development.  MinGW has been used for validation of sources on Windows, you can get it [here](https://sourceforge.net/projects/mingw/files/latest/download).  A general how to install and configure the path can be found [here](https://youtu.be/guM4XS43m4I). Unlike Unix-like environments GCC does not come installed by default on the Windows platforms. You can also turn on the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/) and use the Microsoft App Store to install a Unix-Like operating system and use GCC natively.  If you're on a Linux or non-windows platform, this document assumes you have a decent command of that evironment.

This document exists for the sole purpose of furthing a dialogue on modern programming in C using GCC for the C Programming Server on Discord 

# index

[Introduction](#introduction)
[

[testing](#testing)

```C
#include <stdio.h>

int main() {
  puts("Hello World!");
  return 0;
}
```

# testing
[jump to index](#index)
