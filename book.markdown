# Why learn C?

It drives the world and is the foundation to pretty much everything in the modern programming world.  Some examples of this are below.

|Compilers|Virtual Machines|Operating Systems|Databases|Tools|Embedded|
|:---:|:---:|:---:|:---:|:---:|:---:|
|[C++](https://isocpp.org/)  |[AWK](https://www.gnu.org/software/gawk/manual/gawk.html)       |[Android](https://developer.android.com/)|[DB2](https://www.ibm.com/products/db2-database)          |[Animation](https://www.blender.org/)     |[Internet of Things](https://github.com/aws/aws-iot-device-sdk-embedded-C) |
|[D](https://dlang.org/)    |[BrainFuck](https://esolangs.org/wiki/Brainfuck) |[BSD](https://www.bsd.org/?)    |[MySQL](https://www.mysql.com/)        |[Drawing](https://www.adobe.com/)       |[Imaging](http://www.imagesystems.se/)|
|[GO](https://golang.org/)   |[.NET](https://dotnet.microsoft.com/)      |[iOS](https://www.apple.com/ca/ios)    |[MS SQL Server](https://www.microsoft.com/en-ca/sql-server/sql-server-2019)|[Game Engines](https://developer.valvesoftware.com/wiki/Goldsource)  |[Drivers](http://www.qnx.com/developers/docs/6.5.0/index.jsp?topic=%2Fcom.qnx.doc.ddk_en%2Fbookset.html)    |
|[LUA](https://www.lua.org/)  |[JAVA](https://www.java.com/en/)      |[Linux](https://www.linux.org/)  |[Oracle](https://www.oracle.com/index.html)       |[Game Engines](https://handmadehero.org/)  |[Firmware](https://en.wikipedia.org/wiki/Firmware)   |
|[JAI](https://valueinbrief.blogspot.com/2021/02/jai-language.html)  |[Javascript](https://www.javascript.com/)|[Mac OS](https://www.apple.com/ca/macos/) |[PostgreSQL](https://www.postgresql.org/)   |[Machinery](https://github.com/grbl/grbl)     |
|[ODIN](https://odin-lang.org/) |[PERL](https://www.perl.org/)      |[Solaris](https://www.oracle.com/ca-en/solaris/solaris11/)|             |[Data Pipelines](https://www.khronos.org/opengl/wiki/Rendering_Pipeline_Overview)|
|[RUST](https://www.rust-lang.org/) |[PHP](https://www.php.net/)       |[Unix](https://unix.org/)   |             |[Robotics](https://www.firstinspires.org/robotics/frc)      |
|[SWIFT](https://developer.apple.com/swift/)|[Python](https://www.python.org/)    |[Windows](https://www.microsoft.com/en-ca/windows)|             |[Shells](https://www.gnu.org/software/bash/)        |
|     |[R](https://www.r-project.org/about.html)         |       |             |[Vehicles](https://en.wikipedia.org/wiki/Intel_8051)      |


C is also extremely portable, which is why it drives so many things.  The [GCC Compiler](https://gcc.gnu.org/) supports 70+ platforms and several architectures.  All of the code examples and C source code in this document will be largely focused on Linux and Windows development.  You can find the base manual for GCC [here](https://gcc.gnu.org/onlinedocs/). MinGW has been used for validation of sources on Windows, you can get it [here](https://sourceforge.net/projects/mingw/files/latest/download).  A general how to install MinGW and configure the path can be found [here](https://youtu.be/guM4XS43m4I). Unlike Unix-like environments, GCC does not come installed by default on Windows platforms. You can also turn on the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/) and use the Microsoft App Store to install a Unix-Like operating system and use GCC natively.  If you're on a Linux or non-windows platform, this document assumes you have a decent command of that evironment.

This document exists for the sole purpose of furthing a dialogue on modern programming in C using GCC for the [C Programming Server](https://discord.gg/KydfXPfpYK) on [Discord](https://discord.com/).

# index

[Chapter 1: A Tutorial Introduction](#chapter-1-a-tutorial-introduction)\
[Part 1: Data Types](#part-1-data-types)\
[⠀⠀Basic Type](#basic-types)\
[⠀⠀⠀⠀Integer Types](#integer-types)\
[⠀⠀⠀⠀Floating Point Types](#floating-point-types)\
[⠀⠀⠀⠀Enumerated Types](#enumerated-types)\
[⠀⠀Derived Types](#derived-types)\
[⠀⠀⠀⠀Arrays](#arrays)\
[⠀⠀⠀⠀Pointers](#pointers)\
[⠀⠀⠀⠀Structures and Unions](#structures-and-unions)\
[⠀⠀⠀⠀Functions](#functions)\
[⠀⠀⠀⠀Type Definitions](#type-definitions)\
[⠀⠀⠀⠀Void](#void)\
[⠀⠀Basic Code Examples](#basic-code-examples)\
[⠀⠀⠀⠀Example 1: Variable Declarations](#example-1-variable-declarations)\
[⠀⠀⠀⠀Example 2: Type Definitions](#example-2-type-definitions)\
[⠀⠀⠀⠀Example 3: Structures](#example-3-structures)\
[⠀⠀⠀⠀Example 4: Structures (Bad Form)](#example-4-structures-bad-form)\
[⠀⠀⠀⠀Example 5: Structures](#example-5-structures)\
[⠀⠀⠀⠀Example 6: Structures (Bad Form)](#example-6-structures-bad-form)\
[⠀⠀⠀⠀Example 7: Structures](#example-7-structures)\
[⠀⠀⠀⠀Example 8: Structures](#example-8-structures)\
[⠀⠀⠀⠀Example 9: Arrays](#example-9-arrays)\
[⠀⠀⠀⠀Example 10: Arrays](#example-10-arrays)\
[⠀⠀⠀⠀Example 11: Arrays](#example-11-arrays)\
[⠀⠀⠀⠀Example 12: Arrays](#example-12-arrays)\
[⠀⠀⠀⠀Example 13: Arrays](#example-13-arrays)\
[⠀⠀⠀⠀Example 14: Arrays](#example-14-arrays)\
[⠀⠀⠀⠀Example 15: Unions](#example-15-unions)\
[⠀⠀⠀⠀Example 16: Problems with Unions](#example-16-problems-with-unions)\
[⠀⠀⠀⠀Example 17: Ideas on Dealing with Union Troubles](#example-17-ideas-on-dealing-with-union-troubles)\
[⠀⠀⠀⠀Example 18: Unions](#example-18-unions)

# Chapter 1: A Tutorial Introduction
## Part 1: Data Types

These refer to specific ways that C stores data.  Data has a specific storage size or memory footprint that it consumes.  The type associated with data determines how it will be stored and interpreted in memory.  C Data Types are broken up into 4 types.  However, we are not going to discuss Enumerated Types in any other context than -- **avoid using them**.

### Basic Types

These are the general arithmetic types that are broken down into integer and floating point formats.

#### Integer Types

|Keyword             |Bit Width|Byte Width|Low Value||High Value|
|---|:--:|:--:|--:|:--:|:--|
|char              |8  | 1|    Single Character|||           
|signed char       |8  | 1|                 -128| to |127
|unsigned char     |8  | 1|                    0| to |255
|short             |16 | 2|                -32768| to |32767
|unsigned short    |16 | 2|                     0| to |65353
|int               |32 | 4|        -2,147,483,648| to |2,147,483,647
|unsigned int      |32 | 4|                     0| to |4,294,967,295
|long long         |64 | 8|  -9223372036854775808| to |9223372036854775807
|unsigned long long|64 | 8|                     0| to |18446744073709551615

**NOTE:** GCC on Linux typically defaults to 64-bits.  On Windows, MinGW defaults to 32-bits.  For compatibility of code between 32-bit and 64-bit, make sure your _long_ Data Types are 64-bit by using _long long_ instead.  In 32-bit environments this will make long 64-bit, and in 64-bit environments it will treat _long long_ as 64-bit _long_.

#### Floating Point Types

|Keyword         |Bit Width|Byte Width|Low Range||High Range|Precision|
|:--|:--:|:--:|--:|---|:--|--:|
|float           |32|  4 |    1.2E-38| to |3.4E+38    | 6 decimal places|
|double          |64|  8 |   2.3E-308| to |1.7E+308   |15 decimal places|
|long double     |80| 10 |  3.4E-4932| to |1.1E+4932  |19 decimal places|

#### Enumerated Types

These are typically regarded as another arithmetic type used to define named variables that are assigned discrete integer values.  They are used in place of magic numbers or hard coded values that can have arbitrary meaning.  The general modern view is to avoid using them.

**MAGIC NUMBERS** - Enumerated values were created as a solution to this problem.  However, they create more problems than they resolve.  When we consider the issue of obfuscated information by using values instead of meaninful tokens we generally refer to those as Magic Numbers.  It is generally regarded that we should not use them as initial values or in the endpoint test expressions of a while, do while, or for loop.  There is general concern for avoiding their use also in expressions, mallocs, and other statements where it may obfuscate information and taint obvious readability or understanding of the code.  You are advised to use a [#define](, or specific variable within contextual scope to give a meaningful name to your value.

```
1. They are not really integer values, but GCC does treat them as such.
2. Code written using Enums is not treated the same by all C compilers.
3. They do not provide any type safety.
4. You can assign values to Enum typed variables that are invalid in context.
5. They share common memory space, which leads to accidental variable collisions.
6. They are converted to constants that remain in your code after compiling.
7. There is no direct substitution performed by the preprocessor.
8. Enums were not part of the original K&R C dialect.
9. The storage size of an Enum is defined by the compiler.
10. You will end up littering your code with switches or other branching layouts.
11. There is no way to use non-numeric values.
12. Has a tendency to force state driven coding.
13. They violate Data Oriented Design and Don't Repeat Yourself principles.
14. Use a #define declaration instead.  We are not C++ coders.
```
[Return to Index](#index)

### Derived Types

These include Arrays, Pointers, Structures, Unions, Functions, and Type Definitions.

#### Arrays

An Array is created from a Data Type that is used to store multiple elements of the same data.  They are zero indexed and you declare them by specifying the total number of elements needed.  To access the last element in an Array use the total number of elements minus one.  Arrays, once declared, cannot change size.  Elements are accessed by unique integer based indices.  Data stored inside an Array, provided Pointers are not involved with the data stored in each element, will generally create a single block of contiguous memory.  Most off by one errors in your code will be created by trying to access information inside Arrays. You do not need to pass an Array by reference to a function as an argument in most cases when using them as they are treated under the hood as pointers or referenced as such.

#### Pointers

These are definitely regarded as one of the single hardest concepts to learn in programming, and the reason most people avoid coding in C.  A Pointer is a variable that uses the address of another variable for storage.  It uses an address that represents a specific location in memory.  You must declare pointers like any other variable declaration.  Confusingly Pointers use the asterisk for dereferencing.  This simply means, to get the value stored at the location of memory the Pointer is pointing at.  The asterisk is also used as the multiplication maths operator.  Pointers have many problems associated with their use, but they are a staple in many of the advanced C language syntax.  To pass variables to a function by reference you must use a pointer for all Data Types, except Arrays in some cases.

C has a special kind of Pointer called the Function Pointer.  This allows creating a Pointer that will point at the address of a specific Function that has been declared.  There are some rules they must follow, but can be very useful when you are writing sorting or other types of algorithms that may have a comparator or some other piece of the algorithm that could change based on requirements.  Instead of creating unique Functions for each specific task of sorting by ascending or descending order, you can pass in a Function that can be used to address this.  There are other more complicated, but useful scenarios when working with graphics engines where you may have to substitute an optional chunk of your code that runs if an equivalent feature is not available on a given platforms.

Other uses of Pointers and Function Pointers exist to form bridges tying certain portions of an Operating System, or to make a call inside a specific library accessing a foreign piece of code.

[Return to Index](#index)

#### Structures and Unions

These are your user defined record types.  Useful when you need to combine groups of items, fields, or members of different data types that can be referenced by name to create a single type.  C doesn't have classes, or support object oriented coding methods for the most part.  All members of a Structure and Union are publicly declared.  Defined Structures and Unions are not assigned memory until declared, and will always be stored in contiguous memory.  Alignment, packing, and padding are compiler implementation specific.  Let's discuss how GCC manages these aspects of these Data Types. The only real difference between a Structure and Union is how they are stored in memory.  Structure members are have unique allotments memory, where Union members all share the same memory region.

**Alignment** - This tells the compiler to attempt a specific alignment during allocation to specific boundaries. Alignment can only be used to increase member boundaries. These are determined by the linker and the platform you are compiling on.  GCC by default will optimise for the platform you are compiling on.  You can assume this is the default memory layout.

**Packing** - Specifies to the compiler that it should use the minimum footprint of memory required to represent the type.  All members of the Structure or Union will have the same equivalent packed attribute applied to them.  This will almost always affect performance negatively.  If you are memory constrained platforms, the performance tradeoff may be required to make things fit.

**Padding** - Is required, and can be manipulated by alignment and packing attributes. Overriding the default padding performed by GCC is likely to slow down access to members, but can save memory. Padding will only be inserted when a Structure member is followed by another Structure member that requires a larger alignment or at the end of the Structure to align it to a specific boundary. GCC by default is not allowed to reorder any Structure members to achieve optimal alignment, so programmers should be mindful of their member layouts inside their Structure definitions.

[Return to Index](#index)

#### Functions

This is another very hard concept for programmers to grasp -- code reuse.  Functions make this possible.  They are a block of syntax statements put together to perform a specific task.  Learning when to use Functions takes a lot of practice.  When you declare a Function you can provide a Return Type, and Argument Types that you want to pass to the Function to be used by the statements inside it.  Functions can call other Functions, and use other Data Types to declare variables.

The C Standard Library provides numerous Functions that you can call.  These often require using the correct #include statement before they can be used.  We will discuss this in detail when going over the preprocessor and the side-effects associated with including and creating headers in your code.

There is one Function that must be present in all programs called main.  This is your entry point to your program.  When you execute programs this will be where the main portion of the controlling code exists.  It is required to be present.  Your main Function should always return an int type.  It can optionally have no arguments or a pair of arguments to accept information being passed to it from the command line.

The Return Type from main is used by the Operating System to determine how the program terminated.  You are expected to return 0 if execution exit was normal, or a non-zero based value to report abnormal termination.  You will see many tutorials and examples that exclude the return value from main.  This was common many decades ago, but modern Operating Systems, especially Linux, expect the return result.  Some compilers will default to a return 0 if the statement is omitted.  For clarity in your code, you should ensure the return statement exists.

Functions can also be invoked from almost anywhere in your source code for your program.  Once a Function is created you can use it over and over.  Functions are extremely useful, practical, and required to keep moderate to large code bases tidy.

Many tutorials written for C, still declare Function main as Return Type void.  Any Function with a Return Type declared as void cannot return any value once a Function has completed executing its statements. This is not to slight the old school manuals of my youth, but they promote models of coding in C that are largely outdated. Beyond this, there are features of more modern languages that C does not support. Function Overloading, is one of them, so all Function names must be unique.

**Function Overloading** - The ability to create multiple Functions with the same name declaration and different arguments.  In modern programming, this is a major drawback that C has not added the ability to use this feature of coding.  This drives many C programmers to write C in C++.  This has a host of other drawbacks.  Despite missing this syntax feature, you can still write robust and useful programs in a meaningful way with C.  A later standard has implemented Generics into C with Macros that can emulate Function Overloading.  When discussing the preprocessor, we will cover this feature.

**Argument Lists** - Functions in order to pass information to them use arguement lists.  They consist of a Data Type and name separated by a comma. This book does not use the modern form of supplying void when there are no arguments accepted.  GCC does not warn if you make a function call with arguments to an empty argument listed function declare.  You will see comments on the Undefined Behaviour this technically causes, however, at best you're going to get a warning.  C compilers have a fuzzy area when it comes to empty argument lists. Since at best you will get is a warning, this book excludes the promotion of using void argument lists.  The only other alternative is to use Function Prototypes.

**Function Prototypes** - Generally these create code clutter, but they can be meaningful in context and are required when delcaring Function Pointers in a modified syntax. The book will detail when using Function Prototypes is generally a good idea.  Since all C Compilers are known as single pass for the most part, things must be declared before use. If a Function is delcared elsewhere, externally, or compiled/linked from another foreign piece of code, you must use a Function Prototype to announce that the compiler should be aware to look for it. Otherwise, you are encouraged to reorder your main Function to the end of your code and ordering all other functions in precalling fashion.  This is another heavily debated topic amongst purists.  As mentioned this book focuses on keeping code clean, easy to read, hardware friendly and mostly modern. Some old school syntax is still encouraged regardless of side-effects.

**NOTE** - No process is going to save you from mistakes you're going to make in your code based on standards, compiler warnings, or style guides.  Based on the discussions around Functions, you are encouraged to understand that C can be an over forgiving language and pretty much take whatever you throw at it. Understanding what the code is doing in C is far more important than anything you can do to generate useless warnings for mistakes you should be aware of in your code. 

[Return to Index](#index)

#### Type Definitions

To implement a Type Definition you must use the typedef keyword.  This allows you to give meaningful names to things, and stop having to type the typical longer syntax required by C.   It also allows forward declarations of things.  Many libraries have custom Type Definitions to keep track of what specific parts of the library belongs to what.  OpenGL comes to mind, or even just having the desire to shorten unsigned long long int to u64.  This has excellent utility when used meaningfully.  Many C purists discourage using Type Definitions, but you cannot overlook the modern desire to keep your code clean, readable, and maintainable.

There are many good discussions between Linus Torvalds and the rest of the internet on [his views](https://yarchive.net/comp/linux/typedefs.html) on programmers that abuse the typedef keyword.  It can certainly be agreed that this is a completely abusable feature of C.  But like the goto keyword, there are some places where it is useful.  You will unfortunately be urged to ignore a feature of the language by many programmers and tutorials because most never learn when to use it in proper context. 

Most projects and coding firms you will write code for have Style Guides.  Each guide will usually include a section on Type Definitions.  Along with other restrictions on how code should be written for the given project.  In general, if it makes things easier for you to write code, is generally self-documenting, helps with maintenance of the code base, then use it regardless of the opinions of other coders, unless the project you are working on has a strict Style Guide.  In which case, you must follow it, regardless of preferred personal coding styles.

**NOTE** - You will see typedefs being used in pretty much every example in this book.  Instead of using <stdint.h>, which normally provides typedefs for specific bitwidth data types, this book uses shorter forms of the int32_t for an unsigned int.  Instead prefixing all unsigned types with a _u_, and signed types with an _s_.  In this case _s64_ would be a type guaranteed to be at least 64 bits and signed.  The only base data type in C that you will see unmodified with a typedef is char.  It has no equivalent associated signed or unsigned state.  The _u8_, and _s8_ typedefs specifiy an unsigned char, and signed char of 8 bits wide.  Floating point types will be prefixed with an _f_.  In the case of structs, unions, and other specific users types they will be prefixed with a _T_.

[Return to Index](#index)

#### Void

Despite this being a Data Type which can be used in various scenarios, there are some restrictions on void that should be discussed.  When dealing with void, it generally means different things contextually. There are also problems with void conversions and data loss. Opportunities to create Undefined Behaviour are also in abundance. 

Unlike other Data Types you cannot directly declare a variable as void unless it is a pointer.  Void when used as a Function Return Data Type, signifies that a Function is incapable of returning any information from it.  Void pointer Data Types on the other hand can be extremely flexible.  They can store any other Data Type, have mixed data, memory layouts, and can also be used to point to Functions.  Many Functions inside the C Standard Library will return a void pointer, or consume one as a Function Argument - malloc() and free() are good examples of this.

When declaring Function Arguments in a Function Prototype you should technically use void if the Function Argument List is actually meant to be nothing.  GCC for backwards compatibility maintains arbitrary Function Prototypes and definitions of functions which can lead to problems if you program using the Function Prototypes.  As mentioned in the Functions sections for Arguments Lists, this book does not use void in this way. 

[Return to Index](#index)

### Basic Code Examples

#### Example 1: Variable Declarations
Basic program that has no output.

1. declaring basic variables and assigning default values
2. setup of function main 

```C
int main() {                                   // Main program entry.
  char foo = 1;                                // Variable type char named foo and assigns it a value of 1.
  char bar = -10;                              // Variable type char named bar and assigns it a value of -10.
  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 2: Type Definitions
Basic program that has no output.

1. using a typedef to declare a custom Type Name
2. declaring basic variables and assigning default values
3. setup of function main 

```C
typedef unsigned char u8;                      // Associate type unsigned char with u8.
typedef int           s32;                     // Associate type signed int with s32.

s32 main() {                                   // Main program entry.
  u8 foo = 0;                                  // Variable type u8 named foo and assigns it a value of 0.
  u8 bar = 212;                                // Variable type u8 named bar and assigns it a value of 212.
  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 3: Structures
Basic program that has no output.

1. using a typedef to declare a custom Type Name
2. definition of a struct with 2 members using the custom Type Name
3. assigning default values to Structure Members
4. setup of function main 

```C
typedef unsigned char u8;                      // Associate type unsigned char with u8.
typedef int           s32;                     // Associate type signed int with s32.

typedef struct {                               // Declare typedef for struct.
  u8 foo;                                      // Declare struct member of type u8 named foo.
  u8 bar;                                      // Declare struct member of type u8 named bar.
} TFoobar;                                     // Assign name of TFoobar to struct declare.

s32 main() {                                   // Main program entry.
  TFoobar record = {                           // Declare type TFoobar named record.
    .foo = 16,                                 // Assign a default value of 16 to member foo.
    .bar = 255                                 // Assign a default value of 255 to member bar.
  };

  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 4: Structures (Bad Form)
Alternate basic program that has no output.

1. using a typedef to declare a custom Type Name
2. definition of a struct with 2 members using the custom Type Name
3. assigning default values to Structure Members
4. setup of function main 

```C
typedef unsigned char u8;                      // Associate type unsigned char with u8.
typedef int           s32;                     // Associate type signed int with s32.

typedef struct {                               // Declare typedef for struct.
  u8 foo;                                      // Declare struct member of type u8 named foo.
  u8 bar;                                      // Declare struct member of type u8 named bar.
} TFoobar;                                     // Assign name of TFoobar to struct declare.

s32 main() {                                   // Main program entry.
  TFoobar record = {2, 1};                     // Declare type TFoobar named record.
                                               // Assigns the values in order of member layout.
                                               // This would assign 2 to foo and 1 to bar
                                               // despite this method being shorter, it does not
                                               // produce self-documenting code and is discouraged.

  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 5: Structures
Alternate basic program that has no output.

1. using a typedef to declare a custom Type Name
2. definition of a struct with 2 members using the custom Type Name
3. assigning default values to Structure Members
4. setup of function main 

```C
typedef unsigned char u8;                      // Associate type unsigned char with u8.
typedef int           s32;                     // Associate type signed int with s32.

typedef struct {                               // Declare typedef for struct.
  u8 foo;                                      // Declare struct member of type u8 named foo.
  u8 bar;                                      // Declare struct member of type u8 named bar.
} TFoobar;                                     // Assign name of TFoobar to struct declare.

s32 main() {                                   // Main program entry.
  TFoobar record = {};                         // Declare type TFoobar named record.
                                               // Assigns a default value of 0 to both foo and bar.

  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 6: Structures (Bad Form)
Alternate basic program that has no output.

1. using a typedef to declare a custom Type Name
2. definition of a struct with 2 members using the custom Type Name
3. assigning default values to Structure Members
4. setup of function main 

```C
typedef unsigned char u8;                      // Associate type unsigned char with u8.
typedef int           s32;                     // Associate type signed int with s32.

typedef struct {                               // Declare typedef for struct.
  u8 foo;                                      // Declare struct member of type u8 named foo.
  u8 bar;                                      // Declare struct member of type u8 named bar.
} TFoobar;                                     // Assign name of TFoobar to struct declare.

s32 main() {                                   // Main program entry.
  TFoobar record = {4};                        // Declare type TFoobar named record.
                                               // Assigns a default value of 4 to foo
                                               // and then sets bar to a value 0 by default.
                                               // Despite this method being shorter, it does not
                                               // produce self-documenting code and is discouraged.

  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 7: Structures
Alternate basic program that has no output.

1. using a typedef to declare a custom Type Name
2. definition of a struct with 2 members using the custom Type Name
3. assigning default values to Structure Members
4. setup of function main 

```C
typedef unsigned char u8;                      // Associate type unsigned char with u8.
typedef int           s32;                     // Associate type signed int with s32.

typedef struct {                               // Declare typedef for struct.
  u8 foo;                                      // Declare struct member of type u8 named foo.
  u8 bar;                                      // Declare struct member of type u8 named bar.
} TFoobar;                                     // Assign name of TFoobar to struct declare.

s32 main() {                                   // Main program entry.
  TFoobar record = {                           // Seclare type TFoobar named record.
    .foo = 12                                  // Assigns a default value of 12 to foo
  };                                           // and then sets bar to a value of 0 by default.
                               
  return 0;                                    // Return status successful
}
```

[Return to Index](#index)

#### Example 8: Structures
Alternate basic program that has no output.

1. using a typedef to declare a custom Type Name
2. definition of a struct with 2 members using the custom Type Name
3. assigning default values to Structure Members
4. setup of function main

```C
typedef unsigned char u8;                      // Associate type unsigned char with u8.
typedef int           s32;                     // Associate type signed int with s32.


typedef struct {                               // Declare typedef for struct.
  u8 foo;                                      // Declare struct member of type u8 named foo.
  u8 bar;                                      // Declare struct member of type u8 named bar.
} TFoobar;                                     // Assign name of TFoobar to struct declare.

s32 main() {                                   // Main program entry.
  TFoobar record = {                           // Declare type TFoobar named record.
    .bar = 34                                  // Assigns a default value of 34 to bar
  };                                           // and then sets foo to a value of 0 by default.

  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 9: Arrays
Basic program that has no output.

1. using a typedef to declare a custom Type Name
2. definition of an arbitrary array with defaults values
3. setup of function main

```C
typedef int          s32;                      // Associate type signed int with s32
typedef unsigned int u32;                      // Associate type unsigned int with u32

s32 main() {                                   // Main program entry
  u32 foo[] = {0, 1, 2, 3, 4, 5, 6};           // Declare type u32 named foo
                                               // The square brackets [] are used
                                               // to denote an array in C.
                                               // In this case we are not defining
                                               // the array with a starting size but
                                               // we are assigning default data to it.
                                               // When using GCC, this is a method for
                                               // automatic initialisation of the array.
                                               // It will calculate the size required for you.
  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 10: Arrays
Alternate basic program that has no output.

1. using a typedef to declare a custom Type Name
2. definition of an arbitrary array with defaults values
3. setup of function main

```
typedef int          s32;                       // Associate type signed int with s32.
typedef unsigned int u32;                       // Associate type unsigned int with u32.

s32 main() {                                    // Main program entry.
  u32 foo[7] = {};                              // Declare type u32 named data.
                                                // In this case we are declaring 7 elements.
                                                // C is a 0 index based language
                                                // this will have a range of 0 to 6.
                                                // We are assigning default data to it.
                                                // With GCC this is a method of
                                                // automatic initialisation to 0 of all
                                                // elements in the array.
  return 0;                                     // Return status successful      
}
```

[Return to Index](#index)

#### Example 11: Arrays
Basic program that has no output.

1. using a typedef to declare a custom Type Name
2. how to typedef forward associations for a struct that contains members of itself
3. definition of a struct with 3 members
4. definition of a fixed declaration of an array of structs with default values
5. setup of function main

```C
typedef int          s32;                       // Associate type signed int with s32.
typedef unsigned int u32;                       // Associate type unsigned int with u32.

typedef struct _TFoobar TFoobar;                // Associate struct _TFoobar with TFoobar.
                                                // We need this forward typedef because
                                                // the struct has a member data type
                                                // of itself.

struct _TFoobar {                               // You cannot use the standard typedef
  u32 foo;                                      // method of declaration when your struct
  u32 bar;                                      // contains a member of itself.
  TFoobar *foobar;                              // Members that are struct data types
};                                              // must be declared as pointers.

s32 main() {                                    // Main program entry.
  TFoobar data[15] = {};                        // Arrays of structs can be default initialised
                                                // in this case we have declared 15 elements.
                                                // This will have a range of 0 to 14.
                                                // All fields will be set to a value of 0.
  return 0;                                     // Return status successful.
}
```

[Return to Index](#index)

#### Example 12: Arrays
Basic program that has no output.

1. using a typedef to declare a custom Type Name
2. how to typedef forward associations for a struct that contains members of itself
3. definition of a struct with 3 members
4. definition of a fixed declaration of an array of structs with specified values
5. setup of function main

```C
typedef int          s32;                       // Associate type signed int with s32.
typedef unsigned int u32;                       // Associate type unsigned int with u32.

typedef struct _TFoobar TFoobar;                // Associate struct _TFoobar with TFoobar
                                                // we need this forward typedef because the
                                                // struct has a member data type of itself.                                                

struct _TFoobar {                               // You cannot use the standard typedef
  u32 foo;                                      // method of declaration when your struct
  u32 bar;                                      // contains a member of itself.
  TFoobar *foobar;                              // Members that are struct data types
};                                              // must be declared as pointers.

s32 main() {                                    // Main program entry.
  TFoobar data[15] = {                          // Arrays of structs can be default initialised.
    { .foo = 12, .bar = 8 },                    // Each element must be contained in a secondary
    {},                                         // block of {} and then it can follow the
    { .foo = 1 }                                // rules defined earlier in examples for initialisation.
  };                                            // Commas are used to seperate a list of
                                                // consecutive initialisations.
                                                // Even though this has 15 elements the reamaining
                                                // elements will be default initialised to 0.
                                                // This is mererly one method for initialisation
                                                // during declare.

  data[12] = (TFoobar){                         // Accesses element 13 [12+1 from 0 index].
    .foo = 5, .bar = 6                          // We need to perform a cast (TFoobar) then
  };                                            // it's possible to use the standard struct
                                                // field initialisation.
  return 0;                                     // Return status successful.
}
```

[Return to Index](#index)

#### Example 13: Arrays
Alternate basic program that has no output.

1. using a typedef to declare a custom Type Name
2. how to typedef forward associations for a struct that contains members of itself
3. definition of a struct with 3 members
4. definition of a fixed declaration of an array of structs
5. initialisation of specific elements after initial declaration of an array
6. setup of function main

```C
typedef int          s32;                       // Associate type signed int with s32.
typedef unsigned int u32;                       // Associate type unsigned int with u32.

typedef struct _TFoobar TFoobar;                // Associate struct _TFoobar with TFoobar.
                                                // We need this forward typedef because
                                                // the struct has a member data type
                                                // of itself.

struct _TFoobar {                               // You cannot use the standard typedef.
  u32 foo;                                      // Method of declaration when your struct
  u32 bar;                                      // contains a member of itself.
  TFoobar *foobar;                              // Members that are struct data types
};                                              // must be declared as pointers.

s32 main() {                                    // Main program entry.
  TFoobar data[15] = {                          // Arrays of structs can be default initialised
    [0].foo = 12, [0].bar = 8,                  // each element and member can be referenced
    [2].bar = 3,                                // by element index in this manner also, then
    [12].foo = 5, [12].bar = 5                  // follow rules defined earlier in examples
  };                                            // for member initialisation.
                                                // Commas are used to seperate a list of
                                                // consecutive initialisations even though
                                                // this has 15 elements they will be default
                                                // initialised to 0.
                                                // This is another method for initialisation
                                                // during declare.
  return 0;                                     // Return status successful.
}
```

[Return to Index](#index)

#### Example 14: Arrays
Basic program that has no output.

1. using a typedef to declare a custom Type Name
2. definition of an arbitrary array of u32
3. initialisation of specific elements in an array using ranges
4. setup of function main

```C
typedef int          s32;                       // Associate type signed int with s32.
typedef unsigned int u32;                       // Associate type unsigned int with u32.

s32 main() {                                    // Main program entry.
  u32 data[] = {                                // Arrays can be default initialised using
    [ 0 ... 10] = 1,                            // ranges for specific values in this manner.
    [11 ... 20] = 3,                            // This will define an arbitrary array with
    [21 ... 99] = 5,                            // 101 elements ranging from 0 to 100.
    [100]       = 0                             // It also works for fixed element declares of
  };                                            // arrays provided indexes fall within range
                                                // of elements defined by the fixed value.
  return 0;                                     // Return status successful.
}
```

[Return to Index](#index)

#### Example 15: Unions
Basic program that has no output.

1. using multiple typedefs to declare custom Type Names
2. creation of a union and its declaration
3. setup of function main.  

```C
typedef unsigned char      u8;                  // associate type unsigned char with u8
typedef unsigned short     u16;                 // associate type unsigned short with u16
typedef int                s32;                 // associate type signed int with s32
typedef unsigned int       u32;                 // associate type unsigned int with u32
typedef unsigned long long u64;                 // associate type unsigned long long with u64

typedef union {                                 // declare typedef for union
  u8  chars [8];                                // takes 8x 1 byte to make a u64
  u16 shorts[4];                                // takes 4x 2 bytes to make a u64 
  u32 ints  [2];                                // takes 2x 4 bytes to make a u64
  u64 base;                                     // largest type inside the union at 8 bytes
} TMagiCaster;                                  // assign TMagiCaster as the union name

s32 main() {                                    // main program entry
  TMagiCaster foo = {};                         // unions can be initialised to 0
                                                // the same as structs
                                                // any assignment to any of the members
                                                // will cause the automatic update of all
                                                // other members inside the union
                                                // this is because each member of the union
                                                // shares the same memory address as every
                                                // other member in the union
                                                // you gain auto-casting or assignments
                                                // between types for free
  return 0;                                     // return status successful
}
```

[Return to Index](#index)

#### Example 16: Problems with Unions
NOTE: PROBLEMS WITH UNIONS -- Basic program that has no output, but shows using multiple typedef to declare custom Type Names, how to create a union, data loss/confusing union behaviour, and setup of function main.  

```C
typedef unsigned char      u8;                  // Associate type unsigned char with u8.
typedef unsigned short     u16;                 // Associate type unsigned short with u16.
typedef int                s32;                 // Associate type signed int with s32.
typedef unsigned int       u32;                 // Associate type unsigned int with u32.
typedef unsigned long long u64;                 // Associate type unsigned long long with u64.
typedef float              f32;                 // Associate type float with f32.
typedef double             f64;                 // Associate type double with f64.
typedef double long        f80;                 // Associate type double long with f80.

typedef union {                                 // Declare typedef for union.
  char *pchars;                                 // When you cross types in this case
  u8  chars  [8];                               // mixing pointers, and floating point
  u16 shorts [4];                               // numbers with integers you will cause
  u32 ints   [2];                               // data loss, conversion cast problems
  u64 intBase;                                  // as these types are fundamentally
  f32 floats [2];                               // incompatible on a memory storage level.
  f64 doubles[2];                               // Floating points and pointers traditionally
  f80 floatBase;                                // are not used in unions because of this.
} TMagiCaster;                                  // Assign TMagiCaster as the union name.

// There are special cases where you may want to mix some types
// but generally follow that pointers in unions will reference
// the address, and not the data at the pointer.
// Floating points will cause some form of awry behaviour when
// converting between them.
// This is not a good use of a union.

s32 main() {
  return 0;
}
```

[Return to Index](#index)

#### Example 17: Ideas on Dealing with Union Troubles
NOTE: IDEAS ON DEALING WITH UNION TROUBLES - Basic program that has no output, but shows using multiple typedef to declare custom Type Names, how to create a struct with an anonymous union inside it, and setup of function main. 

```C
typedef unsigned char      u8;   //associate type unsigned char with u8
typedef unsigned short     u16;  //associate type unsigned short with u16
typedef int                s32;  //associate type signed int with s32
typedef unsigned int       u32;  //associate type unsigned int with u32
typedef unsigned long long u64;  //associate type unsigned long long with u64
typedef float              f32;  //associate type float with f32
typedef double             f64;  //associate type double with f64
typedef long double        f80;  //associate type double long with f80

typedef struct {                 //declare typedef for struct  
  union {                        //in this case we are declaring an
    u8  chars  [8];              //anonymous union to deal with our
    u16 shorts [4];              //compatible integer types and embedding
    u32 ints   [2];              //it inside our struct
    u64 intBase;                 //these members will still share the same
  };                             //memory region
  char *pchars;                  //where these members outside the union
  f32 floats [2];                //will have their own regions of memory
  f64 doubles[2];                //as regular members of a struct
  f80 floatBase;             
} TMagiCaster;               

s32 main() {
  TMagiCaster foo = {};
  //you can access the members from the anonymous union as if they
  //were base members of the struct

  //foo.chars
  //foo.shorts
  //foo.floatbase

  //if we named the union inside the struct, you would need to
  //specify the union name as in foo.unionName.chars to access those
  //members inside the union
  
  return 0;
}
```

[Return to Index](#index)

#### Example 18: Unions
Basic program that has no output, but shows using a union, a series of anonymous struct layouts for common associations of data, and setup of function main. 

```C
typedef int s32;          //associate type signed int with s32
typedef float f32;        //associate type float with f32

typedef union {           //declare typedef for struct  
  struct {                //each of these anonymous structures
    f32 x;                //inside the union will be treated as
    f32 y;                //two seperate groups of members
  };                      //because each anonymous struct is part
  struct {                //of the union all the structs will share
    f32 u;                //the same memory region
    f32 v;                //set 1:
  };                      //  foo.x
  struct {                //  foo.u
    f32 left;             //  foo.left
    f32 right;            //  foo.width
  };                      //set 2:
  struct {                //  foo.y
    f32 width;            //  foo.v
    f32 height;           //  foo.right
  };                      //  foo.height
  f32 members[2];         //this array will place set 1 at index 0
} T2DVectorF32;           //and set 2 at index 1

s32 main() {              //main program entry
  T2DVectorF32 foo = {};  //default initialise all members to 0
  
  foo.x = 0.6f;           //assigns a value of 0.6f to set 1
  foo.right = 8.5f;       //assigns a value of 8.5f to set 2
  
  return 0;               //return status successful
}
```

It might seem strange to cover the complexities of struct, union, typedef and other things before the basics of general variable use and output, but since each of those things is likely to use the prior outlined references, it seemed prudent to cover those first.  This gives general exposure, so when used in the next pieces they are not new concepts.  We are going to bypass Functions, Pointers, and other types not discussed until post Console Output.

[Return to Index](#index)

# Part 2: Console Output & Using #include

Console, or Terminal based output has been around since the advent of computer screens.  It is the most common way programmers can present information from within the program.  C has Functions built into the Standard Library that can be accessed from various includible libraries.  This is where the #include tag is useful.  For this context we will be referencing the library stdio.h. 

> #include <stdio.h>
 
The Standard I/O library gives us access to several useful predefined Functions.

> puts 

This allows us to write a string of char to the Console and appends a newline character to the output automatically.  The function prototype for puts...  

> int puts(const char *str)

In this case it returns an int value, and accepts a Pointer Type of char named str.  As usual with functions that will accept char strings, they need to be NULL terminated.  In other words, make sure your char string, buffer, or other form of data has a '\0' literal on the end of it.  We will cover char strings more later.

The int return from puts will be the total number of characters written to the Console including the '\n' it appends to the end.  If there is an error, the return will be set to the constant EOF and it will set an error number you can lookup.  If you missed putting the '\0' at the end, you will cause Undefined Behaviour. (edited)
Avatar
PDrifting 23-Apr-21 04:42 PM
putchar
Sometimes you just need to output a single char to the Console.  This is what putchar is for.  The function prototype for putchar... 
int putchar(int character)
It might seem odd that putchar accepts an int instead of char, but these are compatible Data Types that can be thought of like a union.  Any int can be a char and any char can be an int.  We'll go over char literals and int more later.  This makes putchar extremely flexible.  You can refer to a specific character by an int value, or by a char literal.

The int return from putchar returns the char output to the Console.  If there is an error, the return will be set to the constant EOF and it will set an error number you can lookup. (edited)
Avatar
PDrifting 23-Apr-21 05:11 PM
printf
Avatar
PDrifting 23-Apr-21 05:36 PM
The beast of Console output.  For formatted output printf is your friend.  Remembering how to use it will make it your enemy.  If you scour the internet for printf cheat sheets, you'll find them in abundance. This is by far one of the most complex feature out the C Standard Library.  Let's start with the prototype... 
int printf(const char *format, ...)
There is a complex concept shown in this prototype -- the ellipsis [...]. All you need to remember is the ellipsis means, can take an arbitrary list of comma separated arguments.  The char format string on the other hand is going to require some deeper discussion.

The format string argument in printf can be a straight char string, but with Format Specifiers peppered throughout it.  Let's dissect the associated Data Types and their Format Specifiers. (edited)
Avatar
PDrifting 23-Apr-21 06:01 PM
                    Format Specifier & Special Characters Table

Integer             Value   Char       Pointer            Address
------------------------------------   ------------------------------------   
char [1]            %hhu    %c         any pointer type   %p
signed char         %hhi    %c
unsigned char       %hhu    %c         
short               %hi     %c                            Output Specifier 
unsigned short      %hu     %c         Convert To [2]     Lwr  Upr  64-Bit
int                 %i      %c         ------------------------------------
unsigned int        %u      %c         hex                %x   %X   %Lx %LX
long long           %Ld                octal              %o
unsigned long long  %Lu
                                       Special Characters 
                            Exponent   ------------------------------------
Floating Point      Value   Lwr  Upr   \n                 New Line
------------------------------------   \f                 Form Feed
float               %f      %e   %E    \r                 Carriage Return
double              %lf     %le  %lE   \t                 Tab
long double         %Lf     %Le  %LE   \b                 Backspace
                                       \\                 Use \ inside string
Strings             Display            \"                 Use " inside string
------------------------------------   %%                 Use % inside string
char *              %s                 \'                 Single Quote
                                       \0                 Null Character

NOTE [1]: Type char is unique from all other types in that it has three unique states, char, signed char, and unsigned char.  None of these equate to each other.  According to the C Standard char will be guaranteed to hold a single character/byte worth of data.  Function arguments that expect char will complain if you try to pass a signed or unsigned variant instead.

NOTE [2]: If the hex specifier is used for any unsigned integer Data Type it will be cast to unsigned char and only display one 8-bit.  The hex and octal specifiers can only be used to represent integer Data Types.  Floating Point Data Types require special pointer twiddling.  You will get strange output trying to use either of the conversion specifiers otherwise.

Alright, now we have a table of nightmares and the basic knowledge to start tackling some basic output.  Let's write some examples.  The following examples will expand on topics missed above and cover a more complete set of examples based on all topics we have covered so far.  Get ready, there's going to be a lot. 

NOTE: Comments and such might be sparse as we carry on with these examples due to the limitations of discord messages to 2000 characters.  This will be resolved later when the book is out of draft format.  Attempts to provide comments will persist where possible. (edited)
Avatar
PDrifting 28-Apr-21 09:59 PM
Part 3: C Output & Expansion on Type Examples (edited)
Basic program with output, using a portion of the C Standard Library to access Functions for output, and setup of function main. 
#include <stdio.h>         //provide access to i/o functions 

typedef int s32;

s32 main() {               //main program entry
  puts("Hello World!");    //displays Hello World! to the console
  return 0;                //return status successful
}
(edited)
Avatar
PDrifting 29-Apr-21 12:26 AM
Basic program with output, using a portion of the C Standard Library to access Functions for output, showing various typedef assignments, general variable use, and setup of function main. (edited)
Avatar
PDrifting 29-Apr-21 03:17 PM
#include <stdio.h>

//create typedef associations
typedef char s8;
typedef short s16;
typedef int s32;
typedef long long s64;

typedef unsigned char u8;
typedef unsigned short u16;
typedef unsigned int u32;
typedef unsigned long long u64;

typedef float f32;
typedef double f64;
typedef long double f80;

s32 main() {
  //variable declarations follow
  //type name = initial value;  
  s8  sFoo  = -120;
  u8  uFoo  = 'A';
  s16 sBar  = -27543;  
  u16 uBar  = 98;
  s32 sBaz  = -1676352;
  u32 uBaz  = 'C';
  s64 sThud = -38131823283338;
  u64 uThud = 14710131619;
  f32 flob  = 0.125;
  f64 corge = 3.141592653589793;
  f80 plugh = 9.6169031625e+35;

  //shows using the appropriate format specifier for a given type
  //C has a special use case for %c so that integer based 8-bit,
  //16-bit, and 32-bit data types can all be used to represent
  //chars as can be seen from the output information below
  //64-bit integer types are incapable of storing char information

  printf("sFoo  [%%c]   = %c\n", sFoo);
  printf("uFoo  [%%c]   = %c\n", uFoo);
  printf("sFoo  [%%d]   = %d\n", sFoo);
  printf("uFoo  [%%d]   = %d\n", uFoo);
  printf("sBar  [%%c]   = %c\n", sBar);  
  printf("uBar  [%%c]   = %c\n", uBar);
  printf("sBar  [%%hi]  = %hi\n", sBar);  
  printf("uBar  [%%hu]  = %hu\n", uBar);
  printf("sBaz  [%%c]   = %c\n", sBaz);
  printf("uBaz  [%%c]   = %c\n", uBaz);
  printf("sBaz  [%%i]   = %i\n", sBaz);
  printf("uBaz  [%%u]   = %u\n", uBaz);  
  printf("sThud [%%lld] = %lld\n", sThud);  
  printf("uThud [%%llu] = %llu\n", uThud);
  printf("flob  [%%f]   = %f\n", flob);
  printf("flob  [%%e]   = %e\n", flob);
  printf("flob  [%%E]   = %E\n", flob);
  printf("corge [%%lf]  = %lf\n", corge);
  printf("corge [%%le]  = %le\n", corge);
  printf("corge [%%lE]  = %lE\n", corge);
  printf("plugh [%%Lf]  = %Lf\n", plugh);
  printf("plugh [%%Le]  = %Le\n", plugh);
  printf("plugh [%%LE]  = %LE\n", plugh);

  return 0;
}
(edited)
Avatar
PDrifting 29-Apr-21 03:26 PM
Generated output:
sFoo  [%c]   = �
uFoo  [%c]   = A
sFoo  [%d]   = -120
uFoo  [%d]   = 65
sBar  [%c]   = i
uBar  [%c]   = b
sBar  [%hi]  = -27543
uBar  [%hu]  = 98
sBaz  [%c]   = �
uBaz  [%c]   = C
sBaz  [%i]   = -1676352
uBaz  [%u]   = 67
sThud [%lld] = -38131823283338
uThud [%llu] = 14710131619
flob  [%f]   = 0.125000
flob  [%e]   = 1.250000e-01
flob  [%E]   = 1.250000E-01
corge [%lf]  = 3.141593
corge [%le]  = 3.141593e+00
corge [%lE]  = 3.141593E+00
plugh [%Lf]  = 961690316249999956021666669771358208.000000
plugh [%Le]  = 9.616903e+35
plugh [%LE]  = 9.616903E+35
(edited)
Avatar
PDrifting 29-Apr-21 06:00 PM
Based on the above we can see some janky output showing up with at least two of the %c specifiers for sFoo and sBaz.  There are problems sometimes, as you can see with non-displayable information.  Here's a little basic program with output, showing how to use the %x [hex specifier], some examples on how it can be used, and setup of Function main. (edited)
Avatar
PDrifting 30-Apr-21 12:00 AM
#include <stdio.h>

//create typedef associations
typedef char s8;
typedef short s16;
typedef int s32;
typedef long long s64;

typedef unsigned char u8;
typedef unsigned short u16;
typedef unsigned int u32;
typedef unsigned long long u64;

s32 main() {
  //variable declarations follow
  //type name = initial value;  
  s8  sFoo  = -120;
  u8  uFoo  = 'A';
  s16 sBar  = -27543;
  u16 uBar  = 98;
  s32 sBaz  = -1676352;
  u32 uBaz  = 'C';
  s64 sThud = -38131823283338;
  u64 uThud = 14710131619;

  //keep in mind the hex specifier only works with integer data types
  //out of the box and only showing the lower case specifier in this case
  //you can use %X and %LX if you prefer upper case
  //remember you need the %Lx or %LX for 64-bit
  //also that all other unsigned integer data tyoes will be cast
  //to unsigned char as you'll see in the output

  printf("sFoo  [%%x] = %x\n", sFoo);
  printf("uFoo  [%%x] = %x\n", uFoo);
  printf("sBar  [%%x] = %x\n", sBar);  
  printf("uBar  [%%x] = %x\n", uBar);
  printf("sBaz  [%%x] = %x\n", sBaz);
  printf("uBaz  [%%x] = %x\n", uBaz);
  printf("sThud [%%Lx] = %Lx\n", sThud);  
  printf("uThud [%%Lx] = %Lx\n", uThud);

  return 0;
}
(edited)
Avatar
PDrifting 01-May-21 11:47 AM
Generated Output:
sFoo  [%x] = ffffff88
uFoo  [%x] = 41                    //cast to a single unsigned char byte
sBar  [%x] = ffff9469
uBar  [%x] = 62                    //cast to a single unsigned char byte
sBaz  [%x] = ffe66bc0
uBaz  [%x] = 43                    //cast to a single unsigned char byte
sThud [%Lx] = ffffdd51be37f376
uThud [%Lx] = 36ccacba3
(edited)
Avatar
PDrifting 01-May-21 01:41 PM
Now that we have a general handle on the basics of printf there is another part we need to discuss that deals with modifiers that can be applied to format specifiers.  These modifiers control justification, number of decimal places to show, and control padding with characters of the output.  We'll need to create another table for some of the rules.  Then we'll go over some examples. (edited)
Avatar
PDrifting 01-May-21 11:19 PM
Modified Format Specifier

%[A][B][C][D]

[A] Use - to format for left justification.
[B] Specify a padding character here.
[C] Use ?.? where ? is an integer value.
    First position is the total width of output.
    Second position after the . is how many decimal positions.
[D] Use your normal format specifier here.

[A][B][C] are optional.
(edited)
Confused? Probably... so let's throw some more examples into the mix.  It's always easier to look at code to figure out how things work.  We'll need to break down every specifier with enough context to fully explore the last remaining pieces of printf. (edited)
Avatar
PDrifting 08-May-21 11:16 AM
Here's a little basic program with output, showing the basics of left justification.  
#include <stdio.h>

typedef char s8;
typedef unsigned char u8;
typedef int s32;

s32 main() {
  s8 sFoo  = -120;
  s8 sBar  = 7;
  s8 sBaz  = 115;
  s8 sThud = 'A';

  u8 uFoo  = 0;
  u8 uBar  = 17;
  u8 uBaz  = 247;
  u8 uThud = 'A';
  
  //left justify 
  printf("sFoo  [%%-d] %-d\n", sFoo);
  printf("sBar  [%%-d] %-d\n", sBar);
  printf("sBaz  [%%-d] %-d\n", sBaz);
  printf("sThud [%%-d] %-d\n\n", sThud);

  printf("uFoo  [%%-d] %-d\n", uFoo);
  printf("uBar  [%%-d] %-d\n", uBar);
  printf("uBaz  [%%-d] %-d\n", uBaz);
  printf("uThud [%%-d] %-d\n\n", uThud);

  printf("sFoo  [%%-c] %-c\n", sFoo);
  printf("sBar  [%%-c] %-c\n", sBar);
  printf("sBaz  [%%-c] %-c\n", sBaz);
  printf("sThud [%%-c] %-c\n\n", sThud);

  printf("uFoo  [%%-c] %-c\n", uFoo);
  printf("uBar  [%%-c] %-c\n", uBar);
  printf("uBaz  [%%-c] %-c\n", uBaz);
  printf("uThud [%%-c] %-c\n\n", uThud);

  return 0;
}
(edited)
Generated Output:
sFoo  [%-d] -120
sBar  [%-d] 7
sBaz  [%-d] 115
sThud [%-d] 65

uFoo  [%-d] 0
uBar  [%-d] 17
uBaz  [%-d] 247
uThud [%-d] 65

sFoo  [%-c] �
sBar  [%-c] 
sBaz  [%-c] s
sThud [%-c] A

uFoo  [%-c] 
uBar  [%-c] 
uBaz  [%-c] �
uThud [%-c] A
(edited)
Avatar
PDrifting 08-May-21 11:24 AM
Another little program with output showing how to use zero and width padding.  Keep in mind you cannot using zero padding or any other character padding with %c.  Only width padding is valid with this Format Specifier.  
#include <stdio.h>

typedef char s8;
typedef unsigned char u8;
typedef int s32;

s32 main() {
  s8 sFoo  = -120;
  s8 sBar  = 7;
  s8 sBaz  = 115;
  s8 sThud = 'A';

  u8 uFoo  = 0;
  u8 uBar  = 17;
  u8 uBaz  = 247;
  u8 uThud = 'A';
  
  //shows padding a value with leading zeroes
  //with use of width padding 
  printf("sFoo  [%%05d] %05d\n", sFoo);
  printf("sBar  [%%05d] %05d\n", sBar);
  printf("sBaz  [%%05d] %05d\n", sBaz);
  printf("sThud [%%05d] %05d\n\n", sThud);

  printf("uFoo  [%%05d] %05d\n", uFoo);
  printf("uBar  [%%05d] %05d\n", uBar);
  printf("uBaz  [%%05d] %05d\n", uBaz);
  printf("uThud [%%05d] %05d\n\n", uThud);

  //padding cannot be applied to %c
  //only width padding is valid
  printf("sFoo  [%%5c] %5c\n", sFoo);
  printf("sBar  [%%5c] %5c\n", sBar);
  printf("sBaz  [%%5c] %5c\n", sBaz);
  printf("sThud [%%5c] %5c\n\n", sThud);

  printf("uFoo  [%%5c] %5c\n", uFoo);
  printf("uBar  [%%5c] %5c\n", uBar);
  printf("uBaz  [%%5c] %5c\n", uBaz);
  printf("uThud [%%5c] %5c\n\n", uThud);

  return 0;
}
(edited)
Avatar
PDrifting 08-May-21 09:54 PM
Generated Output:
sFoo  [%05d] -0120
sBar  [%05d] 00007
sBaz  [%05d] 00115
sThud [%05d] 00065

uFoo  [%05d] 00000
uBar  [%05d] 00017
uBaz  [%05d] 00247
uThud [%05d] 00065

sFoo  [%5c]     �
sBar  [%5c]     
sBaz  [%5c]     s
sThud [%5c]     A

uFoo  [%5c]     
uBar  [%5c]     
uBaz  [%5c]     �
uThud [%5c]     A
(edited)
Avatar
PDrifting 08-May-21 10:22 PM
Modifications to show %x and %X and some side-effects when dealing with signed numbers.
#include <stdio.h>

typedef char s8;
typedef unsigned char u8;
typedef int s32;

s32 main() {
  s8 sFoo  = -120;
  s8 sBar  = 7;
  s8 sBaz  = 115;
  s8 sThud = 'A';

  u8 uFoo  = 0;
  u8 uBar  = 17;
  u8 uBaz  = 247;
  u8 uThud = 'A';
  
  //shows padding a value with leading zeroes
  //with use of width padding
  //sFoo is going to cause roll and since %x
  //defaults to the width needed 
  //notice an unexpected side-effect when
  //the compiler casts the s8 to s32 for the -120
  printf("sFoo  [%%05x] %05x\n", sFoo);
  printf("sBar  [%%05x] %05x\n", sBar);
  printf("sBaz  [%%05x] %05x\n", sBaz);
  printf("sThud [%%05x] %05x\n\n", sThud);

  printf("uFoo  [%%05x] %05x\n", uFoo);
  printf("uBar  [%%05x] %05x\n", uBar);
  printf("uBaz  [%%05x] %05x\n", uBaz);
  printf("uThud [%%05x] %05x\n\n", uThud);

  //no real difference, just uppercase
  printf("sFoo  [%%05X] %05X\n", sFoo);
  printf("sBar  [%%05X] %05X\n", sBar);
  printf("sBaz  [%%05X] %05X\n", sBaz);
  printf("sThud [%%05X] %05X\n\n", sThud);

  printf("uFoo  [%%05X] %05X\n", uFoo);
  printf("uBar  [%%05X] %05X\n", uBar);
  printf("uBaz  [%%05X] %05X\n", uBaz);
  printf("uThud [%%05X] %05X\n\n", uThud);

  return 0;
}
(edited)
Generated Output:
sFoo  [%05x] ffffff88
sBar  [%05x] 00007
sBaz  [%05x] 00073
sThud [%05x] 00041

uFoo  [%05x] 00000
uBar  [%05x] 00011
uBaz  [%05x] 000f7
uThud [%05x] 00041

sFoo  [%05X] FFFFFF88
sBar  [%05X] 00007
sBaz  [%05X] 00073
sThud [%05X] 00041

uFoo  [%05X] 00000
uBar  [%05X] 00011
uBaz  [%05X] 000F7
uThud [%05X] 00041
(edited)
Avatar
PDrifting 08-May-21 10:33 PM
All Integer Data Types follow what is shown above.  You can change the padding character, width padding, and interchange the Format Specifier with the appropriate type.  The next little program will show how to format Floating Point Data Types.  When declaring with float, literals used to initialise variables are treated as double by default, so you'll need to tack on an 'f' to cast them to float. (edited)
Avatar
PDrifting 24-May-21 04:10 PM
#include <stdio.h>

typedef int s32;
typedef float f32;

s32 main() {
  //this shows the introduction of estimation errors
  //with floating point numbers
  //you will see output that often does not match
  //what you are assigning to your variables
  //there are inaccuracy problems since all floating
  //point type values cannot always be accurately
  //represented with standard bit patterns like the
  //integer types 
    
  f32 f32Foo = 10.2f;
  f32 f32Bar = 0.123456f;
  f32 f32Baz = 123456.0123456f;
  f32 f32Thud = 3.14159265358979323846f;

  //left justify notice the trucation on output
  printf("f32Foo  [%%-f] %-f\n", f32Foo);
  printf("f32Bar  [%%-f] %-f\n", f32Bar);
  printf("f32Baz  [%%-f] %-f\n", f32Baz);
  printf("f32Thud [%%-f] %-f\n", f32Thud);

  //try to force more decimal places
  //you will see more errors introduced at this point
  printf("\nf32Foo  [%%-.10f] %-.10f\n", f32Foo);
  printf("f32Bar  [%%-.10f] %-.10f\n", f32Bar);
  printf("f32Baz  [%%-.10f] %-.10f\n", f32Baz);
  printf("f32Thud [%%-.10f] %-.10f\n", f32Thud);

  //additional formatting
  //note that the left alignment cancels any left
  //padding values used in the format 
  printf("\nf32Foo  [%%-9.2f] %-9.2f\n", f32Foo);
  printf("f32Bar  [%%-9.2f] %-9.2f\n", f32Bar);
  printf("f32Baz  [%%-9.2f] %-9.2f\n", f32Baz);
  printf("f32Thud [%%-9.2f] %-9.2f\n", f32Thud);

  //alignment formatting
  printf("\nf32Foo  [%%9.2f] %9.2f\n", f32Foo);
  printf("f32Bar  [%%9.2f] %9.2f\n", f32Bar);
  printf("f32Baz  [%%9.2f] %9.2f\n", f32Baz);
  printf("f32Thud [%%9.2f] %9.2f\n", f32Thud);

  return 0;
}
(edited)
General Output:
f32Foo  [%-f] 10.200000
f32Bar  [%-f] 0.123456
f32Baz  [%-f] 123456.015625
f32Thud [%-f] 3.141593

f32Foo  [%-.10f] 10.1999998093
f32Bar  [%-.10f] 0.1234560013
f32Baz  [%-.10f] 123456.0156250000
f32Thud [%-.10f] 3.1415927410

f32Foo  [%-9.2f] 10.20    
f32Bar  [%-9.2f] 0.12     
f32Baz  [%-9.2f] 123456.02
f32Thud [%-9.2f] 3.14     

f32Foo  [%9.2f]     10.20
f32Bar  [%9.2f]      0.12
f32Baz  [%9.2f] 123456.02
f32Thud [%9.2f]      3.14
(edited)
Avatar
PDrifting 24-May-21 05:46 PM
This expands on the float example above showing we can get a bit more precision with double but things still get messy.  Since literals are double by default when dealing with Floating Point Types, you do not need to add anything to the end of the literals on initalisation. (edited)
#include <stdio.h>

typedef int s32;
typedef double f64;

s32 main() {
  //this shows the introduction of estimation errors
  //with floating point numbers
  //you will see output that often does not match
  //what you are assigning to your variables
  //there are inaccuracy problems since all floating
  //point type values cannot always be accurately
  //represented with standard bit patterns like the
  //integer types 
    
  f64 f64Foo = 10.2;
  f64 f64Bar = 0.123456;
  f64 f64Baz = 123456.0123456;
  f64 f64Thud = 3.14159265358979323846;

  //left justify notice the trucation on output
  printf("f64Foo  [%%-lf] %-lf\n", f64Foo);
  printf("f64Bar  [%%-lf] %-lf\n", f64Bar);
  printf("f64Baz  [%%-lf] %-lf\n", f64Baz);
  printf("f64Thud [%%-lf] %-lf\n", f64Thud);

  //forcing more decimal places because we have higher //precision with more bits
  //you can still see there are errors being introduced
  //when we extend more decimal places  
  printf("\nf64Foo  [%%-.25lf] %-.25lf\n", f64Foo);
  printf("f64Bar  [%%-.25lf] %-.25lf\n", f64Bar);
  printf("f64Baz  [%%-.25lf] %-.25lf\n", f64Baz);
  printf("f64Thud [%%-.25lf] %-.25lf\n", f64Thud);

  //additional formatting
  //note that the left alignment cancels any left
  //padding values used in the format 
  printf("\nf64Foo  [%%-9.2lf] %-9.2lf\n", f64Foo);
  printf("f64Bar  [%%-9.2lf] %-9.2lf\n", f64Bar);
  printf("f64Baz  [%%-9.2lf] %-9.2lf\n", f64Baz);
  printf("f64Thud [%%-9.2lf] %-9.2lf\n", f64Thud);

  //alignment formatting
  printf("\nf64Foo  [%%9.2lf] %9.2lf\n", f64Foo);
  printf("f64Bar  [%%9.2lf] %9.2lf\n", f64Bar);
  printf("f64Baz  [%%9.2lf] %9.2lf\n", f64Baz);
  printf("f64Thud [%%9.2lf] %9.2lf\n", f64Thud);

  return 0;
}
(edited)
General Output:
f64Foo  [%-lf] 10.200000
f64Bar  [%-lf] 0.123456
f64Baz  [%-lf] 123456.012346
f64Thud [%-lf] 3.141593

f64Foo  [%-.25lf] 10.1999999999999992894572642
f64Bar  [%-.25lf] 0.1234559999999999962971842
f64Baz  [%-.25lf] 123456.0123456000001169741153717
f64Thud [%-.25lf] 3.1415926535897931159979635

f64Foo  [%-9.2lf] 10.20    
f64Bar  [%-9.2lf] 0.12     
f64Baz  [%-9.2lf] 123456.01
f64Thud [%-9.2lf] 3.14     

f64Foo  [%9.2lf]     10.20
f64Bar  [%9.2lf]      0.12
f64Baz  [%9.2lf] 123456.01
f64Thud [%9.2lf]      3.14
Lastly, we'll look at long double.  We need to tack on an 'L' to end of literals used for assignment.  Despite more precision, you will never be able to get absolutely true representations of your values.  All we are going to gain is some extra digits of accuracy.  We'll also look at using E Notation Fomat Specifiers with long double output. (edited)
Avatar
PDrifting 24-May-21 09:12 PM
#include <stdio.h>

typedef int s32;
typedef long double f80;

s32 main() {
  //things do not get much better even with the highest precision
  f80 f80Foo = 10.2L;
  f80 f80Bar = 0.123456L;
  f80 f80Baz = 123456.0123456L;
  f80 f80Thud = 3.14159265358979323846L;

  //left justify notice the truncation on output
  printf("f80Foo  [%%-Lf] %-Lf\n", f80Foo);
  printf("f80Bar  [%%-Lf] %-Lf\n", f80Bar);
  printf("f80Baz  [%%-Lf] %-Lf\n", f80Baz);
  printf("f80Thud [%%-Lf] %-Lf\n", f80Thud);

  //even with long double there is still a shortage of precision
  //and accuracy with the approximated values
  printf("\nf80Foo  [%%-.40Lf] %-.40Lf\n", f80Foo);
  printf("f80Bar  [%%-.40Lf] %-.40Lf\n", f80Bar);
  printf("f80Baz  [%%-.40Lf] %-.40Lf\n", f80Baz);
  printf("f80Thud [%%-.40Lf] %-.40Lf\n", f80Thud);

  //additional formatting
  //note that the left alignment cancels any left
  //padding values used in the format 
  printf("\nf80Foo  [%%-9.2Lf] %-9.2Lf\n", f80Foo);
  printf("f80Bar  [%%-9.2Lf] %-9.2Lf\n", f80Bar);
  printf("f80Baz  [%%-9.2Lf] %-9.2Lf\n", f80Baz);
  printf("f80Thud [%%-9.2Lf] %-9.2Lf\n", f80Thud);

  //alignment formatting
  printf("\nf80Foo  [%%9.2Lf] %9.2Lf\n", f80Foo);
  printf("f80Bar  [%%9.2Lf] %9.2Lf\n", f80Bar);
  printf("f80Baz  [%%9.2Lf] %9.2Lf\n", f80Baz);
  printf("f80Thud [%%9.2Lf] %9.2Lf\n", f80Thud);

  //E Notation will ignore the left padding since there will
  //only ever be a single digit to the left of the floating point
  printf("\nf80Foo  [%%.3Le] %.6Le\n", f80Foo);
  printf("f80Bar  [%%.3Le] %.6Le\n", f80Bar);
  printf("f80Baz  [%%.3Le] %.6Le\n", f80Baz);
  printf("f80Thud [%%.3Le] %.6Le\n", f80Thud);

  return 0;
}
(edited)
General Output:
f80Foo  [%-Lf] 10.200000
f80Bar  [%-Lf] 0.123456
f80Baz  [%-Lf] 123456.012346
f80Thud [%-Lf] 3.141593

f80Foo  [%-.40Lf] 10.1999999999999999998265276524023192905588
f80Bar  [%-.40Lf] 0.1234559999999999999970240818769617874295
f80Baz  [%-.40Lf] 123456.0123456000000032872776500880718231201172
f80Thud [%-.40Lf] 3.1415926535897932385128089594061862044327

f80Foo  [%-9.2Lf] 10.20    
f80Bar  [%-9.2Lf] 0.12     
f80Baz  [%-9.2Lf] 123456.01
f80Thud [%-9.2Lf] 3.14     

f80Foo  [%9.2Lf]     10.20
f80Bar  [%9.2Lf]      0.12
f80Baz  [%9.2Lf] 123456.01
f80Thud [%9.2Lf]      3.14

f80Foo  [%.3Le] 1.020000e+01
f80Bar  [%.3Le] 1.234560e-01
f80Baz  [%.3Le] 1.234560e+05
f80Thud [%.3Le] 3.141593e+00

More problems are created when we consider the case of 0 with floating point numbers.  Like every other value stored inside a Floating Point Type, it will be approximated.  This creates confusion when programmers assign a value of 0 and then attempt to do comparisons only to find out 0 does not equal 0 in the world of approximated values.  We'll explore this more when we get to if branching.

For now let's dig into the basics of Pointer Types. (edited)
Avatar
PDrifting 24-May-21 09:25 PM
Part 4: Pointer Basics (edited)
As mentioned prior, Pointer Types are a troubling subject for C programmers know matter their experience.  We'll cover some scenarios with code and hopefully demystify some of the confusion surrounding them.
This is a basic program with output showing how to declare variables, structures, unions, an introduction to pointers, getting the address of things, and declaring function main. (edited)
Avatar
PDrifting 25-May-21 06:39 PM
#include <stdio.h>

typedef int s32;

typedef struct {
  s32 flob;
  s32 corge;
  s32 plugh;
} TFCP;

typedef union {
  struct {
    s32 eggs;
    s32 ham;
  };
  s32 spam[2];
} TEHS;

s32 main() { 
  //every variable, pointer, structure, union, member and function
  //are assigned an addressable location in memory on the computer
  s32 u32Foo = 12;

  //pointers store these addresses for lookup
  //the * in front a variable denotes this is a pointer
  //the & means the address of something
  s32 *u32Bar = &u32Foo;

  TFCP thud = {};
  TFCP *qux = &thud;

  TEHS garply = {};
  TEHS *grault = &garply;

  //we have only covered function main to this point
  //in order to create a function pointer to main
  //we must match the return type of int
  //give the function pointer a name (*name)
  //and an argument list referenced by the following ()
  //you are then able to assign the address of matching
  //functions that follow the same function pointer prototype
  int (*fp)() = &main;

  printf("Address of  u32Foo = %p\n", &u32Foo);
  printf("Address at *u32Bar = %p\n", u32Bar);
  printf("Address of *u32Bar = %p\n\n", &u32Bar);

  printf("Address of    thud = %p\n", &thud);
  printf("        thud.flob  = %p\n", &(thud.flob));
  printf("        thud.corge = %p\n", &(thud.corge));
  printf("        thud.plugh = %p\n", &(thud.plugh));
  printf("Address at    *qux = %p\n", qux);
  printf("Address of    *qux = %p\n\n", &qux);  

  printf("Address of  garply = %p\n", &garply);
  printf("    garply.eggs    = %p\n", &(garply.eggs));
  printf("    garply.ham     = %p\n", &(garply.ham));
  printf("    garply.spam[0] = %p\n", &(garply.spam[0]));
  printf("    garply.spam[1] = %p\n", &(garply.spam[1]));
  printf("Address at *grault = %p\n", grault);
  printf("Address of *grault = %p\n\n", &grault); 

  printf("Address of  main() = %p\n", &main);
  printf("Address at     *fp = %p\n", fp);
  printf("Address of     *fp = %p\n\n", &fp);

  return 0;
}
(edited)
General Output:
Address of  u32Foo = 0x7ffd0424af08
Address at *u32Bar = 0x7ffd0424af08
Address of *u32Bar = 0x7ffd0424af00

Address of    thud = 0x7ffd0424aef0
        thud.flob  = 0x7ffd0424aef0
        thud.corge = 0x7ffd0424aef4
        thud.plugh = 0x7ffd0424aef8
Address at    *qux = 0x7ffd0424aef0
Address of    *qux = 0x7ffd0424aee8

Address of  garply = 0x7ffd0424aee0
    garply.eggs    = 0x7ffd0424aee0
    garply.ham     = 0x7ffd0424aee4
    garply.spam[0] = 0x7ffd0424aee0
    garply.spam[1] = 0x7ffd0424aee4
Address at *grault = 0x7ffd0424aee0
Address of *grault = 0x7ffe28e72538

Address of  main() = 0x400540
Address at     *fp = 0x400540
Address of     *fp = 0x7ffd0424aed0

NOTE: Everytime you execute this program these memory addresses will be different.  This is only the current snapshot of the memory layout at the time the example was executed.  You should expect things to move around in memory.  The references that follow are based on this current snapshot for the machine it was executed on. (edited)
Avatar
PDrifting 26-May-21 11:37 AM
If we remember back when we were looking our bitwidths and byte requirements of individual Types there are some things we can glean from what we're seeing in this output.  Let's dissect this a little to figure out what the computer this is running on has done and things to be mindful of.
s32 u32Foo = 12;
s32 *u32Bar = &u32Foo;

Address of  u32Foo = 0x7ffd0424af08
Address at *u32Bar = 0x7ffd0424af08
Address of *u32Bar = 0x7ffd0424af00
In the code we declared u32Foo before *u32Bar, yet in memory based on the addresses we can see *u32Bar was placed in memory before u32Foo.  How can we determine this from those addresses?  Like any representation of a number, those hex formatted addresses are still read from right to left.  We can split them up into byte pairs and then determine the most significant portion of what we are looking at.
Avatar
PDrifting 26-May-21 11:47 AM
Byte Pairs
01 02 03 04 05 06
7f|fd|04|24|af|08 u32Foo appears 8 bytes after *u32Bar in memory
7f|fd|04|24|af|00 *u32Bar is 8 bytes

//we are only looking at byte pair 06 when determining the 8 bytes used [08 - 00 = 8]
//or by looking at the addresses as a whole [7ffd0424af08 - 7ffd0424af00 = 8]
(edited)
Avatar
PDrifting 26-May-21 11:59 AM
The next problem we should address is the out of order problem in memory.  Any time you declare something in C it can cause Memory Fragmentation depending on how it was declared.  Memory Fragmentation will be discussed in more detail when we begin dealing with malloc and free a bit later.  Individual variables in this case clearly show the order they are declared in does not guarantee that same order in memory.  We can also learn from looking at this, that any declared pointer is using 8 bytes of memory.  So pointers are 64-bit based on the architecture this code was compiled on.  This can change depending on your system configuration, and compiler setup also.  Let's look at another feature of the addresses shown. (edited)
Address of  u32Foo = 0x7ffd0424af08
Address at *u32Bar = 0x7ffd0424af08
Address of *u32Bar = 0x7ffd0424af00
When we say pointers store an address of something, we can clearly see this is true.  The address stored at *u32Bar is the same address of the variable u32Foo.  This should be the case because we assigned the address of u32Foo to *u32Bar when we declared *u32Bar.  By using the amperstand [&] we fetched the address of u32Foo.  We will see this replicates in the same way when we deal with the other pieces of this examples. (edited)
Let's take a look at how the struct TFCP and the pointer we coupled it with look in memory.  
Address of    thud = 0x7ffd0424aef0
        thud.flob  = 0x7ffd0424aef0
        thud.corge = 0x7ffd0424aef4
        thud.plugh = 0x7ffd0424aef8
Address at    *qux = 0x7ffd0424aef0
Address of    *qux = 0x7ffd0424aee8
Avatar
PDrifting 26-May-21 12:23 PM
We can see from the addresses of u32Foo and *u32Bar and the addresses here that we have moved to a different region of memory.  The struct TFCP  appears before those other variables.  Byte pair 05 changed from AF [175] to AE [174], where 175 > 174, so we know we are in an early region of memory.  Since memory on any computer is addressed in bytes, smaller memory addresses are always going to be in a region of memory before the next largest memory address. This is what allows us to actually look at memory layouts and figure out where something is, and based on things around it, approximate how many bytes it may be consuming.  In the case of  struct TFCP we'll also be able to figure something else out.  The members thud.flob, thud.corge, thud.plugh, and byte pair 06 show they are laid out in order by fours.  This makes sense, because they are declared as s32 which was typedefed from an int which we know uses 4 bytes of memory.  Also, remember that *qux holds the address pointing to the start of struct TFCP, but the address of *qux, like any pointer is going to have its own address as well. 

NOTE:  The C Standard guarantees that any struct declaration will always have member layout in the order it is declared unless you use an alternate alignment modifier on the struct. (edited)
Avatar
PDrifting 26-May-21 12:31 PM
If unions give you problems visualising, hopefully this will help sort it out.  Next we'll look at the union TEHS which we created in the example.  
Address of  garply = 0x7ffd0424aee0
    garply.eggs    = 0x7ffd0424aee0
    garply.ham     = 0x7ffd0424aee4
    garply.spam[0] = 0x7ffd0424aee0
    garply.spam[1] = 0x7ffd0424aee4
Address at *grault = 0x7ffd0424aee0
Address of *grault = 0x7ffe28e72538
(edited)
Avatar
PDrifting 26-May-21 02:44 PM
Unions as we know, can share regions of memory with other members depending on how the union was declared.
typedef union {
  struct {
    s32 eggs;
    s32 ham;
  };
  s32 spam[2];
} TEHS;
Avatar
PDrifting 26-May-21 03:44 PM
The union declares a group of member variables inside a nameless struct.  Then we declare spam as an array with 2 elements as another member.  Logically, we should be able to conclude from this declaration layout that eggs will map to spam[0] and ham will map to spam[1].  By looking at the addresses of each of the member variables we can see this is the case.  This is the basic fundamental concept of a pointer.  When you update a union member, the associated union member will also update.  A pointer will do the same thing since it points to the address of something. We can also conclude that anything we do with the pointer has the potential to update what the pointer is pointing to.  Before we explore this, we'll finish reviewing the *fp declare. (edited)
Address of  main() = 0x400540
Address at     *fp = 0x400540
Address of     *fp = 0x7ffd0424aed0
Avatar
PDrifting 26-May-21 03:52 PM
As mentioned, everything pretty much has an address, right down to the compiled byte code encoded internally to the executable.  Function main() is no different.  There are cases where this will prove to be very useful.  Like all pointers *fp points to something and has its own address.  Pointers can point to other pointers.  Unlike other pointers though, a function pointer is able to call/invoke the function its pointing too.  This will be covered later when we go over functions.  It's important that we finish going over pointers.
Avatar
PDrifting 29-May-21 04:22 PM
Basic program with output, showing how we can use pointers to map different data types, output showing that when we update the pointer the thing we point to also updates, and a method for determining what Endianness your current hardware is using, and layout for function main. (edited)
#include <stdio.h>

typedef unsigned char u8;
typedef int s32;
typedef unsigned long long u64;

s32 main() {
  //we're going to create a simple byte map
  //of a u64 integer so we need 8 bytes
  //intialise it to 0  
  u8 u64Map[8] = {};
  
  //set up an unsigned 64-bit integer
  //filling every bit with something
  //creating 8 bytes of data
  u64 foo = 0xffeeddccbbaa9988ULL;
  
  //remember arrays are pointers
  //so we can use the name u64map as we saw
  //above it stores the start address of
  //u64map[0] we don't really need to do this
  //its merely for reinforcement of a concept
  u8 *bar = u64Map;
  
  //this creates an unsigned char pointer
  //and casts our unsigned 64-bit integer
  //to an unsigned 8-bit char pointer
  u8 *fuzz = (u8 *)&foo;
  
  //we need to remember to use %Lx for 64-bit integers
  printf("foo = %Lx\n\n", foo);
  
  //once we map our pointers, just like mentioned
  //when discussing pointers when we update any
  //element of pointer bar we are going to
  //acutally be updating u64map elements
  //we can see this here
  bar[0] = fuzz[0];
  printf("bar[0] u64Map[0] = %x %x\n", bar[0], u64Map[0]);
  bar[1] = fuzz[1];
  printf("bar[1] u64Map[1] = %x %x\n", bar[1], u64Map[1]);
  bar[2] = fuzz[2];
  printf("bar[2] u64Map[2] = %x %x\n", bar[2], u64Map[2]);
  bar[3] = fuzz[3];
  printf("bar[3] u64Map[3] = %x %x\n", bar[3], u64Map[3]);
  bar[4] = fuzz[4];
  printf("bar[4] u64Map[4] = %x %x\n", bar[4], u64Map[4]);
  bar[5] = fuzz[5];
  printf("bar[5] u64Map[5] = %x %x\n", bar[5], u64Map[5]);
  bar[6] = fuzz[6];
  printf("bar[6] u64Map[6] = %x %x\n", bar[6], u64Map[6]);
  bar[7] = fuzz[7];
  printf("bar[7] u64Map[7] = %x %x\n", bar[7], u64Map[7]);
  
  return 0;
}
(edited)
General Output:
foo = ffeeddccbbaa9988

bar[0] u64Map[0] = 88 88
bar[1] u64Map[1] = 99 99
bar[2] u64Map[2] = aa aa
bar[3] u64Map[3] = bb bb
bar[4] u64Map[4] = cc cc
bar[5] u64Map[5] = dd dd
bar[6] u64Map[6] = ee ee
bar[7] u64Map[7] = ff ff
Avatar
PDrifting 29-May-21 04:40 PM
Looking at the way the array mapped byte by byte from the integer we can see it mapped backwards.  Depending on the architecture you are using this may change.  What we see here is an effect caused by Little-Endianness.  If we were on a Big-Endianness architecture the array would be mapped from left to right and would appear as it is displayed.  Here's a basic table on which architectures are which. (edited)
Endianness

Little                  Max Bits    Big               Max Bits    Bi/Mixed/Other    Max Bits
---------------------------------------------------------------------------------------------
PDP-11                  16          CDC 3000 Series   48          CDC 6000 Series   12 -> 60
8080                    8           System/360        32          PDP-8             12
6502                    8           System/370        32          MIPS              32 -> 64
Z80                     8           zESAME Series     64          ARM/A32 Series    32
VAX                     32          6809              8           SPARC             32 -> 64
8051                    8  -> 32    680x0             32          RISC-HP/PA        32 -> 64
x86 Series              16 -> 64    DLX               32          Power PC/ISA      32 -> 64
NS32K Series            32          MMIX              64          Alpha             64
Transputer              4  -> 64    AVR32             32          ARM/TDMI          32
AVR                     8           Mixo32            32          SuperH Series     32 -> 64
Blackfin                32          Sega Genesis      16          ARC               16 -> 32
Crusoe Series           32          Sony PS1/PS2/PS3  32          M32R              32
RA Series               16          XBox 360          64          Itanium           64
RZ/Cortex Series        32 -> 64    Nintendo 64       64          RISC-eSI          16 -> 32
Sunplus SPG290          32          Nintendo Gamecube 64          ARM/A64           64
RISC-V                  32 -> 128   Nintendo WII/U    64
Elbrus                  64
Nintendo TV-Game        8
Nintendo [NES]          8
Nintendo Gameboy/Color  8
Nintendo [Super]        16
Nintendo 3/DS/XL        32
Nintendo Virtualboy     32
Nintendo Switch         64
XBox One                64
Atari Consoles          8  -> 64
Sony PS4/PS5            64
(edited)
Avatar
PDrifting 30-May-21 12:34 AM
The problem with this might not be apparent immediately, however, if we store data in binary formats, pass information across networks, store data in some other way that may do encoding with a certain Endianness, things are going get a little wonky.  It's unlikely you'll be coding on a majority of these platforms, but a career in software engineering might have you crossing paths with older systems still in the wild running legacy code.  Migrating data from one architecture to another will require you have some understanding of how integer data will be stored.  Modern coding does create some problems specifically when creating games, especially ones that are multi-player crossing platforms.  If you support phones, you're going to be running into ARM based architecture which is BI-Endianness and will be determined by the operating system installed on the device.  While your server may be running on some other architecture that will be different Endianness.  Regardless, you are encouraged to do research to determine the hardware and operating system limitations that will effect how things are stored in memory. (edited)
Here's another table showing Endianness by Operating Systems.
Avatar
PDrifting 30-May-21 01:55 AM
Endianness

Little                  Big                     Determined by Hardware
----------------------------------------------------------------------
Android                 Apple Mac OS            Linux
Apple OSX               HP UNIX                 Solaris
iOS                     Amiga OS                IBM Linux
Microsoft Windows
HP VMS
OS/2
(edited)
Generally most architectures and operating systems are moving exclusively towards Little-Endianness.  Neither of the above tables should be considered complete or exhaustive, but are provided merely to show examples that there are different circumstances where you should be considering how you think about data storage on your given platform.  There are cases where networking protocols, specifically TCP come to mind that are Big-Endian.  For the time being we'll cover a few more basics of pointers showing how we might take Endianness into consideration.  Future examples of code will generally ignore Endianess unless specifically required. (edited)
Avatar
PDrifting 30-May-21 08:36 PM
Part 5: Using sizeof() (edited)
Avatar
PDrifting 30-May-21 09:12 PM
As we expand into our understanding of pointers and memory, there is a useful Operator called sizeof.  It is calculated during compile time and will result in the compiler returning a value that will be representative of the size in bytes of the things you requested the sizeof. (edited)
Basic program with output, showing the use of sizeof, a brief introduction to padding and working with addresses, an introduction malloc, also free, and the basic use of main.
#include <stdio.h>
#include <stdlib.h>

typedef char s8;
typedef unsigned char u8;
typedef short s16;
typedef unsigned short u16;
typedef int s32;
typedef unsigned int u32;
typedef long long s64;
typedef unsigned long long u64;

typedef float f32;
typedef double f64;
typedef long double f80;

typedef struct {  
  s8 foo[100];
  u64 bar;  
} TFooBar;

s32 main() {
  TFooBar thud = {};
  //sizeof is a macro used to determine the size of whatever
  //you stick in between the parenthesis returned in bytes used
  printf("size of s8  = %lu\n", sizeof(s8));
  printf("size of u8  = %lu\n", sizeof(u8));
  printf("size of s16 = %lu\n", sizeof(s16));
  printf("size of u16 = %lu\n", sizeof(u16));
  printf("size of s32 = %lu\n", sizeof(s32));
  printf("size of u32 = %lu\n", sizeof(u32));
  printf("size of s64 = %lu\n", sizeof(s64));
  printf("size of u64 = %lu\n", sizeof(u64));
  printf("size of f32 = %lu\n", sizeof(f32));
  printf("size of f64 = %lu\n", sizeof(f64));
  printf("size of f80 = %lu\n\n", sizeof(f80));
  printf("size of TFooBar     = %lu\n", sizeof(thud));
  printf("size of TFooBar.foo = %lu\n", sizeof(thud.foo));
  printf("size of TFooBar.bar = %lu\n", sizeof(thud.bar));
  printf("address of TFoobar.foo = %p\n", &thud.foo);
  printf("address of TFoobar.bar = %p\n", &thud.bar);
  printf("gap between addresses  = %Lu\n", (u64)&thud.bar - (u64)&thud.foo);
  printf("padding in TFooBar  = %lu\n",
    sizeof(thud) - (sizeof(thud.foo) + sizeof(thud.bar))
  );
  
  //this is a C++ friendly form of a malloc call
  //type of thing to create a pointer from called fooBar
  //cast the return from the malloc to the given type
  //call malloc passing how much space you are requesting
  //in this case we would like to allocate enough space
  //for a single instance of TFooBar
  TFooBar *fooBar = (TFooBar *)malloc(sizeof(TFooBar));
  
  //don't forget to call free on the pointer
  free(fooBar);
  
  return 0;
}
(edited)
General Output:
size of s8  = 1
size of u8  = 1
size of s16 = 2
size of u16 = 2
size of s32 = 4
size of u32 = 4
size of s64 = 8
size of u64 = 8
size of f32 = 4
size of f64 = 8
size of f80 = 16

size of TFooBar     = 112
size of TFooBar.foo = 100
size of TFooBar.bar = 8
address of TFoobar.foo = 0x7ffdd45a3bc8
address of TFoobar.bar = 0x7ffdd45a3c30
gap between addresses  = 104
padding in TFooBar  = 4
Avatar
PDrifting 30-May-21 10:19 PM
Each of the values displayed by the example program above, short of the addresses, are measured in bytes.  If we recall back in the early part of this text, we had a table of Integer and Float Types and their associated byte/bitwidths.  All the base types in this case should show the corresponding matching byte requirements.  The exception in this case is the f80 which was mapped from long double.  It shows 16 bytes being used, however, it should be known that only 10 bytes will ever be used according to the C Standard for precision.  Some padding has taken place.  This is a good way to figure out what your bitwidths will be for given types in the future if you're unsure of your given limitations on a given platform, architecture or under a given operating system.

The other section of the output deals with the sizeof a struct and it's members.  As shown in this case, the C Standard dictates that the compiler for memory alignment can add padding.  In this case the 100 elements that we declared for TFooBar.foo, created a gap filled by padding of 4 bytes.  Despite the struct having a sizeof 112, the members of TFooBar only actually use 108 bytes in total.  These are useful ways to find out how your struct is using memory.  For now, your understanding is unlikely to take advantage of what all this means, but this is strictly for exposure to how you can determine these things later when you need to.

Finally, we have the malloc and free that didn't really have any side-effects or purpose in this code, other than to show why we needed to cover sizeof.  We will be covering proper use of malloc and free later.  For now we're going to tie up our basics on pointers and continue on to Functions.  Pointers were needed in basic understanding so we could continue on to the next part of our programming understanding. (edited)
Avatar
PDrifting 30-May-21 10:30 PM
Part 6: Introduction to Functions (edited)
Avatar
PDrifting 30-May-21 11:57 PM
It has taken a bit longer than normal to get to this part, but one of the purposes of the order of this text is to make sure we are not covering anything without first knowing or having exposure to the base concepts prior.  Functions are a very useful feature of programming.  They allow splitting up code, creating sections that are reusable, or just in general grouping code by purpose for what it does.  Let's dive into some examples and cover some basics.

Basic program with output, showing how to create and call a Function from main.
#include <stdio.h>

typedef int s32;

//functions follow a given form known as a prototype
//return type name(argument list)
//in this case our return type is void telling us
//our function does not return anything
//in this case we do not need have a return statement
//line we normally have had in the past when we leave main
//our function has a name of foo and its has no arguments
//we need to remember that C is a delcare before use
//this goes for functions as well so we must make sure
//that our functions like anything else appear before
//we use them
void foo() {
  puts("Hello World!");
}

s32 main() {
  //this calls function foo with no arguments
  //when the call to foo is complete it will return
  //to the line after the foo() call and carry on
  //with the program
  foo();  
  return 0;
}
(edited)
General Output:
Hello World!
Let's carry on with another basic program with out, showing how to create and call a function with arguments from main. (edited)
#include <stdio.h>

typedef int s32;

//like the prior example we are not returning anything
//as designated by the return type being void
//we are still naming our function foo, however
//we have an argument in the argument list
//arguments follow the base form a normal variable
//declare in that they have a type and a name
void foo(s32 bar) {
  printf("value of bar = %i\n", bar);
}

s32 main() {
  //since we have a function that can take an argument now
  //we are passing a value of 1 to foo and since the
  //argument list for foo declares and int called bar
  //when we call the function the argument variable
  //bar will be assigned the value we pass it
  //so in this case bar in the function will equal 1
  foo(1);

  //now that we have a function we can call it whenever
  //we want to so in this case we are passing -2344 so
  //when foo is called bar will be assigned this value
  //just like above
  foo(-2344);

  //in this case we are passing a char literal which we
  //can do because we know char literals are promoted to
  //int types automatically
  foo('Z');
  
  return 0;
}
(edited)
General Output:
value of bar = 1
value of bar = -2344
value of bar = 90
Hopefully now based on what we've covered prior, this should be relatively easy so far.  Here's another basic program with output, showing how to create and call a function with multiple arguments from main. (edited)
Avatar
PDrifting 31-May-21 10:22 AM
#include <stdio.h>

typedef int s32;
typedef float f32;

//arguments can be separatly listed by using
//a comma to declare them as shown here
void foo(s32 bar, f32 thud) {
  printf("value of bar  = %i\n", bar);
  printf("value of thud = %f\n\n", thud);
}

s32 main() {
  //similarly when calling functions that expect more
  //than one argument, you list them separatly also
  //with commas
  foo(1, 0.03f);
  foo(-2344, 1.24567f);
  foo('Z', -7.41f);

  return 0;
}

General Output: 
value of bar  = 1
value of thud = 0.030000

value of bar  = -2344
value of thud = 1.245670

value of bar  = 90
value of thud = -7.410000
(edited)
Avatar
PDrifting 31-May-21 10:53 AM
What happens if we want to use a Function to update a value? This is called passing by reference.  Normally arguments are merely copied, or passed by value, and disposed once the Function has finished and exits.  There are ways we can create persistent states.  Over the next few examples we explore this.

Basic program with output, showing how to pass a value by reference to a function that uses a pointer from main. (edited)
Avatar
PDrifting 31-May-21 01:46 PM
#include <stdio.h>

typedef int s32;
typedef float f32;

//we have declared bar in this case as a pointer
//so the changes we make to bar can persist
//since we are working with a direct memory region
//that exists outside of function foo
//this is known as passing by reference
//we have left thud as a non-pointer so it will
//default to passing by value
void foo(s32 *bar, f32 thud) {
  //we know that using bar = thud would assign
  //a value that would become the address
  //we know that using bar = &thud would assign
  //the address of thud to the address stored by bar
  //in this case we need to assign the value of
  //thud to the value stored at the address of bar
  //so we must use *bar to accomplish the assignment
  //this is known as dereferencing a pointer
  *bar = thud;
  
  //this is not a pointer, so despite assigning it
  //a new value, this change will not persist once
  //the function exits because thud is only a local
  //copy that will not persist
  thud = 5.0f;
}

s32 main() {  
  s32 bar = 1;
  f32 thud = 2.0f;

  //because bar is not a pointer we must remember
  //that we can pass the address of something
  //we know that getting the address of something is
  //done using the amperstand [&] in front of it
  //in this case &bar is converted to a temporary
  //pointer to the address of bar
  //thud is passed normally to show the basic
  //difference between passing by referrence and
  //passing by value
  foo(&bar, thud);
  
  //bar will show a new value changed from 1
  //because it was passed by reference
  printf("value of bar  = %i\n", bar);
  //thud will state 2.0 and not be changed to 5.0
  //because it was passed by value
  printf("value of thud = %f\n", thud);

  return 0;
}
(edited)
General Output:
value of bar  = 2
value of thud = 2.000000
Avatar
PDrifting 06-Jun-21 12:08 AM
What happens if we have a lot of arguments that we need to pass to a function? In terms of much of the Linux or Windows Application Programming Interface [LAPI or WAPI] we will be running into Functions that require a lot of parameters.  There isn't much we can do when it comes to how things have been written in the past, but we can be mindful of how future programmers deal with these sorts of problems.  For instance if we look at XCreateWindow from Linux, we will see something that looks like this for a rough outline of a prototype.  
Window XCreateWindow(display, parent, x, y, width, height, border_width, depth, 
                     class, visual, valuemask, attributes)
(edited)
Many of the LAPI and WAPI Functions have very wide argument lists.  When you begin to look at what many of these are defined as, you will begin to get a little overwhelmed.
Window XCreateWindow(
  Display *display,
  Window parent,
  int x,
  int y,
  unsigned int width,
  unsigned int height,
  unsigned int border_width,
  int depth,
  unsigned int class,
  Visual *visual,
  unsigned long valuemask,
  XSetWindowAttributes *attributes
)
(edited)
Avatar
PDrifting 06-Jun-21 12:23 AM
This idea was to create flexibility, but created a cost to programmers with additional complexity.  Without typedefs, we create wide declarations, coupled with custom Type Definitions such as Display, Window, Visual and XSetWindowAttributes.  Each of these will add overhead to the program that must be used and populated.   While also remembering the order and what each argument is expecting.  This may have been acceptable in the past, not so sure we should be designing things this way for the preservation of sanity to next generations of programmers.  This a primary reason C has a bad reputation, generated from this type of low level nightmare.

Another problem we face when looking at C code is when it was written.  Types did not always have the same bit widths as they do now.  Up to this point we have made the assumption that we are running on modern 64-bit platforms.  When the LAPI code was written that includes XCreateWindow, int would have been 16-bit [2 bytes], and long would have been 32-bit [4 bytes].  Upto this point we have been using typedef statements and creating aliases such as s32 or s64.  One of the reasons this is done is to make it clear what bit width we are coding against for a given Type.  Depending on the age of C code, you must take these things into consideration.  Since architecture in the future is likely to expand from 64-bit to 128-bit, or higher we should be mindful that like in the past, Types are going to change bit widths. (edited)
Generally in this case it would be preferable to write something in this way.  Basic general program that will not run showing a model of how this might be addressed in the future.  NOTE: WILL NOT COMPILE.  This is only for reference.
Avatar
PDrifting 06-Jun-21 12:57 AM
//long is a good indicator this code was written before 64-bit architecture
//which would make types shift where long is modern int
//and int would be modern short
//in this case...
//long is 32 bit
//int is 16 bit

//we can get around this by including fixed width type
//definitions that are found in the following library
#include <stdint.h>

//then we can typedef by specific widths to make
//code portable across different platforms
//all examples in the future will switch to using
//this style of typedef to promote habits around
//future proofing code
typedef int16_t s16;
typedef uint16_t u16;
typedef int32_t s32;

typedef struct {
  Display *display,
  Window parent,
  s16 x,
  s16 y,
  u16 width,
  u16 height,
  u16 border_width,
  s16 depth,
  u16 class,
  Visual *visual,
  s32 valuemask,
  XSetWindowAttributes *attributes
} XCreateWindowArgs

Window XCreateWindow(XCreateWindowArgs args) {
   Windows r = {};
   //do whatever the method used to do...
   return r;
}

s32 main() {
  //in this case we are just defaulting the members to 0
  //args in this case could be initialised using standard
  //member assignment out of order
  //most IDEs, even basic ones will be able to provide
  //the list of members available to args
  //in general this is just a better way to deal with this
  XCreateWindowArgs args = {};
  Window window = {};

  //as a struct you don't need to worry about remembering
  //what order the arguments need to be in
  window = XCreateWindow(args);

  return 0;
}
(edited)
Avatar
PDrifting 07-Jun-21 03:29 PM
Over the next few examples we'll cover initialising things inside Functions and passing them back.  We have not really handled return values yet, so those will also be explored.  Depending on what we are dealing with, there are different methods for each to consider. (edited)
NOTE: As we start switching over to using stdint.h for portability there are a few caveats to remember.  There is no equivalent to char or _wchar_t_ for fixed bit width types.  The _uint8_t_ and _int8_t_ have no overlap as char is not signed or unsigned and is treated as a third unique 8-bit type.  Type _uint16_t_ and _int16_t_ also do not overlap with _wchar_t_.

Basic program with output showing how to initialise a structure from a function, return it, printing out some of its member values, and setting up function main. (edited)
Avatar
PDrifting 11-Jun-21 08:05 AM
#include <stdio.h>
#include <stdint.h>

//remember we are switching to portable equivalent types
typedef int32_t s32;
typedef uint32_t u32;
typedef uint64_t u64;

typedef struct {
  s32 foo;
  u32 bar;
} TFBT;

TFBT initTFBT(s32 foo, u32 bar) {  
  //compound literal - in case you want to know
  //what to search for in google
  return (TFBT) {
    .foo = foo,
    .bar = bar,
  };
}

void initTFBTAlt(TFBT *r) {
  //assign the return value from initTFBT
  //to the value stored at pointer r that was
  //passed as an argument
  *r = initTFBT(-26, 12);
}

s32 main() {  
  //preferred initialisers based on what we know of structs 
  
  //TFBT bazz = { .foo = -26, .bar = 12};
  //TFBT buzz would match the bazz initialisation

  //when we get to the array, it doesn't really
  //get much more complex since we have a linear
  //declaration of values
  //there are cases later where this style will
  //just be too burdensome so use clarity
  //where appropriate

  //TFBT arr2[] = {
  //  { .foo = -20, .bar = 60},
  //  { .foo = -26, .bar = -12},
  //  { .foo = -30, .bar = 80},
  //  { .foo = -26, .bar = -12},
  //}

  TFBT bazz = initTFBT(-26, 12);
  
  TFBT buzz = {};
  initTFBTAlt(&buzz);

  TFBT arr[4] = {};
  arr[0] = initTFBT(-20,60);
  initTFBTAlt(&arr[1]);
  arr[2] = initTFBT(-30,80);
  initTFBTAlt(&arr[3]);

  printf("bazz.foo = %i\n", bazz.foo);
  printf("bazz.bar = %u\n", bazz.bar);
  printf("buzz.foo = %i\n", buzz.foo);
  printf("buzz.bar = %u\n", buzz.bar);  
  printf("arr[0].foo = %i\n", arr[0].foo);
  printf("arr[0].bar = %i\n", arr[0].bar);
  printf("arr[1].foo = %i\n", arr[1].foo);
  printf("arr[1].bar = %i\n", arr[1].bar);
  printf("arr[2].foo = %i\n", arr[2].foo);
  printf("arr[2].bar = %i\n", arr[2].bar);
  printf("arr[3].foo = %i\n", arr[3].foo);
  printf("arr[3].bar = %i\n", arr[3].bar);

  return 0;
}
(edited)
General Output: 
bazz.foo = -26
bazz.bar = 12
buzz.foo = -26
buzz.bar = 12
arr[0].foo = -20
arr[0].bar = 60
arr[1].foo = -26
arr[1].bar = 12
arr[2].foo = -30
arr[2].bar = 80
arr[3].foo = -26
arr[3].bar = 12

Basic program with output showing how to use malloc to initialise memory from a function, assigning some values within context of the allocated memory, using free, and setup of function main. (edited)
Avatar
PDrifting 11-Jun-21 08:54 AM
#include <stdlib.h>
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;

typedef struct {
  s32 foo;
  c8 bar;  
} TFB;

TFB *newTFB() {
  //normally when using malloc we should
  //be checking to make sure the malloc
  //succeeded, however we have not learned
  //about if or expressions yet
  //for now we are just assuming everything
  //is working as it should
  TFB *r = (TFB *)malloc(sizeof(TFB));
  r->foo = 23;
  r->bar = 'A';
  return r;
}

//this is where pointers and malloc get
//a lot of programmers hung up
//we must make sure if we are going to
//use an argument pointer to pass back
//malloc allocated memory we must use
//an extra * on the pointer
//this creates a pointer to the pointer
//if you do not remember the extra *
//the argument variable you are expecting
//to be allocated will fail and you will
//create a dangling pointer
void newTFBAlt(TFB **r) {
  printf(" r   %p\n", r);
  printf("*r   %p\n", *r);

  //the next part that causes confusion is
  //remembering that we must use a
  //dereference to the pointer argument
  *r = (TFB *)malloc(sizeof(TFB));
  //remember this special form of parenthesis
  //use when assigning values to a pointer in
  //this special case
  //effectively we are (*r) looking up the
  //pointer stored at the pointer **r and
  //and then using the -> pointer member
  //method of referring to the structure
  //stored at at (*r)
  (*r)->foo = 23;
  (*r)->bar = 'A';

  printf(" r   %p\n", r);
  printf("*r   %p\n", *r);
}

s32 main() {
  TFB *bazz = newTFB();

  TFB *buzz = NULL;
  printf("buzz %p\n", &buzz);
  //when passing a pointer in this context
  //to satisfy the **r we must pass the
  //address of pointer buzz
  newTFBAlt(&buzz);
 
  printf("bazz.foo = %d\n", bazz->foo);
  printf("bazz.bar = %c\n", bazz->bar);
  printf("buzz.foo = %d\n", buzz->foo);
  printf("buzz.bar = %c\n", buzz->bar);

  free(bazz);
  free(buzz);

  return 0;
}
(edited)
General Output:
buzz 0x7ffd5b98c5d8
 r   0x7ffd5b98c5d8
*r   (nil)
 r   0x7ffd5b98c5d8
*r   0x2091690
bazz.foo = 23
bazz.bar = A
buzz.foo = 23
buzz.bar = A
(edited)
Avatar
PDrifting 11-Jun-21 09:27 AM
A little more dissection of the address outputs will hopefully clarify what is actually happening when we are calling function newTFBAlt and passing pointer buzz to it.  Since pointer buzz is merely type TFB and a single pointer, meaning we do not have an array, in the case of TFB *buzz[] and we do not have any pointers to pointers in the case of TFB **buzz, we must satisfy the conversion to the **r argument expected in the call.  The easiest way to do this is to pass the address of buzz.  In this case the address of the pointer buzz is shown to be 0x7ffd5b98c5d8.   When we enter the function the address of **r becomes the address of buzz as shown by the address matching.  When we call the malloc it will request a section of memory that also has an address that we need to store.  That address passed back from the malloc is shown to be 0x2091690.  The reason we need to use (*r) in this case is because **r points to the address of &buzz, and we know when we take *ptr we are looking at the value of what is stored there, giving us access to the pointer being pointed to.  The first pointer is buzz, and it points to the address returned by the malloc.

Here is an example with output showing the side-effects of the above and further explaining why this fails to further reinforce the concept above. (edited)
Avatar
PDrifting 11-Jun-21 01:34 PM
#include <stdlib.h>
#include <stdio.h>
#include <stdint.h>

typedef int8_t s8;
typedef int32_t s32;

typedef struct {
  s32 bar;
  s8 foo;  
} TFB;

void newTFBAlt(TFB *r) {  
  printf("&r %p\n", &r);
  printf(" r %p\n", r);  
  r = (TFB *)malloc(sizeof(TFB));
  printf("&r %p\n", &r);
  printf(" r %p\n", r);
}

s32 main() {
  TFB *buzz = NULL;
  printf("&buzz %p\n", &buzz);
  printf(" buzz %p\n", buzz);
  newTFBAlt(buzz);
  
  printf("buzz.foo = %d\n", buzz->foo);
  printf("buzz.bar = %c\n", buzz->bar);

  free(buzz);

  return 0;
}
(edited)
General Output:
&buzz 0x7ffe55680c10
 buzz (nil)
&r 0x7ffe55680be8
 r (nil)
&r 0x7ffe55680be8
 r 0x9f1670
Avatar
PDrifting 11-Jun-21 02:17 PM
The second example shows how we would normally pass a pointer to a function so we can update its value.  We can see the address of buzz is 0x7ffe55680c10.  Things get janky when we enter the function and realise that the address of the pointer argument *r is 0x7ffe55680be8.  This is because pointers are passed by value, and so a copy of the pointer was made locally and placed on the stack.  Even though we are passing by reference, we are only able to update the value stored at what buzz is pointing to.  In this case we can see the (nil) value stored there, however, it is stored at a different address.  Where buzz and *r exist in memory does not match.  So the address of the pointer can never truly be updated, because we do not actually have the true address of the thing we are trying to assign it to.  This is why we need the second indirection with a pointer to a pointer.  We must be able to preserve the address in the by reference call, not just the value being passed by reference. (edited)
Avatar
PDrifting 11-Jun-21 02:29 PM
The *r creates a pointer to an address of a value.  What we need for preservation of the malloc address is a pointer to an address of a pointer to an address of a value.  That is where the **r comes in.   Because we must pass the address of something as the argument not just what the pointer is pointing to we have changed the conditions of the by reference call.   The second indirection gives us the ability to access address.

If we think about how we normally would deal with a variable, then a pointer, and accessing the value at that pointer. (edited)
int buzz = 0;
int *bar = &buzz;
printf("buzz  %i\n", *bar);
We know buzz has an address on the stack and holds a value of 0.  Assigning the address of buzz to bar allows us to access the value of buzz through a dereference to the value stored at what bar is pointing to by using *bar. (edited)
int buzz = 0;
int *foo = &buzz;
int **bar = &foo;
printf("foo   %i\n", *foo);
printf("buzz  %i\n", **bar);
Double indirection of pointers above is what we are actually requiring.  We need a point that can point to the value it holds.  When we call the function with 
newTFBAlt(&buzz);
 we end up with something like this. (edited)
Avatar
PDrifting 11-Jun-21 02:52 PM
TFB *buzz = NULL;
TFB **r = &buzz;
*r = (TFB *)malloc(sizeof(TFB));
In this case we have built the proper chain for the persistence of the address passed back by the malloc.  When passing things as arguments to functions we need to be mindful of where things are pointing, and what they are pointing to.  This is a perfect example of pointer complexity that creates immense confusion.  Just remember, if you must malloc something inside a function and pass it by reference as an argument, always add one more level of pointer indirection than what the pointer has been declared as.  Make sure you pass the address, and use the proper level of dereferencing. (edited)
Avatar
PDrifting 11-Jun-21 03:04 PM
Image attachment
Avatar
PDrifting 11-Jun-21 03:14 PM
NOTE: The last thing we need to remember, POINTERS ARE ALWAYS PASSED BY VALUE.  You will never be able to update an address of a pointer because of this.  To accomplish this, ADD ONE EXTRA LEVEL OF INDIRECTION SO THE POINTER CAN BE PASSED BY REFERENCE.  When calling the function, PASS THE ADDRESS OF THE POINTER YOU ARE TRYING TO UPDATE.   Then make sure you DEREFERENCE ONE LEVEL OF INDIRECTION TO ACCESS THE ORIGINAL POINTER.  Everything should be okay. (edited)
If you fail to remember this, you will end up seeing a lot of this...
Segmantation fault (core dumped)
Avatar
PDrifting 12-Jun-21 05:39 PM
One last group of examples will cover passing arrays and their special treatment within C.  Arrays are treated as pointers when referred to by their name and always passed by reference.

Basic program with output showing how to pass an array, setup a function call, use sizeof for basic length calculations, and general setup of function main. (edited)
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;
typedef size_t length;

//arrays are pointers that are automatically passed
//by reference which means you can modify them
//without any special syntax    
void foo(c8 bar[], length len) {
  printf("len = %lu\n", len);
  printf("[%s]\n", bar);
  bar[0] = 'h';
  bar[6] = 'w';
}

s32 main() {
  //keep in mind there is a NULL automatically
  //added to end of char/string data declared
  //this way  
  c8 thud[] = "Hello World!";
  
  //there is no length or size of things in C
  //so you need to create little expressions like
  //this to determine those values
  //len will be calculated as 13, 12 + NULL
  length len = sizeof(thud) / sizeof(c8);

  foo(thud, len);
  
  //shows that the array was able to be updated
  //without having to declare the arguments
  //as pointers
  printf("post foo [%s]\n", thud);

  return 0;
}
(edited)
General Output:
len = 13
[Hello World!]
post foo [hello world!]
Avatar
PDrifting 13-Jun-21 02:16 AM
Passing multi-dimensional arrays is little more complicated, you just need to remember that the last dimension needs to match element bounds of the array you will be passing.  Other than that, no fancy pointer stuffs required.  Here's another basic program with output showing how to use strlen, pass a multi-dimensional array to a function, modify a some things in it verifying the by reference state of arrays, and the general setup of function main.
#include <stdio.h>
#include <stdint.h>
#include <string.h> //just for strlen()

typedef char c8;
typedef int32_t s32;
typedef size_t length;

//this shows passing a multi-dimensional array
//as as an argument
//you must declare the number of elements in the last
//dimension of the arrays if it is multi-dimensional
//it will also be treated just like single-dimension
//arrays as a pointer by name and by reference
void foo(c8 bar[][20], length len) {
  printf("len = %lu\n", len);
  //we are using strlen() here to get the length of
  //each of the strings inside the array
  //since they are declared with max 19 characters + NULL [20]
  //we need another way to track the length
  //strlen() returns the length to the first NULL character
  printf("bar[0] len = %2lu [%s]\n",strlen(bar[0]), bar[0]);
  printf("bar[1] len = %2lu [%s]\n",strlen(bar[1]), bar[1]);
  printf("bar[2] len = %2lu [%s]\n",strlen(bar[2]), bar[2]);
  bar[0][0] = 'h';
  bar[0][6] = 'w';
  bar[1][0] = 'f';
  bar[2][0] = 'm';
  bar[2][6] = 'd';
}

s32 main() {
  //keep in mind there is a NULL automatically
  //added to end of char/string data declared
  //this way for each literal
  //when you're dealing with multi-dimensional
  //arrays you do need to specify the number of
  //elements in the last dimension
  c8 thud[][20] = {
    {"Hello World!"},
    {"Foobar"},
    {"Multi-Dimensional"}
  };
  
  //this will give you the total size of thud
  //since there are 3 elements by 20 you should
  //see 60 stored in len
  //the NULL calculations in this case don't matter
  //because we have set a hard size for the char/string
  //buffers despite a NULL being added to the end of
  //each of the string declares
  length len = sizeof(thud) / sizeof(c8);

  foo(thud, len);
  
  //shows that the array was able to be updated
  //without having to declare the arguments
  //as pointers
  puts("\npost foo");
  printf("thud[0] [%s]\n", thud[0]);
  printf("thud[1] [%s]\n", thud[1]);
  printf("thud[2] [%s]\n", thud[2]);
  return 0;
}
(edited)
General Output:
len = 60
bar[0] len = 12 [Hello World!]
bar[1] len =  6 [Foobar]
bar[2] len = 17 [Multi-Dimensional]

post foo
thud[0] [hello world!]
thud[1] [foobar]
thud[2] [multi-dimensional]
Avatar
PDrifting 13-Jun-21 05:17 PM
Basic program with output showing how to pass data between functions, allocate a buffer, introduction to memset, and general setup of function main. (edited)
#include <stdio.h>
#include <stdlib.h> //for malloc()
#include <stdint.h> 
#include <string.h> //for memset()

typedef char c8;
typedef int32_t s32;
typedef size_t length;


//remember we need to declare functions before we use
//them to avoid the need to for janky forward prototypes
//this function for now is just a wrapper to memset()
//which is used to fill a region of memory with a
//character based on a given length
void bar(c8 *toFill, length len, c8 chr) {
  //void *memset(void *str, int c, size_t n)
  //first arg is what we want to fill
  //second is what to fill it with
  //third is the count/length 
  memset(toFill, chr, len);

  //memset and most functions that are part of
  //the C stdlib do not add NULLS so we need
  //to make sure we put one on the end of the
  //memory block since this is going to be
  //treated as a string for output later in
  //the program
  toFill[len + 1] = '\0';
}

c8 *foo(length len, c8 chr) {
  //this will create janky memory fragementation
  //not recommended to do indvidual memory allocations this
  //way, it's merely for example
  //remember the +1 for the null and that malloc() does
  //not initialise memory to 0
  //still have the problem of being unable to check
  //if the malloc succeeded
  //we will be getting to this soon
  c8 *r = (c8 *)malloc(sizeof(c8) + 1);

  //pass the allocated memory, the length, and the char
  //to fill the block of memory with
  bar(r, len, chr);
  
  //return the allocated block of memory
  return r;
}

s32 main() {
  //set a length for our allocated block of memory  
  int len = 12;
  
  //call function foo passing the length and a character
  //then assign the returned pointer value to our declared
  //pointer str
  c8 *str = foo(len, 'a');
    
  printf("len = %d address = %p [%s]\n", len, &str, str);
  
  return 0;
}
(edited)
General Output:
len = 12 address = 0x7fff7842e370 [aaaaaaaaaaaa]
Avatar
PDrifting 13-Jun-21 06:05 PM
So far we have only been dealing with one form of function main.  The following example will be the last one we explore for Function use.  There are times when we need to pass information to a program when it starts.  This is done with command line arguments.  The next basic example has output, and shows how to reconfigure main to accept arguments from the command line. (edited)
Avatar
PDrifting 13-Jun-21 06:20 PM
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;

//most of the time we are not writing programs that
//deal with anything being passed to it
//however, when you write tools or have a need for
//for another reason to pass something this is the
//form of function main you should use in place of
//s32 main() {}
//count is how many arguments were passed from the
//command line
//args[] is a list of strings that represent the
//arguments that were passed
s32 main(s32 count, c8 *args[]) {
  printf("number of arguments received = %i\n", count);
  
  //this assumes we have 2 args passed
  //bad things will happen if you do not pass
  //at least 2
  //arg[0] will always be the name of the program
  //the command line arguments always start at args[1]
  //from here will be the actual arguments passed
  //to the program during execution
  printf("args[0] = [%s]\n", args[0]);
  printf("args[1] = [%s]\n", args[1]);
  printf("args[2] = [%s]\n", args[2]);
  
  return 0;
}
(edited)
Command Line Input: (edited)
./main foo bar
General Output:
number of arguments received = 3
args[0] = [./main]
args[1] = [foo]
args[2] = [bar]
(edited)
Avatar
PDrifting 13-Jun-21 06:30 PM
Now that we have hit some the basic building blocks of coding, in order to move forward there is a need to understand some other basic concepts around Operators and Expression building.  In order to move into branching and flow control these topics need to be addressed first.
Part 7: Operators and Expressions
Avatar
PDrifting 18-Jun-21 11:05 AM
In C, there are several types of Operators to explore.  They fall into groups, such as Mathematical, Unary, Relational, Logical, Bitwise, Assignment, Comma and Conditional.  Each group of Operators are used to create Expressions.  Expressions in C are made up of Variables, Functions and Operators. These are important for various flow and branch control uses in our programs.  Let's begin with exploring what we can do with these and how they will relate to future examples and programs we will be exploring in the book. (edited)
Mathematical Operators
Useful for basic maths operations.
Operator     Description
------------------------------------------------
  +          Adds
  -          Subtracts
  *          Multiplies
  /          Divides
  %          Modulus [Remainder from Division]
Basic program with ouput showing how to use each of the Mathematical Operators, and general setup of function main.
Avatar
PDrifting 18-Jun-21 12:51 PM
#include <stdio.h>
#include <stdint.h>
#include <string.h>

typedef char c8;
typedef int32_t s32;
typedef uint64_t u64;
typedef float f32;

void formatOutput(c8 foo, s32 bar, u64 baz, f32 thud, c8 *operation) {
  printf("%s\n", operation);
  puts("-----------------");
  printf("foo  = %d\n",     foo);
  printf("bar  = %i\n",     bar);
  printf("baz  = %lu\n",    baz);
  printf("thud = %.3f\n\n", thud);  
}

void formatModulus(s32 array[], c8 group) {
  printf("Modulus [group%c]\n", group);
  puts("-----------------------");
  printf(
    "       0 1 2 3 4 5 6\n"
    "result %d %d %d %d %d %d %d\n\n",
    array[0], array[1], array[2], array[3], array[4], array[5], array[6]
  );  
}


s32 main() {
  //addition
  c8  aFoo  = 5 + 9;
  s32 aBar  = 3 + 7;
  u64 aBaz  = 6754 + 8653;
  f32 aThud = 3.4f + 11.123f;

  formatOutput(aFoo, aBar, aBaz, aThud, "Addition");

  //subtraction
  c8  sFoo  = 5 - 9;
  s32 sBar  = 3 - 7;
  u64 sBaz  = 6754 - 8653;
  f32 sThud = 3.4f - 11.123f;

  formatOutput(sFoo, sBar, sBaz, sThud, "Subtraction");

  //multiplication
  c8  mFoo  = 5 * 9;
  s32 mBar  = 3 * 7;
  u64 mBaz  = 6754 * 8653;
  f32 mThud = 3.4f * 11.123f;

  formatOutput(mFoo, mBar, mBaz, mThud, "Multiplication");

  //division
  c8  dFoo  = 45 / 9;
  s32 dBar  = 21 / 7;
  u64 dBaz  = 6000 / 2000;
  f32 dThud = 3.4f / 11.123f;

  formatOutput(dFoo, dBar, dBaz, dThud, "Division");

  //modulus
  s32 groupX[] = {0 % 2, 1 % 2, 2 % 2, 3 % 2, 4 % 2, 5 % 2, 6 % 2};
  s32 groupY[] = {0 % 3, 1 % 3, 2 % 3, 3 % 3, 4 % 3, 5 % 3, 6 % 3};
  s32 groupZ[] = {0 % 4, 1 % 4, 2 % 4, 3 % 4, 4 % 4, 5 % 4, 6 % 4};

  formatModulus(groupX,'X');
  formatModulus(groupY,'Y');
  formatModulus(groupZ,'Z');

  return 0;
}
General Output:
Addition
-----------------
foo  = 14
bar  = 10
baz  = 15407
thud = 14.523

Subtraction
-----------------
foo  = -4
bar  = -4
baz  = 18446744073709549717
thud = -7.723

Multiplication
-----------------
foo  = 45
bar  = 21
baz  = 58442362
thud = 37.818

Division
-----------------
foo  = 5
bar  = 3
baz  = 3
thud = 0.306

Modulus [groupX]
-----------------------
       0 1 2 3 4 5 6
result 0 1 0 1 0 1 0

Modulus [groupY]
-----------------------
       0 1 2 3 4 5 6
result 0 1 2 0 1 2 0

Modulus [groupZ]
-----------------------
       0 1 2 3 4 5 6
result 0 1 2 3 0 1 2
The only Operator that tends to cause confusion is the Modulus Operator [%].  Let's dissect the output from the arrays that we built help in groupX, groupY and groupZ.
s32 groupX[] = {0 % 2, 1 % 2, 2 % 2, 3 % 2, 4 % 2, 5 % 2, 6 % 2};

Modulus [groupX]
-----------------------
       0 1 2 3 4 5 6
result 0 1 0 1 0 1 0
Modulus works by producing the remainder result from a division operation.
Avatar
PDrifting 18-Jun-21 01:04 PM
        R     
0 / 2 = 0
1 / 2 = 1
2 / 2 = 0
3 / 2 = 1
4 / 2 = 0
5 / 2 = 1
6 / 2 = 0
Avatar
PDrifting 18-Jun-21 01:26 PM
This is useful if you need to restrict numbers to a range.  It will create a repeating cycle that has great utility.  We'll see the modulus operator in use when we get to writing some of our Containers, specifically in the Queue example.  One other thing we need to address is the side-effect of the following Expression.  
u64 sBaz  = 6754 - 8653;
 This caused what is known as Roll Over.  Since u64 is declared as _typedef uint64_t u64_, this is an unsigned type.  The value of 8653 is greater than 6754, so when the subtraction operation takes place, C does not complain at all, it just rolls over to 18446744073709551615 which is the unsigned long long maximum value and continues the subtraction beyond 0.  This is why we see a strange value when we look at the result for sBaz.  
baz  = 18446744073709549717
 There are no exceptions, or any warnings of any kind, where other languages would throw something like an out of bounds error.  C does not guarantee errors of this nature.  If you see strange results, you have likely caused Roll Over, some other form of Undefined Behaviour or you caused a segmantation fault and crashed your program.
"The handling of overflow, divide check, and other exceptions in expression evaluation is not defined by the language.  Most existing implementations of C ignore overflow in evaluation of signed integral expressions and assignments, but this behavior is not guaranteed."

K&R (Second Edition) [Page 200]
(edited)
This has not been updated in the C standard for the most part either.  This is compiler dependent.  Below we'll look at some of things you might encounter as side-effects.  Here is a basic program with output showing features of Roll Over, and setup of function main. (edited)
Avatar
PDrifting 18-Jun-21 01:51 PM
#include <stdio.h>
#include <stdint.h>
#include <limits.h>

typedef int32_t s32;
typedef int16_t s16;

s32 main() {
  s16 foo = INT16_MIN;
  s16 bar = INT16_MAX;
  
  printf("%d - 1 = %d\n", foo, (s16)(foo - 1));
  printf("%d + 1 = %d\n", bar, (s16)(bar + 1));

  printf("%d", 3 / 0);

  return 0;
}
(edited)
Compiler Output:
main.c: In function ‘main’:
main.c:16:18: warning: division by zero [-Wdiv-by-zero]
   printf("%d", 3 / 0);
                  ^
General Output:
-32768 - 1 = 32767
32767 + 1 = -32768
Floating point exception (core dumped)
C is going to require you get to know your compiler.  As you can see from the warning, it is complaining about the divide by zero.  Which is Undefined Behaviour so every compiler is going to do something different.  In the case of GCC, it causes a segmentation fault (core dump) in relation to floating point maths.  We can clearly see the Roll Over taking place on the minimum and maximum values.  Here's another basic program with output showing other features of Roll Over, and setup of function main.
#include <stdio.h>
#include <stdint.h>
#include <limits.h>

typedef int32_t s32;
typedef uint16_t u16;

s32 main() {
  u16 foo = 0; //all unsigned types default to 0 as their minimum
  u16 bar = UINT16_MAX;
  
  printf("%u - 1 = %u\n", foo, (u16)(foo - 1));
  printf("%u + 1 = %u\n", bar, (u16)(bar + 1));

  return 0;
}
General Output:
0 - 1 = 65535
65535 + 1 = 0
Avatar
PDrifting 18-Jun-21 02:17 PM
NOTE: If you are encountering oddities, check your maths, range, limits, bounds, operators, casts, and heed warnings from the compiler.  This did not cover Not A Number [NAN], Infinity [INF] and other things that go wrong with Floating Point Types.  You are encouraged to explore with code what your specific compiler is going to do in relation to what you are expecting.  They may not always agree.  If things are still exploding, ask for help. (edited)
Unary Operators
These Operators come in a few different contexts.
Operator  Prefix  Postfix  Description
-------------------------------------------------------------------------------------
  -         Y        N     declares a value as negative
  +         Y        N     pretty much useless in C [effectively never used]
  --        Y        Y     decrement by 1
  ++        Y        Y     increment by 1
  !         Y        N     negation/checks if something equals zero
  &         Y        N     get the address of something
  *         Y        N     get the value stored at a pointer address [dereference]
  sizeof    Y        N     get the size of something
(edited)
Avatar
PDrifting 18-Jun-21 06:45 PM
As always, let's write some code.  We'll gloss over &, *, and sizeof operator, since we already covered those in the Pointer Basics section.  Here is a basic program with output covering the - and + Unary Operators, and setup of function main. (edited)
Avatar
PDrifting 19-Jun-21 11:32 AM
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef uint16_t u16;
typedef int32_t s32;
typedef uint32_t u32;

s32 main() {
  s32 foo = -23;
  //+ unary doesn't convert to plus
  //doesn't really do much at all
  //was adopted in C++ for operator
  //overloading symmetry
  //as mentioned in C it doesn't really
  //do anything until you look at the
  //assembly emitted by the compiler
  printf("(s32)+foo  [%d]\n", (s32)+foo);

  c8 bar = -12;
  printf("bar        [%d]\n", bar);
  printf("+bar       [%d]\n", +bar);
  
  //- unary operator works like it
  //does in standard maths
  //- on a positive will convert it
  //to negative and a - on a negative
  //will convery it to a positive
  printf("-bar       [%d]\n", -bar);
  bar = -bar;
  printf("bar = -bar [%d]\n", bar);

  return 0;
}
General Output:
(s32)+foo  [-23]
bar        [-12]
+bar       [-12]
-bar       [12]
bar = -bar [12]
In conclusion, the +  prefix operator, at least in the context of GCC, is useless.  This may differ based on the compiler you are using.  Next we will look at the decrement and increment operators. (edited)
Avatar
PDrifting 19-Jun-21 12:48 PM
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;
typedef uint32_t u32;

s32 main() {
  s32 foo = 7;
  printf("foo [%d]\n\n", foo);
  //when a variable is isolated from an expression
  //it doesn't matter if the increment or decrement
  //is pre or postfixed
  
  ++foo;
  printf("++foo [%d]\n", foo);
  
  foo = 7;
  foo++;
  printf("foo++ [%d]\n\n", foo);

  foo = 7;
  --foo;
  printf("--foo [%d]\n", foo);
  
  foo = 7;
  foo--;
  printf("foo-- [%d]\n\n", foo);

  //where things begin to get complicated is when
  //the increment or decrement are used in an
  //expression, argument, or other context where
  //time of lookup and effect matter
  foo = 7;
  //this will pre increment the value of foo
  //then use the value so ++foo would become
  //a value of 8 then be used hence we will
  //see 8 for ++foo and after will also report
  //a value of 8 since the value was pre incremented
  printf("++foo [%d]\n", ++foo);
  printf("after [%d]\n\n", foo);

  foo = 7;
  //post increment uses the value of foo first
  //then increments it after we used it
  //we should see 7 then 8
  printf("foo++ [%d]\n", foo++);
  printf("after [%d]\n\n", foo);

  foo = 7;
  //the decrement operator will work the
  //same as increment merely working to
  //decrease the value under the same
  //circumstances instead
  printf("--foo [%d]\n", --foo);
  printf("after [%d]\n\n", foo);

  foo = 7;
  printf("foo-- [%d]\n", foo--);
  printf("after [%d]\n\n", foo);

  return 0;
}
General Output:
foo [7]

++foo [8]
foo++ [8]

--foo [6]
foo-- [6]

++foo [8]
after [8]

foo++ [7]
after [8]

--foo [6]
after [6]

foo-- [7]
after [6]
We do need to address some common problems programmers get into with the increment and decrement operators.  They are famous for creating undefined behaviour and other oddities.  Let's explore a few of them.  Keep in mind in each of these scenarios it will be impossible to predict what the compiler is going to do, or the sequence modern processes may execute it.  The following are guaranteed to produce unpredictable results and should be avoided.  The following examples may produce the results you are expecting, but this is not going to be consistently predictable everywhere. (edited)
Examples of Undefined Behaviour from Increment or Decrement Side-Effects (edited)
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  s32 foo = 42;
  s32 bar = 8;

  printf("%i\n\n", ++foo + bar++ - ++bar);

  return 0;
}
Compiler Output [compiled with -Wall]: (edited)
main.c: In function ‘main’:
main.c:10:31: warning: operation on ‘bar’ may be undefined [-Wsequence-point]
   printf("%i\n\n", ++foo + bar++ - ++bar);
General Output:
41
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  s32 foo = 42;
  foo = ++foo;

  printf("%i\n\n", foo);

  return 0;
}
Compiler Output [compiled with -Wall]:
main.c: In function ‘main’:
main.c:8:7: warning: operation on ‘foo’ may be undefined [-Wsequence-point]
   foo = ++foo;
General Output:
43
Avatar
PDrifting 19-Jun-21 01:30 PM
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  s32 foo[3] = {};
  s32 i = 0;

  foo[i] = ++i;
  foo[i] = ++i;
  foo[i] = ++i;

  printf("foo[0] = %i\n", foo[0]);
  printf("foo[1] = %i\n", foo[1]);
  printf("foo[2] = %i\n", foo[2]);
  
  return 0;
}
(edited)
Compiler Output [compiled with -Wall]:
main.c:10:12: warning: unsequenced modification and access to 'i' [-Wunsequenced]
  foo[i] = ++i;
      ~    ^
main.c:11:12: warning: unsequenced modification and access to 'i' [-Wunsequenced]
  foo[i] = ++i;
      ~    ^
main.c:12:12: warning: unsequenced modification and access to 'i' [-Wunsequenced]
  foo[i] = ++i;
      ~    ^
3 warnings generated.
General Output:
foo[0] = 0
foo[1] = 1
foo[2] = 2
(edited)
Avatar
PDrifting 19-Jun-21 01:55 PM
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

void undefinedBehaviour(s32 foo, s32 bar) {
  printf("%i\n", foo + bar);
}

s32 main() {
  s32 foo = 1;

  //the C standard does not define a mandatory
  //order in which your function arguments will be
  //handed to the function you are calling and
  //does not define the order they will be evaluated
  undefinedBehaviour(foo, ++foo);
  
  return 0;
}
Compiler Output [compiled with -Wall]
main.c: In function ‘main’:
main.c:17:27: warning: operation on ‘foo’ may be undefined [-Wsequence-point]
   undefinedBehaviour(foo, ++foo);
General Output:
4
NOTE: When you introduce a side-effect of this nature, you cause UNDEFINED BEHAVIOUR across your entire program.  The moment you lose the ability to predict what your code will do, and why, you can no longer guarantee stability, or expected results.  This is very bad.  There are other scenarios created with pointers and other things.  We'll explore those when we get to strings.  Do not use or reference something and modify it in the same expression, this will guarantee potential for unwanted side-effects.
Avatar
PDrifting 19-Jun-21 05:34 PM
Now that we have tackled some of the problems and basics of the increment and decrement operator lets go over some examples of the ! operator.
Avatar
PDrifting 19-Jun-21 08:39 PM
Basic program with output showing how the ! operator works, and setup of function main.
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  //this is our first introduction to a
  //logical operator
  //with any logical operator it will
  //be working on a bitwise level and
  //have a truth table

  //input       ouput
  //not 0  ->     0
  //  0    ->     1

  //not 0 literally means any value
  //that does not equal zero
  //the ! operator will make it zero
  s32 bar  = 1;
  s32 baz  = 10;
  s32 thud = 23;
  s32 fuzz = -42;

  printf("bar  %i\n", !bar);
  printf("baz  %i\n", !baz);
  printf("thud %i\n", !thud);
  printf("fuzz %i\n", !fuzz);

  //but if we have a value of 0
  //it will set it to a value of 1
  s32 foo  = 0;  

  printf("foo  %i\n", !foo);
  
  return 0;
}
(edited)
General Output:
bar  0
baz  0
thud 0
fuzz 0
foo  1
We are going to skip over the & and sizeof operators as we've covered them prior and end this group with looking at the unary bitwise operator ~.

Basic program with output showing how the ~ operator works, and general setup of function main.  
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;


void dumpFoo(char where[], c8 foo) {
  printf("%s\n", where);
  printf("foo [%%c]  %c\n", foo);
  printf("foo [%%hhu] %hhu\n\n", foo);
}

s32 main() {  
  c8 foo = '(';
  dumpFoo("Base", foo);
  
  foo = ~foo;  
  dumpFoo("Post 1st ~", foo);
  
  foo = ~foo;
  dumpFoo("Post 2nd ~", foo);
  
  return 0;
}
 General Output: 
Base
foo [%c]  (
foo [%hhu] 40     //bit wise 00101000

Post 1st ~
foo [%c]  �
foo [%hhu] 215    //bit wise 11010111   

Post 2nd ~
foo [%c]  (
foo [%hhu] 40     //bit wise 00101000
 Useful when you want to completely flip the bits of something you're working on.  When you're dealing with a scenario that needs flags, or attributes, or some other things inside an API, you'll find bitwise operators to be very useful. (edited)
Relational Operators
Avatar
PDrifting 20-Jun-21 12:30 AM
Below is a table of each of the operators in this group.  As always, we'll keep it brief, then dive into some code.
Operator   Definition
--------------------------------------
   >       greater than
   <       less than
  >=       greater than or equal to
  <=       less than or equal to
  ==       tests for equality
  !=       tests for inequality
Basic program with output showing how each of the Relational Operators works, a trick on how to use an array and some strings to fetch values based on tests conditions, and setup of function main.
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;

void evaluate(s32 lValue, s32 rValue) {
  //since we haven't learned how to use if
  //statements yet, or ternary if statements
  //we can use a char array of 2 strings
  //buff[0] = "false"
  //buff[1] = "true"
  c8 *buff[] = {"false","true"};
  //displays the relational states of each
  //possible relational operator for values
  //that were passed to the function
  //the true/false is looked up based on the
  //evaluation of each expression
  //for instance if we look at the first one
  //lValue > rValue
  //if lValue is greather than rValue it will
  //return 1 [true] else it will return 0 [false]
  printf("%i >  %i = %s\n", lValue, rValue, buff[lValue > rValue]);
  printf("%i <  %i = %s\n", lValue, rValue, buff[lValue < rValue]);
  printf("%i >= %i = %s\n", lValue, rValue, buff[lValue >= rValue]);
  printf("%i <= %i = %s\n", lValue, rValue, buff[lValue <= rValue]);
  printf("%i == %i = %s\n", lValue, rValue, buff[lValue == rValue]);
  printf("%i != %i = %s\n\n", lValue, rValue, buff[lValue != rValue]);
}

s32 main() {
  //you can modify these calls to function
  //evaluate to figure out how each of the
  //relational operators works based on
  //inputs for lValue and rValue
  evaluate(1,1);
  evaluate(1,2);
  evaluate(2,1);
  evaluate(-10,20);
  evaluate(20,10);
  evaluate(42,16);

  return 0;
}
General Output:
1 >  1 = false
1 <  1 = false
1 >= 1 = true
1 <= 1 = true
1 == 1 = true
1 != 1 = false

1 >  2 = false
1 <  2 = true
1 >= 2 = false
1 <= 2 = true
1 == 2 = false
1 != 2 = true

2 >  1 = true
2 <  1 = false
2 >= 1 = true
2 <= 1 = false
2 == 1 = false
2 != 1 = true

-10 >  20 = false
-10 <  20 = true
-10 >= 20 = false
-10 <= 20 = true
-10 == 20 = false
-10 != 20 = true

20 >  10 = true
20 <  10 = false
20 >= 10 = true
20 <= 10 = false
20 == 10 = false
20 != 10 = true

42 >  16 = true
42 <  16 = false
42 >= 16 = true
42 <= 16 = false
42 == 16 = false
42 != 16 = true
Logical Operators
This is a short group, we have already explored one with the Unary Operator !.  The other two logical operators are as follows.
Operator   Description
  &&       logical and
  ||       logical or
   !       logical not
Basic program with output showing how the Logical Operators function, and general setup of function main.
Avatar
PDrifting 20-Jun-21 12:50 AM
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;

void evaluate(s32 lValue1, s32 rValue1, s32 lValue2, s32 rValue2) {
  c8 *buff[] = {"false","true"};
  
  //when dealing with the && operator
  //both expressions must be true
  //the || operator only requires that
  //one of the expressions is true
  //you can see from the tables generated
  //how this works logically
  printf("%i > %i && %i != %i = %s\n",
    lValue1, rValue1, lValue2, rValue2,
    buff[lValue1 > rValue1 && lValue2 != rValue2]
  );

  printf("%i > %i || %i != %i = %s\n",
    lValue1, rValue1, lValue2, rValue2,
    buff[lValue1 > rValue1 || lValue2 != rValue2]
  );

  printf("%i > %i && %i == %i = %s\n",
    lValue1, rValue1, lValue2, rValue2,
    buff[lValue1 > rValue1 && lValue2 == rValue2]
  );

  printf("%i > %i || %i == %i = %s\n\n",
    lValue1, rValue1, lValue2, rValue2,
    buff[lValue1 > rValue1 || lValue2 == rValue2]
  );
}

s32 main() {
  //you can modify these calls to function
  //evaluate to figure out how each of the
  //relational operators works based on inputs
  //for lValue1, rValue1, lValue2, and rValue2
  evaluate(1,1,3,4);
  evaluate(1,2,5,2);
  evaluate(2,1,2,2);
  evaluate(-10,20,9,2);
  evaluate(20,10,2,2);
  evaluate(42,16,6,6);

  return 0;
}
(edited)
General Output:
1 > 1 && 3 != 4 = false
1 > 1 || 3 != 4 = true
1 > 1 && 3 == 4 = false
1 > 1 || 3 == 4 = false

1 > 2 && 5 != 2 = false
1 > 2 || 5 != 2 = true
1 > 2 && 5 == 2 = false
1 > 2 || 5 == 2 = false

2 > 1 && 2 != 2 = false
2 > 1 || 2 != 2 = true
2 > 1 && 2 == 2 = true
2 > 1 || 2 == 2 = true

-10 > 20 && 9 != 2 = false
-10 > 20 || 9 != 2 = true
-10 > 20 && 9 == 2 = false
-10 > 20 || 9 == 2 = false

20 > 10 && 2 != 2 = false
20 > 10 || 2 != 2 = true
20 > 10 && 2 == 2 = true
20 > 10 || 2 == 2 = true

42 > 16 && 6 != 6 = false
42 > 16 || 6 != 6 = true
42 > 16 && 6 == 6 = true
42 > 16 || 6 == 6 = true
Avatar
PDrifting 20-Jun-21 02:16 PM
As mentioned we're skipping the ! operator and moving on to the next group of operators.
Bitwise Operators
Avatar
PDrifting 20-Jun-21 09:02 PM
C provides six bit manipulation operators and are listed in the table below.  These are most effectively used on Integer Types.  Floating Point Types do not store their data in linear order and are made up of parts.

NOTE: Performing bitwise operations on Float Types without a strong understanding of their parts will cause Undefined Behaviour. (edited)
Operator  Description
--------------------------------------
   &      bitwise and
   |      bitwise or
   ^      bitwise exclusive or (xor)
   <<     bitwise left shift
   >>     bitwuse right shift 
   ~      bitwise not
(edited)
Avatar
PDrifting 21-Jun-21 04:05 AM
Basic program with output showing the use of operators right shift, and, or, xor, and the general setup of function main. (edited)
#include <stdio.h>
#include <stdint.h>

typedef uint8_t u8;
typedef int32_t s32;

void c8ToBits(u8 byte) {
  printf(
    "%hhu%hhu%hhu%hhu%hhu%hhu%hhu%hhu [%hhu]\n",
    //to extract a specific bit we can use an
    //and mask that follows powers of 2
    //once we have the mask applied we
    //need to right shift so that we are
    //left with either a zeroed state or
    //a shifted value with a 1 in the rightmost
    //position
    
    //byte val 0b????????
    //128 mask 0b10000000
    (u8)((byte & 128) >> 7),  //if set 10000000 >> 7 yields 1 or 0 [1 or 0]
    //64  mask 0b01000000
    (u8)((byte & 64) >> 6),   //if set 01000000 >> 6 yields 01 or 000 [1 or 0]
    //32  mask 0b00100000
    (u8)((byte & 32) >> 5),   //if set 00100000 >> 5 yields 001 or 0000 [1 or 0]
    //16  mask 0b00010000
    (u8)((byte & 16) >> 4),   //if set 00010000 >> 4 yields 0001 or 00000 [1 or 0]
    //8   mask 0b00001000
    (u8)((byte & 8) >> 3),    //if set 00001000 >> 3 yields 00001 or 000000 [1 or 0]
    //4   mask 0b00000100
    (u8)((byte & 4) >> 2),    //if set 00000100 >> 2 yields 000001 or 0000000 [1 or 0]
    //2   mask 0b00000010
    (u8)((byte & 2) >> 1),    //if set 00000010 >> 1 yields 0000001 or 00000000 [1 or 0]
    //1   mask 0b00000001
    (u8)(byte & 1),           //if set 00000001 yields 00000001 or 000000000 [1 or 0]
    byte
  );
}

void dumpBitwise(u8 a, u8 b) {  
  printf("a [%3hhu]  - ",a);
  c8ToBits(a);
  printf("b [%3hhu]  - ",b);
  c8ToBits(b);  
  
  //and truth table
  //1 and 1 = 1
  //1 and 0 = 0
  //0 and 1 = 0
  //0 and 0 = 0

  printf("\na and b  - ");
  u8 foo = a & b;  
  c8ToBits(foo);
  
  //or truth table
  //1 or 1 = 1
  //1 or 0 = 1
  //0 or 1 = 1
  //0 or 0 = 0

  printf("a or b   - ");
  foo = a | b;
  c8ToBits(foo);
  
  //xor truth table
  //1 xor 1 = 0
  //1 xor 0 = 1
  //0 xor 1 = 1
  //0 xor 0 = 0

  printf("a xor b  - ");
  foo = a ^ b;
  c8ToBits(foo);

  //not truth table
  //1 = 0
  //0 = 1

  printf("not a    - ");
  foo = ~a;
  c8ToBits(foo);

  printf("not b    - ");
  foo = ~b;
  c8ToBits(foo);  
}

s32 main() {
  dumpBitwise('a',')');
  puts("\n--------------------\n");
  dumpBitwise('1','z');
  puts("\n--------------------\n");
  dumpBitwise(15,240);
  puts("\n--------------------\n");
  dumpBitwise(170,204);

  return 0;
}
(edited)
General Output:
a [ 97]  - 01100001 [97]
b [ 41]  - 00101001 [41]

a and b  - 00100001 [33]
a or b   - 01101001 [105]
a xor b  - 01001000 [72]
not a    - 10011110 [158]
not b    - 11010110 [214]

--------------------

a [ 49]  - 00110001 [49]
b [122]  - 01111010 [122]

a and b  - 00110000 [48]
a or b   - 01111011 [123]
a xor b  - 01001011 [75]
not a    - 11001110 [206]
not b    - 10000101 [133]

--------------------

a [ 15]  - 00001111 [15]
b [240]  - 11110000 [240]

a and b  - 00000000 [0]
a or b   - 11111111 [255]
a xor b  - 11111111 [255]
not a    - 11110000 [240]
not b    - 00001111 [15]

--------------------

a [170]  - 10101010 [170]
b [204]  - 11001100 [204]

a and b  - 10001000 [136]
a or b   - 11101110 [238]
a xor b  - 01100110 [102]
not a    - 01010101 [85]
not b    - 00110011 [51]
Basic program with output showing how the left and right shift operators function, and general setup of function main.
Avatar
PDrifting 21-Jun-21 04:21 AM
#include <stdio.h>
#include <stdint.h>

typedef uint8_t u8;
typedef int32_t s32;

void c8ToBits(u8 byte) {
  printf(
    "%hhu%hhu%hhu%hhu%hhu%hhu%hhu%hhu [%hhu]\n", 
    (u8)((byte & 128) >> 7),    
    (u8)((byte & 64) >> 6),
    (u8)((byte & 32) >> 5),
    (u8)((byte & 16) >> 4),
    (u8)((byte & 8) >> 3),
    (u8)((byte & 4) >> 2),
    (u8)((byte & 2) >> 1),
    (u8)(byte & 1),
    byte
  );
}

s32 main() {
  //right shift does a divide by 2
  //with integer rounding
  puts("Right shift...");
  u8 foo = 0b10000000;
  c8ToBits(foo);
  c8ToBits(foo >> 1);
  c8ToBits(foo >> 2);
  c8ToBits(foo >> 3);
  c8ToBits(foo >> 4);
  c8ToBits(foo >> 5);
  c8ToBits(foo >> 6);
  c8ToBits(foo >> 7);

  puts("\n-----------------\n");
  //left shift does a multiply by 2
  //with integer rounding
  puts("Left shift...");
  u8 bar = 0b00000001;
  c8ToBits(bar);
  c8ToBits(bar << 1);
  c8ToBits(bar << 2);
  c8ToBits(bar << 3);
  c8ToBits(bar << 4);
  c8ToBits(bar << 5);
  c8ToBits(bar << 6);
  c8ToBits(bar << 7);
  

  puts("\n");
  u8 baz = 14 >> 1;  //divide 14 by 2
  c8ToBits(14);
  c8ToBits(baz);
  printf("baz = %hhu\n\n", baz);

  baz = 35 >> 1;     //divide 35 by 2
  c8ToBits(35);
  c8ToBits(baz);  
  printf("baz = %hhu\n\n", baz);

  baz = 14 << 1;     //multiply 14 by 2
  c8ToBits(14);
  c8ToBits(baz);  
  printf("baz = %hhu\n\n", baz);

  baz = 35 << 1;     //multiply 35 by 2
  c8ToBits(35);
  c8ToBits(baz);    
  printf("baz = %hhu\n", baz);

  return 0;
}
(edited)
General Output:
Right shift...
10000000 [128]
01000000 [64]
00100000 [32]
00010000 [16]
00001000 [8]
00000100 [4]
00000010 [2]
00000001 [1]

-----------------

Left shift...
00000001 [1]
00000010 [2]
00000100 [4]
00001000 [8]
00010000 [16]
00100000 [32]
01000000 [64]
10000000 [128]


00001110 [14]
00000111 [7]
baz = 7

00100011 [35]
00010001 [17]
baz = 17

00001110 [14]
00011100 [28]
baz = 28

00100011 [35]
01000110 [70]
baz = 70
Avatar
PDrifting 26-Jun-21 12:18 PM
Assignment Operators
There are a total of 11 operators of this kind available in C.  Now that we have covered the a majority of the basic operators the table below will show how they can be combined with the simple equals Assignment Operator to form Compound Assignment Operators. (edited)
           Operator   Equivalence          Description
--------------------------------------------------------------------------------            
Simple         =      var = value          general assignment
Compound      +=      var = var + value    addition and assignment
              -=      var = var - value    subtraction and assignment
              *=      var = var * value    multiplication and assignment
              /=      var = var / value    division and assignment
              %=      var = var % value    modulus and assignment
             <<=      var = var << value   bitwise shift left and assignment
             >>=      var = var >> value   bitwise shift right and assignment
              &=      var = var & mask     bitwise and with assignment
              |=      var = var | mask     bitwise or with assignment
              ^=      var = var ^ mask     bitwise xor with assignment
(edited)
Avatar
PDrifting 26-Jun-21 12:43 PM
Basic program with output showing the general use of the Assignment Operators, several functions, and as always setup of function main.
Avatar
PDrifting 26-Jun-21 03:16 PM
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  s32 foo = 0;                //general assignment
  printf("foo = %i\n", foo);

  foo += 1;                   //foo = foo + 1;
  printf("foo = %i\n", foo);
  
  foo -= 12;                  //foo = foo - 12;
  printf("foo = %i\n", foo);
  
  foo *= -6;                  //foo = foo * -6;
  printf("foo = %i\n", foo);
  
  foo /= 11;                  //foo = foo / 11;
  printf("foo = %i\n", foo);

  foo %= 5;                   //foo = foo % 5;
  printf("foo = %i\n", foo);

  foo <<= 3;                  //foo = foo << 3;
  printf("foo = %i\n", foo);

  foo >>= 2;                  //foo = foo >> 2;
  printf("foo = %i\n", foo);

  foo &= 0xFF00FF00FF;        //foo = foo & 0xFF00FF00FF;
  printf("foo = %i\n", foo);

  foo |= 0xFF00FF00FF;        //foo = foo | 0xFF00FF00FF;
  printf("foo = %i\n", foo);

  foo ^= 0xFF00FF00FF;        //foo = foo ^ 0xFF00FF00FF;
  printf("foo = %i\n", foo);

  return 0;
}
General Output:
foo = 0
foo = 1
foo = -11
foo = 66
foo = 6
foo = 1
foo = 8
foo = 2
foo = 2
foo = 16711935
foo = 0
Avatar
PDrifting 27-Jun-21 10:56 AM
Comma Operator
Avatar
PDrifting 27-Jun-21 11:24 AM
We are only going to introduce it here.  No code showing its use will follow at this point.  This is technically an Unary Operator, and has very limited places where it can be used.  Its primary use is for sequencing side-effects from other expressions or operations.  Like many other operators in C, it shares multiple purposes generating confusion if context is not understood.  The , operator in this context should not be confused with compound variable declarations, function arguments lists, or structure or union layouts.  Our use of the , operator will be limited in the future to for loops, macros, auxiliary computations of expressions in the same statement, complex returns, and avoiding the need for blocks and associated { block } braces.  Since we have not covered most of the parts of where this operator is used, it will be detailed later in each of the future programming concepts as we go over them.
Conditional Operator
Avatar
PDrifting 27-Jun-21 11:33 AM
Sometimes we need to make assignments based on a decision. This is our introductory branching operator.  It's made up a few parts that must follow a specific order.  It uses an evaluation expression and has two state expressions representing true and false based on the logical result of the expression.  You will also hear the Conditional Operator commonly referred to as a ternary if statement.

Basic program with output showing an example using the ternary if statement, and the general setup of function main. (edited)
Avatar
PDrifting 27-Jun-21 04:18 PM
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

//common form of simple find mininum of two integers
s32 minV1(s32 a, s32 b) {
  //introduction to if which will be the next section
  //but for this example we need to use it for context
  //of what not to do
  //the multiple returns in this code violate modern
  //coding ceoncepts around single entrance - single exit
  //this is spaghetti return statements
  //all functions should only have one return or
  //other method of exiting from it
  
  //checks to see if a is greater than b  
  if (a > b)
    //yes, so return b
    return b;
  else
    //no, so return a
    return a;
}                                  

s32 minV2(s32 a, s32 b) {
  //this is a better form of the above getting rid of the
  //multiple return statements using a variable declared as r
  //in this case we assign the default value of a to r
  int r = a;
  //only if a is greater than be set r = b
  if (a > b) r = b;
  //returns the value of r
  return r;
}

s32 minV3(s32 a, s32 b) {
  //this is what we are actually covering in this example
  //the construction of a ternary if from the above  
  //   if (a > b) ? return b : return a
  //with a ternary if we don't need the if 
  //we just need the expression then the ? operator
  //portion of the conditional
  //the remaining two expressions separated by the colon
  //are the true : false states of the original logical
  //resolution of the expression
  //so if a is greater than b then the return will
  //be equivalent to return b else it will be return a
  return (a > b) ? b : a;
}

//we have not covered the preprocessor yet, but this is
//generally what we would aim for in place of the functions
//above, they are completely unnecessary. we will cover
//the preprocessor after branching and loops.
#define minV4(a, b) (((a) > (b)) ? (b) : (a))

void compareFuncs(int a, int b) {
  printf("minV1(%i,%i) = %i\n", a, b, minV1(a,b));
  printf("minV2(%i,%i) = %i\n", a, b, minV2(a,b));
  printf("minV3(%i,%i) = %i\n", a, b, minV3(a,b));
  printf("minV4(%i,%i) = %i\n", a, b, minV4(a,b));
  puts("");
}

s32 main() {
  compareFuncs(3, 15);
  compareFuncs(-3, -15);
  compareFuncs(45, 23);
  compareFuncs(9, 8);

  return 0;
}
(edited)
General Output:
minV1(3,15) = 3
minV2(3,15) = 3
minV3(3,15) = 3
minV4(3,15) = 3

minV1(-3,-15) = -15
minV2(-3,-15) = -15
minV3(-3,-15) = -15
minV4(-3,-15) = -15

minV1(45,23) = 23
minV2(45,23) = 23
minV3(45,23) = 23
minV4(45,23) = 23

minV1(9,8) = 8
minV2(9,8) = 8
minV3(9,8) = 8
minV4(9,8) = 8
Avatar
PDrifting 27-Jun-21 09:41 PM
Basic program with output showing some other examples of ternary if statements, and general setup of function main.
Avatar
PDrifting 28-Jun-21 02:08 PM
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 findMax(s32 a, s32 b, s32 c) {
  //normally we wouldn't use the /* comment */ format
  //but something with the syntax highlight linter
  //is getting confused by the code below and will
  //not colour code it correctly

  /*
  ternary if statements can be compounded making
  complex linear blocks of code this basically
  implements an if structure that follows like this
  
  if (a > b) {           //(a > b) ?
    if (a > c) {         //(a > c ?
      return a;          //a
    } else {             //:
      return c;          //c
    }                    //)
  } else {               //:
    if (b > c) {         //(b > c ?
      return b;          //b 
    } else {             //:
      return c;          //c
    }                    //)   
  }                      //;
  
  this is generally generally discoraged
  (a > b) ? (a > c ? a : c) : (b > c ? b : c);
  
  a more readable form would be
  */
  s32 t = (a > c) ? a : c;
  s32 f = (b > c) ? b : c;
  return  (a > b) ? t : f;
}

s32 main() {
  s32 foo = 3;
  s32 bar = 12;
  s32 baz = -8;

  printf("%i\n", findMax(foo, bar, baz));

  return 0;
}
(edited)
Avatar
PDrifting 28-Jun-21 02:29 PM
General Output:
12
NOTE: Many online tutorials, books, and manuals may show something along the lines of this as a possible correct usage of ternary if statements.  
#include <stdio.h>

int main() {
  // if (2 > 1) {
  //   printf("if\n");
  // } else {
  //   printf("else\n");
  // }

  2 > 1 ? printf("if\n") : printf("else\n");

  return 0;
}
This is not a good usage.  Basic example with output showing a better form of the above, and general setup of function main.
#include <stdio.h>

int main() {
  // if (2 > 1) {
  //   printf("if\n");
  // } else {
  //   printf("else\n");
  // }

  printf("%s\n", (2 > 1) ? "if" : "else");
  
  return 0;
}
(edited)
General Output:
if
Avatar
PDrifting 28-Jun-21 04:26 PM
And this leads us into the next section beyond operators.
Part 8: Introduction to Branching (edited)
Avatar
PDrifting 28-Jun-21 05:38 PM
In C there are if, else if and else statements that can make up one for of branching.  There is also the switch, case, default statements.  The ternary if operator we just went over, return statements we have been we have been using in every one of our examples to this point, and a few others that are generally discouraged from use.  These include continue, goto, labels and the function exit.  One last but slightly deficient important statement is break.  Limitations of the break statement in some contexts requires we drag the goto statement into use.

As we have already found, there are many cases where an if statement is easily replaced.  But we will start with it, and show alternatives if available. (edited)
Avatar
PDrifting 28-Jun-21 07:15 PM
Basic example with output showing how to create the simplest form of a branching setup for loop control using goto, and a general setup of function main.

NOTE: This is merely for example, and not a general recommendation on how to solve a problem.  It's a prime example of the mess goto statements make.  Early programming languages did not have the syntax to create better models of code structure.  The Assembly Language uses a lower model of this style of label and goto statement, except they are a series of instructional codes based on jmp which is short for jump. (edited)
Avatar
PDrifting 28-Jun-21 07:31 PM
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  s32 foo = 0;
  
  //this is a label
  //they are used for goto statements
  //so they know where to jump to
  //this creates a label called loopHead
  loopHead:
    //prints out the state of foo 
    printf("%i\n", foo++);
    //checks to see if foo > 10
    //if so, goto afterLoop to escape it
    if (foo > 10) goto afterLoop;
  //this creates the loop
  //if we don't goto afterLoop this
  //will goto loopHead doing another iteration
  //of a loop
  goto loopHead;

  //escape label so we have somewhere to
  //goto and escape the loop
  afterLoop:
  return 0;
}
General Output:
0
1
2
3
4
5
6
7
8
9
10
Avatar
PDrifting 28-Jun-21 07:47 PM
Now that we know what not to do with a basic introduction to the goto and labels, we'll move on to more basic examples of using if, else if, and else, and general setup of function main. (edited)
Avatar
PDrifting 28-Jun-21 08:01 PM
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;

s32 main(s32 count, c8 *args[]) {
  //if does not require block braces { }
  //if each if, else if, or else only contains
  //a single statement of code
  //comments do not count against the single statement
  if (count > 1 && count < 4)
    //if count is greater than 1 and count is less than 4 is true
    printf("count = %d\n", count);
  else if (count >= 4) 
    //if count is greater than or equal to 4 is true
    puts("Too many arguments passed from the command line.");
  else
    //else neither of the above conditions were met
    //so we trigger this
    puts("Not enough arguments passed from the command line.");
  
  return 0;
}
(edited)
Command Line Input:
./main
General Output:
Not enough arguments passed from the command line.

Command Line Input:
./main foo
General Output:
count = 2

Command Line Input:
./main foo bar
General Output:
count = 3

Command Line Input:
./main foo bar baz
General Output:
Too many arguments passed from the command line.
(edited)
Avatar
PDrifting 28-Jun-21 09:23 PM
Basic example with output showing how to setup another basic if, else if block of statements and condition where thinking about initialisation of a declare can take the place of an else, also general setup of function main.
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef unsigned char u8;
typedef int32_t s32;

c8 getLetter(u8 grade) {
  //this takes the place of the general else
  //if we default the initialisation assignment
  //to 'F' we can save a statement and assignment
  //if we had done and initial declare as
  //c8 r = 0; then we need to have an
  //else r = 'F' at the end of the if statement
  //blocks, so in this case we just assign it
  //this way so we don't need it
  c8 r = 'F';
  
  //test if grade passed is greater than or equal to 80
  if (grade >= 80) r = 'A';       //yes so set the grade to 'A'
  //else test if grade passed is greater than or equal to 70
  else if (grade >= 70) r = 'B';  //yes so set the grade to 'B'
  //else test if grade passed is greater than or equal to 60
  else if (grade >= 60) r = 'C';  //yes so set the grade to 'C'
  //else test if grade passed is greater than or equal to 50
  else if (grade >= 50) r = 'D';  //yes so set the grade to 'D'

  return r;
}

s32 main() {
  printf("%c\n", getLetter(90));
  printf("%c\n", getLetter(45));
  printf("%c\n", getLetter(52));
  printf("%c\n", getLetter(79));
  printf("%c\n", getLetter(66));

  return 0;
}
General Output:
A
F
D
B
C
Basic example showing how to test for the failure of a malloc call, and general setup of function main.
Avatar
PDrifting 28-Jun-21 10:03 PM
#include <stdlib.h>
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

//remember when we need to allocate memory to a pointer
//and pass it through as an argument we must remember
//to use a pointer to a pointer **
s32 getMemory(void **toAllocate, s32 mbs) {
  //set r = 1 to default the return state to
  //a success state
  s32 r = 1;
  
  //and make sure we use the single dereference to
  //the pointer we are trying to allocate an address to
  *toAllocate = malloc(1000000 * mbs);
  
  //this tests to see if the malloc failed
  //if malloc fails it will return 0 [NULL]
  //so in this case we are testing if *toAllocate
  //is equal to 0 by using the ! operator
  //if not *toAllocate then set r = 0
  //this is our failed return state
  if (!(*toAllocate)) r = 0;   
    
  return r;
}

s32 main() {
  void *ptr = NULL;
  
  //run several tests to see how much RAM can be allocated
  //on the system...

  //checks to if the return state from the call to getMemory
  //is anything but 0
  //we do not need to use the block {} braces in part of the
  //if statements because there is more than one statement
  //contained within part of one of the logical states
  if (getMemory(&ptr, 1)) {
    //it succeeded so show a success message
    puts("Got 1 MB of memory successfully.");
    
    //free the memory we requested to send it back
    //to the memory pool
    free(ptr);    
  //the call to getMemory failed so trigger the else
  } else puts("Failed to get 1 MB of memory.");

  //these are just repeats of the above and could be
  //coded into a function, however these are left as
  //is to reinforce a concept of sequential if chains
  if (getMemory(&ptr, 500)) {
    puts("Got 500 MB of memory successfully.");
    free(ptr);
  } else puts("Failed to get 500 MB of memory.");

  if (getMemory(&ptr, 1000)) {
    puts("Got 1 GB of memory successfully.");
    free(ptr);
  } else puts("Failed to get 1 GB of memory.");

  if (getMemory(&ptr, 10000)) {
    puts("Got 1 TB of memory successfully.");
    free(ptr);
  } else puts("Failed to get 1 TB of memory.");

  if (getMemory(&ptr, 100000)) {
    puts("Got 10 TB of memory successfully.");
    free(ptr);
  } else puts("Failed to get 10 TB of memory.");

  if (getMemory(&ptr, 1000000)) {
    puts("Got 100 TB of memory successfully.");
    free(ptr);
  } else puts("Failed to get 100 TB of memory.");

  return 0;
}
(edited)
General Output:
Got 1 MB of memory successfully.
Got 500 MB of memory successfully.
Got 1 GB of memory successfully.
Got 1 TB of memory successfully.
Got 10 TB of memory successfully.
Failed to get 100 TB of memory.
Avatar
PDrifting 28-Jun-21 10:16 PM
We don't know actually how much memory we could allocate on this given system, but it's somewhere between 10 terabytes and less than 100 terabytes of RAM.  This is pretty considerable.  The typical modern desktop computer maxes out as of the writing of this manual between 8 GB and 16 GB according to the latest Steam Hardware Survey [May 2021].  When the code above was run it was executed on a cloud based server which has considerably more memory than a computer you may have access to.

NOTE: Remember that the Operating System, Drivers, Services, and other Software that may be running on the system will be consuming memory.  Just because your machine may have 8 GB of RAM, you may at any given point in time only have access to about 4 GB of RAM that are not in use.  RAM is not unlimited like many courses teach, and should be treated as a finite resource and managed accordingly. (edited)
Avatar
PDrifting 29-Jun-21 10:44 AM
Basic program with output showing how to read and parse simple arguments from the command line, nest if statements, format complex expressions for readability, and general setup of function main. (edited)
Avatar
PDrifting 29-Jun-21 11:43 AM
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;

void showHelp(c8 *name) {
  //remember when dealing with complex printf statements
  //you can order individual strings in this manner so you
  //plan your output
  printf(
    "\n"
    "Please supply a single character from the command line.\n"    
    "Example:\n"
    "  ./%s [a..z]|[A..Z]|[0..9]\n"
    "\n"
    "Or a number followed by an operator and another number\n"
    "  Single digit numbers only.\n"
    "  Operators [a]dd, [s]ubtract, [m]ultiply, [d]ivide are known.\n"
    "\n"
    "Example:\n"
    "  ./%s 5 a 9\n"
    "\n",
    name, name
  );
}

void malformedHelp(c8 *name) {
  puts("\nMalformed command line arguments...");
  showHelp(name);
}

void divideByZero(c8 *name) {
  puts("\nUndefined Behaviour - Cannot divide by zero...");
  showHelp(name);
}

s32 main(s32 count, c8 *args[]) {  
  //this is a common form of if, else if, else
  //layout and generally acceptable
  //however, we will be covering switch, case, default
  //next as alternative cleaner version of this mess

  //show help
  if (count == 1) showHelp(args[0]);    
  
  //process single char
  else if (count == 2) {
    //in order to grab a character from inside the
    //string array of arguments from the command line
    //we can index args[1] <- the string based on location
    //             args[1][0] <- the 1st char in that string
    c8 c = args[1][0];
    
    if      (c >= 'a' && c <= 'z')  puts("Lower case letter.");
    else if (c >= 'A' && c <= 'Z')  puts("Upper case letter.");
    else if (c >= '0' && c <= '9')  puts("Number");
    else puts("Unrecognised");
  
  //process simple expression
  } else if (count == 4) {
    c8 left  = args[1][0];
    c8 op    = args[2][0];    
    c8 right = args[3][0];
        
    //left should be a number
    //right should be a number
    //op should be either a, s, m or d
    if ((left  >= '0' && left  <= '9') &&
        (right >= '0' && right <= '9') &&  
        (op == 'a' || op == 's' || op == 'm' || op == 'd'))

      //this is a trick to quickly convert an number
      //stored as '0' through '9' to an number
      //just subtract 48 from the char value
      //since char 0 on the ascii table has a value
      //of 48, 1 has a value of 49, 2 has a value of
      //50 etc, by subtracting 48 from it you get
      //a actual value of the digit
      left  -= 48;
      right -= 48;

      //perform each of the maths operations based
      //one what they supplied on the command line      
      if      (op == 'a') printf("%d\n", left + right);
      else if (op == 's') printf("%d\n", left - right);
      else if (op == 'm') printf("%d\n", left * right);
      else if (op == 'd') {
        //check to make sure do not have a divide by zero
        //test if right is not zero else dump an error
        if (right)        printf("%d\n", left / right);
        else divideByZero(args[0]);
      }
    //trigger malformed help
    else malformedHelp(args[0]);
      
  //trigger malformed help
  } else malformedHelp(args[0]);
  
  return 0;
}
(edited)
Avatar
PDrifting 29-Jun-21 11:58 AM
Command Line Input: 
./main
General Output:
Please supply a single character from the command line.
Example:
  ././main [a..z]|[A..Z]|[0..9]

Or a number followed by an operator and another number
  Single digit numbers only.
  Operators [a]dd, [s]ubtract, [m]ultiply, [d]ivide are known.

Example:
  ././main 5 a 9

Command Line Input:
./main a
General Output:
Lower case letter.

Command Line Input:
./main Z
General Output:
Upper case letter.

Command Line Input:
./main 7
General Output:
Number

Command Line Input:
./main {
General Output:
Unrecognised

Command Line Input:
./main foo bar this
General Output:
Malformed command line arguments...

Please supply a single character from the command line.
Example:
  ././main [a..z]|[A..Z]|[0..9]

Or a number followed by an operator and another number
  Single digit numbers only.
  Operators [a]dd, [s]ubtract, [m]ultiply, [d]ivide are known.

Example:
  ././main 5 a 9

Command Line Input:
./main 5 a 9
General Output:
14

Command Line Input:
./main 5 d 0
General Output:
Undefined Behaviour - Cannot divide by zero...

Please supply a single character from the command line.
Example:
  ././main [a..z]|[A..Z]|[0..9]

Or a number followed by an operator and another number
  Single digit numbers only.
  Operators [a]dd, [s]ubtract, [m]ultiply, [d]ivide are known.

Example:
  ././main 5 a 9

Command Line Input:
./main 5 p 2
General Output:
Malformed command line arguments...

Please supply a single character from the command line.
Example:
  ././main [a..z]|[A..Z]|[0..9]

Or a number followed by an operator and another number
  Single digit numbers only.
  Operators [a]dd, [s]ubtract, [m]ultiply, [d]ivide are known.

Example:
  ././main 5 a 9
(edited)
Avatar
PDrifting 29-Jun-21 12:17 PM
Introduction to Switch, Case, Default and Break
There's a few things we need go over in the basics, but otherwise, switch statements are a much cleaner mechanism than if statements generally.  Once you learn to use ternary if statements and switch statements, you won't be using if statements that much.

Basic example with output showing the basic setup of a switch statement, function pointer review, and general setup of function main. (edited)
Avatar
PDrifting 29-Jun-21 02:50 PM
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;

//NOTE: janky old school comments because discord be broke

/*
special typedef for a function pointer type to handle
each of the calls inside the caller function and
satisfy a format for the function we can accept

void callSwitchFunc(c8 *name, switchDelegate func)

this will let us pass individual functions and invoke
them reusing the the output capabilities of that function
*/
typedef s32 (*switchDelegate)(s32);

//NOTE: none of the following examples of switch statements
//should be considered good form

s32 standardSwitch(s32 foo) {
  s32 r = 0;
  
/*
  as mentioned above the code here would be a better
  solution to the following and you could do something
  like this for each of these other examples also
  but as mentioned the idea is just to show form and
  layout of each basic switch state
  
  s32 val[] = {-1,2,3,6,1,4,5};  
  return val[(foo < 1 || foo > 6) ? : 0 : foo];

  the basic standard switch statement starts off with
  switch (expression)
  switch statements must contain their case and default
  options inside a brace block {}  
  each option of a switch statement is denoted by
  case value:
  followed by C statements of code and must end each
  case option with a break statement to prevent a
  side-effect called waterfalling
  if you are familiar with other programming languages
  most will treat each case statement independently
  exiting the switch statement without processing any
  other case options
  this is not the case with C and you must be mindful
  of your break statements
  the method of catching your else conditions in switch
  is by using the default option
  it should be your last case option in the switch block
*/
  switch (foo) {
    case 1: r = 2; break;
    case 2: r = 3; break;
    case 3: r = 6; break;
    case 4: r = 1; break;
    case 5: r = 4; break;
    case 6: r = 5; break;
    default: r = -1;
  }

  return r;
}

s32 waterfallSwitch(s32 foo) {
  s32 r = 0;
    
  switch (foo) {
    //if a case statement does not invoke a break
    //it will carry onto the next case automatically
    //until it hits a break somewhere
    //this can be advantageous if you want a series
    //of case options to perform the same option
    case 1: 
    case 2:
    case 3:
    case 4:
    case 5:
    case 6: r = 1; break;
    default: r = -1; break;
  }

  return r;
}

s32 rangeSwitch(s32 foo) {
  s32 r = 0;
  
  //NOTE: not part of the C standard - compiler specific

  //a more straightforward equivalent of the above
  //removes the reliance on recognising intentional
  //waterfalling behaviour and clearly defines a
  //range for the case using the special ... [range]
  //modifier for the case statement
  switch (foo) {
    case 1 ... 6 : r = 1; break;
    default: r = -1; break;
  }

  return r;
}

//takes a name to build the function name string
//and a function that follows the form of our function
//delegate type we created above
void callSwitchFunc(c8 *name, switchDelegate func) {
  puts("\n");
  printf("%sSwitch(0) = %d\n", name, func(0));
  printf("%sSwitch(1) = %d\n", name, func(1));
  printf("%sSwitch(2) = %d\n", name, func(2));
  printf("%sSwitch(3) = %d\n", name, func(3));
  printf("%sSwitch(4) = %d\n", name, func(4));
  printf("%sSwitch(5) = %d\n", name, func(5));
  printf("%sSwitch(6) = %d\n", name, func(6));
  printf("%sSwitch(7) = %d\n", name, func(7));
}

s32 main() {
  //passes each of the names for the string construction
  //and individual functions to reuse the functional features
  callSwitchFunc("standard", &standardSwitch);
  callSwitchFunc("waterfall", &waterfallSwitch);
  callSwitchFunc("range", &rangeSwitch);

  return 0;
}
(edited)
Avatar
PDrifting 29-Jun-21 05:00 PM
General Output:
standardSwitch(0) = -1
standardSwitch(1) = 2
standardSwitch(2) = 3
standardSwitch(3) = 6
standardSwitch(4) = 1
standardSwitch(5) = 4
standardSwitch(6) = 5
standardSwitch(7) = -1


waterfallSwitch(0) = -1
waterfallSwitch(1) = 1
waterfallSwitch(2) = 1
waterfallSwitch(3) = 1
waterfallSwitch(4) = 1
waterfallSwitch(5) = 1
waterfallSwitch(6) = 1
waterfallSwitch(7) = -1


rangeSwitch(0) = -1
rangeSwitch(1) = 1
rangeSwitch(2) = 1
rangeSwitch(3) = 1
rangeSwitch(4) = 1
rangeSwitch(5) = 1
rangeSwitch(6) = 1
rangeSwitch(7) = -1
Let's quickly cover the things you can't do with case options. (edited)
Avatar
PDrifting 29-Jun-21 05:11 PM
case "string":       //strings comparisons are not valid in this context

s32 var = 2; 
case var:            //values attached to a case statement must be constant

s32 arr[] = { ... };
case arr[0]:         //again values must be constant

case >2              //you cannot use any logical operators

case 1.1f:           //floating point types are not allowed, integer type only

case 1: int x = 2;   //declares within scope cannot be declared like this
                     //they must be encapsulated in braces [see below]

case 2:              //all values within the switch block must have unique
case 2:              //case options or undefined behaviour will result
(edited)
Things you can do with case options. (edited)
Avatar
PDrifting 29-Jun-21 05:23 PM
case 'a':              //char literals

case 'a' ... 'z':      //ranges with char literals

case 1:                //integer values

case 1000 ... 2000:    //ranges with integer values

#define var 2          //[NOTE: pre-exposure to preprocessor syntax]
case var:              //use a defined value 

case 1: {              //declares inside a case statement encapsulated in braces
  int x = 2;
  ...
}

case 1:                //multi-line case blocks without braces as long as
  ...                  //declares do not occur within the syntax statements
  ...
  ...

case 'c': case 'C':    //pack waterfalling case statements on the same line

#define var 2          //[NOTE: pre-exposure to preprocessor syntax]
case var:              //as long as the values involved in the expression are
case var+1:            //constants you can use mathematical operator based
case var*2:            //expressions

case 1 << 2:           //bitwise operators can also be used to make expressions
case 0xf & 20:         //as long as the values used in those expressions
case 0xfe >> 1:        //are constant

case 1 << 2 + 4:       //you are able to create complex expressions also
(edited)
Avatar
PDrifting 29-Jun-21 08:05 PM
We're going to revisit some code we just wrote going over if, else if and else statements to show swtich statements can clean up code.

Basic sample program excluding output, as it would replicate the output from the prior example, showing how to refactor using switch statements, and general setup of function main.

```C
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;

void showHelp(c8 *name) {
  printf(    
    "\n"
    "Please supply a single character from the command line.\n"    
    "Example:\n"
    "  ./%s [a..z]|[A..Z]|[0..9]\n"
    "\n"
    "Or a number followed by an operator and another number\n"
    "  Single digit numbers only.\n"
    "  Operators [a]dd, [s]ubtract, [m]ultiply, [d]ivide are known.\n"
    "\n"
    "Example:\n"
    "  ./%s 5 a 9\n"
    "\n",
    name, name
  );
}

void malformed(c8 *name) {
  puts("\nMalformed command line arguments...");
  showHelp(name);
}

void divideByZero(c8 *name) {
  puts("\nUndefined Behaviour - Cannot divide by zero...");
  showHelp(name);
}

//should macro this, but we haven't covered the preprocessor yet...
s32 isDigit(c8 toCheck) { return (toCheck >= '0' && toCheck <= '9'); }

void processSingleChar(c8 what) {
  switch (what) {
    case 'a' ... 'z': puts("Lower case letter."); break;
    case 'A' ... 'Z': puts("Upper case letter."); break;
    case '0' ... '9': puts("Number");             break;
    default:          puts("Unrecognised");       break;
  } 
}

void processExpression(c8 *args[]) {
  c8 left  = args[1][0];
  c8 op    = args[2][0];    
  c8 right = args[3][0];

  if (isDigit(left) && isDigit(right)) {
    left  -= 48;
    right -= 48;

    switch (op) {
      case 'a': printf("%d\n", left + right); break;
      case 's': printf("%d\n", left - right); break;
      case 'm': printf("%d\n", left * right); break;
      case 'd': 
        if (right) printf("%d\n", left / right);
        else divideByZero(args[0]);
        break;
      default: malformed(args[0]); break;
    }
  } 
}

s32 main(s32 count, c8 *args[]) {    
  switch (count) {    
    case 1:  showHelp(args[0]);             break;    
    case 2:  processSingleChar(args[1][0]); break;
    case 4:  processExpression(args);       break;
    default: malformed(args[0]);            break;
  }
    
  return 0;
}```

General Output for this example above is identical to the prior version of the code.
Most of the basic branching methods have been explained to this point.  We are not going to cover continue, or exit, as these are considered violations of either spaghetti code or single-entrance single-exit.

# Part 9: For, Do, and While Loops

In order to save typing, handle deeper states of flow and control over our code we need loops.  We encountered our first janky loop using goto and label.  The loops we will be covering in this section will effectively accomplish the same thing, just with cleanliness and features that cannot be provided with primitive spaghetti code.  There are many reasons to repeat sections of your code.  As we progress beyond this section, loops will be an important part of your continued programming journey.  The for loop will be the first one we will be covering.

Basic program with output showing how to setup and use basic for loops, and general setup of function main. (edited)

```C
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;
typedef float f32;

s32 main() {
  //for loops have 3 parts separated by a semi-colon
  //initialisation                c8 c = 'a'
  //exit expression logic         c <= 'z'
  //modification of variables     ++c

  //variables initialised in this way will be scoped
  //to the context of the for loop block and will not
  //exist beyond it

  //displays the letters from a ... z

  for (c8 c = 'a'; c <= 'z'; ++c) putchar(c);
  puts("\n");

  //initialisation                s32 i = 1
  //exit expression logic         i < 11
  //modification of variables     ++i

  //like if statements and other blocks in C
  //if there is only one statement associated with
  //it, you do not need block braces {}

  //counts from 01 to 10

  for (s32 i = 1; i < 11; ++i) printf("%02i ", i);
  puts("\n");

  //initialisation                s32 i = 1
  //exit expression logic         f < 1.0f
  //modification of variables     f += 0.2f

  //the variable modification section is effectively
  //stepping calculations that control the direction
  //the loop will resolve

  //counts from 0.00f to 0.80f
  
  for (f32 f = 0.0f; f < 1.0f; f += 0.2f) printf("%1.2f ", f);
  puts("");

  return 0;
}```

> General Output:

```abcdefghijklmnopqrstuvwxyz

01 02 03 04 05 06 07 08 09 10 

0.00 0.20 0.40 0.60 0.80```

Basic program with output showing forward and backward counting examples using a for loop, and general setup of function main.

```C
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  s32 foo = 3;
  s32 bar = -1;

  //for loops do not actually require all 3 parts to be
  //present in its declaration
  //in this case we have initialised foo outside
  //the for loop declaration, but since the for
  //loop is in the same block of code it's able
  //to modifiy and use the variable

  //initialisation                implied from s32 foo = 3;
  //exit expression logic         foo >= bar
  //modification of variables     --foo

  //this outputs numbers from 3 down to -1
  for (; foo >= bar; --foo) printf("%i ", foo);

  //one reason you may do a declaration like this,
  //is if you need to use foo for some other reason
  //after the for loop has run
  //the changes to foo will persist outside the for
  //loop because it was declared outside that local
  //declaration within the for loop

  foo += 4 * bar;
  printf("%i ", foo);

  //this resues the foo variable and we set it to a new
  //value and declare another for loop around it
  //you cannot reuse variables in this way if they are
  //declared inside the initialisation portion of the for
  //as in this reminder example

  //for (int foo = 5;;) 

  //initialisation                --foo
  //exit expression logic         foo >= bar
  //modification of variables     --foo

  //outputs from -7 down to -11
  for (--foo; foo > -12; --foo) printf("%i ", foo);
  
  return 0;
}```

> General Output:

```3 2 1 0 -1 -6 -7 -8 -9 -10 -11```

Basic program with output showing how to use nested for loops, general implementation of the Bubble Sort algorithm, some functions, tying ideas together, and the general setup of function main.

```C
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;
typedef size_t length;

//this is the slowest most cumbersome sort out there
//however, it's easy enough to implement
void bubbleSort(s32 arr[], length n, c8 sortOrder) {  
  //we have nested two for loops to implement the bubble sort
  
  //initialisation                s32 i = 0
  //exit expression logic         i < n
  //modification of variables     ++i
  
  //this iterates through each element in the array
  for (s32 i = 0; i < n; ++i) {
    //in order to nest a for loop simply indent like usual
    //make sure you have your blocking in order and carry on  
 
    //initialisation                s32 j = 0;
    //                              implies s32 jLimit = n - 1
    //                              implies s32 *a
    //                              implies s32 *b
    //exit expression logic         j < jLimit
    //modification of variables     ++j
  
    //this uses the for loop to initialise several variables that will
    //exist only within the persistence of the loop
    //this might look complicated, but it's only because we are using
    //the initialisation section to decalre so many variables
    for (s32 j = 0, jLimit = n - 1, *a, *b; j < jLimit; ++j) {  
      a = &arr[j];
      b = &arr[j + 1];            
      
      //figure out which direction we are going to sort
      //defaulting to ascending order if anything other than
      //'d' or 'D' is passwed with sortOrder
      switch (sortOrder) {        
        //the swap used by both sort orders is a bit twiddle hack
        //using xor assignment in this way avoids needing a temporay
        //variable for storage, though this only works with integral
        //data types
        case 'd':
        //if value at pointer a is less than the value at pointer b        
        //swap using the bit twiddle hack with xor        
        case 'D': if (*a < *b) *a ^= *b, *b ^= *a, *a ^= *b; break;
        //if value at pointer a is greater than the value at pointer b
        //swap using the bit twiddle hack with xor
        default : if (*a > *b) *a ^= *b, *b ^= *a, *a ^= *b; break;
      }      
    }
  }
}
 
void printArray(s32 arr[], length n) {
  puts("\nordered array:");

  //initialisation                s32 i = 0
  //exit expression logic         i < n
  //modification of variables     ++i

  //dumps out the contents of the array  
  for (s32 i = 0; i < n; ++i)
    printf("%02d ", arr[i]);
  
  puts("\n");
}
 
s32 main() {
  //generated an unordered list of numbers
  s32 numbers[] = {46, 63, 92, 27, 11, 21, 10};
  //calulate the number of elements in the array
  length n = sizeof(numbers)/sizeof(numbers[0]);
  
  //test the sorter
  puts("Ascending");
  bubbleSort(numbers, n, 'a');
  printArray(numbers, n);
  
  puts("Descending");
  bubbleSort(numbers, n, 'd');  
  printArray(numbers, n);
  
  return 0;
}```

> General Output:

```Ascending

ordered array:
10 11 21 27 46 63 92 

Descending

ordered array:
92 63 46 27 21 11 10```

Basic program with output showing the difference between do and while loops, and general setup of function main.

```C
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {  
  //these are equivalient loops
  //for now it doesn't really matter which is used
  //in this context, however, there are cases
  //where do is preferable over while
  //when example code is detailed in later examples
  //there will be plenty of cases where a while
  //is used traditionally, but a do should have been
  //used for clarity
  
  //the only real difference between do and while loops
  //is that do waits one cycle before executing the exit
  //expression test
  //this can cause side-effects so be mindful of why
  //you are using one over the other
  
  s32 i = 0;
  do {
    printf("%d ", i++);
  } while (i < 10);

  puts("");

  i = 0;
  while (i < 10) {
    printf("%d ", i++);
  }

  return 0;
}```

> General Output:

```0 1 2 3 4 5 6 7 8 9 
0 1 2 3 4 5 6 7 8 9```

A major problem exists with nested loops in C, caused by limitations with the break statement.  It is only capable of escaping one nested layer at a time.  Unfortunately with C there is no other way to escape multiple nested loops, unless the exit conditions are met for each of them, or a goto statement is used.  This can, and will create some spaghetti in your code.

```C
for (...) {
  for (...) {
    if (outlying condition) goto label;
  }
}

label:```

NOTE: The same problem exists for any nested code that relies on the break statement.  It is very rare that you will need to use this special case, but it is presented, for example of what to do when you have no other choice.

# Part 10: The C Preprocessor

There are plenty of ways you can abuse the C language when writing code.  The Preprocessor is by far the most abused and abusive feature of the language.  When referring to the Preprocessor, we have been using at least one directive in our programs so far called #include.  All Preprocessor directives are preceded by the # symbol.  GCC executes all Preprocessor directives before any processing of your program syntax.  The most useful process we can derive from the Preprocessor is Meta-Programming.  We can literally use the Preprocessor to write C syntax in our code, manage constants, and even determine system architecture we might be running on.  This is useful if we plan on writing cross-platform code beyond the basic C syntax we have covered so far.  Libraries we can #include are determined by the Operating System and the Architecture we are compiling against.

//TODO: NEED TO TABLE THIS
Preprocessor Directives in GCC
#include                 //includes a library in your code
#define                  //defines a named macro
#undef                   //destroys a macro by name
#ifdef  or #if defined   //these are equivalent... checks if a macro is defined
#ifndef or #if !defined  //these are equivalent... checks if a macro is not defined
#elif                    //works just like a regular else if
#else                    //works just like the else in a regular if
#endif                   //ends an #if directive
#pragma                  //allows you to provide additional information to the compiler

There are some other handy features of the Preprocessor when it comes to GCC as it has some things predefined to make things a little easier for you.

//TODO: need to table this
Predefined Macros in GCC
__FILE__             //expands the full path of the current input file as string constant
__FILENAME__         //expands the current input file name only as a string constant
__BASE_FILE__        //expands the main input file supplied on the command line as a string constant
__INCLUDE_LEVEL__    //expands to an integer constant representing how nested we are inside #includes
__LINE__             //expands the current input file line number as an integer constant
__DATE__             //expands todays date in expanded form as a string constant
__TIME__             //expands the current time stamp as a string constant
__TIMESTAMP__        //expands a string constant that described the current time and date
__cplusplus__        //being compiled with C++
__OBJC__             //being compiled with Objective C
__ASSEMBLER__        //the preprocessor in processing ASSEMBLY
__GFORTRAN__         //being compiled with Fortran
__GNUC__             //being compiled with the GNU C Compiler
__MINGW32__          //32-bit Mingw under Windows
__MINGW64__          //64-bit Mingw under Windows
__GNUC_MINOR__       //gets the compiler minor version number as an integer constant
__GNUC_PATCHLEVEL__  //gets the compiler patchlevel version number as an integer constant
__NEXT_RUNTIME__     //being compiled with Objective C using the NeXT runtime
__STD_HOSTED__       //the C standard library is available
__STDC_VERSION__     //generates the C Standard Version Number as a long integer constant
__STDC__             //will equal 1 if the compiler follows the ISO Standard of C
__STRICT_ANSI__      //will be defined if following the strict ANSI C Standard
__VERSION__          //expands to a string constant giving at least the release number
__ELF__              //good indicator we are on Linux or targeting ELF object formats
__COUNTER__          //equals an integer value of 0 which increments after use
__SANTIZE_ADDRESS__  //array bound checking and catching pointer use after free bugs
__SANITIZE_THREAD__  //looking for multi-threading race conditions
__BYTE_ORDER__       //set to either __ORDER_LITTLE_ENDIAN__, __ORDER_BIG_ENDIAN__, or __ORDER_PDP_ENDIAN__ 
__FLOAT_WORD_ORDER__ //set to either __ORDER_LITTLE_ENDIAN__ or __ORDER_BIG_ENDIAN__
__LP64__             //long int and pointers are both 64-bit and int is 32-bit
__i386__             //GNU C identifier for old intel 3x86 architecture
__i486__             //GNU C identifier for old intel 4x86 architecture
__i586__             //GNU C identifier for old intel 5x86 architecture
__i686__             //GNU C identifier for old intel 6x86 architecture
_X86_                //only defined in Mingw for intel x86 based architecture
__VA_ARGS__          //used as an extension in GCC to represent a list of arguments where an ellipsis was used

This is far from a complete list, but generally depending on your architecture, cpu, and otherwise, there will be some way to tell what you're running on.  Unfortunately, there is no way to get a complete list, even the GCC manual excludes most of the macros it establishes for a given compilation environment. As we require them, or you develop a need, there is always information somewhere for context.  The list above is just most of the more common ones you might need to reference.

When using GCC you can use -dM with -E on a file to see what is predefined.  This will need to be done from a terminal on Windows or Linux.

> For Windows/DOS: 
```echo | gcc -dM -E -```

> For Non-Windows that supports /dev/null: 
```gcc -dM -E - < /dev/null```

# \#include
There are two forms for an #include directive.  Filenames declared as <stdio.h> and "myheader.h".  The <header> form searches for a file by that name from an internal list of system directories.  These are typically part of the C Standard Library or other packages that you have installed alongside your compiler.  When including using this form "header", the compiler will search the directory that contains the file \_BASE_FILE__.  If you need to modify directories the compiler should be searching for with either form, you can use the -I_ option from the command line. (edited)

  
Common C Standard Library Headers

Name            ISO   Description
-----------------------------------------------------------------------------------------
<assert.h>            Conditional macros for testing and comparison of things
<complex.h>     [C99] Complex number arithmetic
<ctype.h>             General type functions for determining and manipulating data
<errno.h>             POSIX compatible error handling
<fenv.h>        [C99] Floating point environment for control of rounding and status flags
<float.h>             Limits for floating point types
<inttypes.h>    [C99] Format conversion of integer types
<iso646.h>      [C95] Alternative operator and token representations
<limits.h>            Limits for integer based types
<locale.h>            Localization utilities for formatting and other regional details
<math.h>              C Standard mathematics functions
<setjmp.h>            Spaghetti jump utilities
<signal.h>            Macros for signal handling, raising and processing 
<stdalign.h>    [C11] Alignment convenience macros
<stdarg.h>            Variadic function and variable argument processing
<stdatomic.h>   [C11] Atomic types, fences, operations and locks
<stdbool.h>     [C99] A relatively useless header to support fake boolean operations
<stddef.h>            General macro definitions for size_t, NULL, etc
<stdint.h>      [C99] Fixed-width integer types
<stdio.h>             General functions for input and output
<stdlib.h>            Memory management, program utilities, string conversions, random numbers, algorithms
<stdnoreturn.h> [C11] Defines the noreturn macro
<string.h>            Lots of useful string handling, memory manipulation and comparitors
<tgmath.h>      [C99] Type generic math macros which wrap around math.h and complex.h
<threads.h>     [C11] A janky and old school threading model [POSIX threads are preferred]
<time.h>              General time and date utilities
<uchar.h>       [C11] UTF-16 and UTF-32 conversion utilities
<wchar.h>       [C95] Extended multibyte and wide character utilities
<wctype.h>      [C95] Functions to determine the type contained in wide character information

Most of these you will never use, and many of these we will be going over how to rewrite, or deal with the specifics in other ways.  Most of the C Standard Libraries are janky, poorly written or generic.  Modern equivalents rely on an understanding of each platform you are coding on and for.  This is especially prevalent when dealing with input and output, memory management, and threading models.  For more information on what is and isn't contained in each of these headers, you can find them on the web.  Since our concern will be more detailed and fine grained, these are merely supplied for reference when you are starting from scratch, or just need something quick and dirty.  In general you are advised to mostly avoid the C Standard Library methods, that pretty much goes for any language. (edited)

# \#define

This is the basic fundamental way we define macros in C.  It allows us to #define named and value constants, expressions, and meta-functions.  Since #define, along with all other Preprocessor Directives are not processed by any IDE or in real-time, they tend to cause massive confusion amongst programmers.  The C++ language actually frowns on the use of Preprocessor Directives in general, citing they are a direct cause for Undefined Behaviour.  Regardless, they are incredibly powerful, can help reduce errors, and keep code tidy.  Most often they are used to avoid single line functions, having to use the inline keyword, and guarantee that code will be directly replaced.

JANKY EXAMPLE: Basic program with output showing general use of #define statements, and general setup of function main. (edited)

```C
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

#define function  //define that has no value represents an empty replacement
#define that      //define that has no value represents an empty replacement
#define has       //define that has no value represents an empty replacement
#define returns   //define that has no value represents an empty replacement
#define named     //define that has no value represents an empty replacement
#define noArgs () //define a macro named noArgs that represents ()
#define foo    2  //define a macro named foo with a constant value of 2
#define bar    4  //define a macro named bar with a constant value of 4
#define start  {  //define a macro named start that represents an open brace
#define end    }  //define a macro named end that represents a close brace
#define equals == //define a macro named equals that represents the == operator
#define and    && //define a macro named and that represents the && operator


function that returns s32 named main that has noArgs start
  if (foo equals 2 and bar equals 4) start
    puts("foo and bar checked out.");
  end

  return 0;
end
Emitted by the Compiler Post Preprocessing: (edited)
typedef int32_t s32;

s32 main () {
  if (2 == 2 && 4 == 4) {
    puts("foo and bar checked out.");
  }

  return 0;
}```

> General Output:

```foo and bar checked out.```

By using the -E command line argument to the compiler we can trigger the compiler to emit the Preprocessor stage of compiling.  All of the #define statements without a constant or represented value were removed from the code.  All other #define macros were replaced at this point with the values they represented.  We can see the constant values of foo and bar, the start and end, equals, and the and macros were all replaced.

JANKY EXAMPLE: Basic program with output showing how to create an argument based #define macro, and general setup of function main. (edited)

```C
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

#define success 1

s32 main() {
  #define buildExpress(expression) bar = (expression); break
  #define buildCase(val, expression) case val: buildExpress(expression)

  s32 foo = 2;
  s32 bar = 0;

  switch (foo) {
    buildCase(1, -1);
    buildCase(2, success);
    default: buildExpress(foo + 6);
  }

  printf("bar = %d\n", bar);

  return 0;
}
(edited)
Emitted by the Compiler Post Preprocessing: (edited)
typedef int32_t s32;

s32 main() {
  s32 foo = 2;
  s32 bar = 0;

  switch (foo) {
    case 1: bar = (-1); break;
    case 2: bar = (1); break;
    default: bar = (foo + 6); break;
  }

  printf("bar = %d\n", bar);

  return 0;
}```

> General Output:

```bar = 1```

As we can see the buildCase and buildExpress macros can be called or used just like a function.  Argument substitution happens as direct literal replacement.  There are no conversions or casts done on what is passed to a macro.  This allows you to pass things you would not normally be allowed to pass to a standard function as an argument.  The #define directive has many uses which we will explore in later examples.

There are a few operators we should cover that allow us to do some other neat things.  They are useful for concatenating strings, or casting something passed to a macro as a string.

Operator   Purpose
------------------------------------------------
 #         casts to a string
 ##        joins what is to the left and right regardless of type
 \         used to denote a multi-line macro [used to escape new lines]

JANKY EXAMPLE: Basic program with output showing how to use the #define directive, use of the # operator, and setup of function main.

```C
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  #define joinStr(str1, str2) #str1 " " #str2 "!"

  puts(joinStr(hello,world));

  return 0;
}```

> Emitted by the Compiler Post Preprocessing:

```C
typedef int32_t s32;

s32 main() {
  puts("hello" " " "world" "!");

  return 0;
}
```

> General Output:

```hello world!```

NOTE: Remember that C will join String Literals in this way automatically.

JANKY EXAMPLE: Basic program with output showing how to use the #define directive, use the ## operator, and setup of function main. (edited)
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

#define joinVars(left, right) left##right

s32 main() {
  int fooBar = 4;

  printf("%i\n", joinVars(foo,Bar));

  return 0;
}
Emitted by the Compiler Post Preprocessing: (edited)
typedef int32_t s32;

s32 main() {
  int fooBar = 4;

  printf("%i\n", fooBar);

  return 0;
}
General Output:
4
JANKY EXAMPLE: Basic program with output showing how to use the #define directive, use the \ operator, and setup of function main.
Avatar
PDrifting 08-Aug-21 01:27 PM
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

#define buildLoop(var, limit)           \
  for (int var = 0; var < limit; ++var) \
    printf(#var " = %i\n", var);        \
  puts("")

s32 main() {
  buildLoop(x, 10);
  buildLoop(y, 5);
  buildLoop(z, 3);
  return 0;
}
Emitted by the Compiler Post Preprocessing:
typedef int32_t s32;

s32 main() {
  for (int x = 0; x < 10; ++x) printf("x" " = %i\n", x); puts("");
  for (int y = 0; y < 5; ++y) printf("y" " = %i\n", y); puts("");
  for (int z = 0; z < 3; ++z) printf("z" " = %i\n", z); puts("");
  return 0;
}
General Output:
x = 0
x = 1
x = 2
x = 3
x = 4
x = 5
x = 6
x = 7
x = 8
x = 9

y = 0
y = 1
y = 2
y = 3
y = 4

z = 0
z = 1
z = 2
We need to use the \ operator with multi-line macros because the \n [new line] character is used as the line delimiter for macros.  They do not use the traditional ; end of statement terminator on the last line of a macro.  You do not need to use it on the last line of the macro definition.  Hopefully from this, you can begin to see the capabilities of the Preprocessor. (edited)
Avatar
PDrifting 08-Aug-21 02:02 PM
DOES NOT RUN: Stub code showing how to use the #define, #undef directives.
#define foo 3
#undef foo

#define combine(left,right) left##right
#undef combine

The #undef directive is useful if you need remove a macro from the known list, or to redefine a macro.  It is good practice to remove the old #define using #undef in either of these cases.

JANKY EXAMPLE: Basic program with output showing how to use the #if, #elif, #else, #endif, defined and general setup of function main. (edited)

  #include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

//always good to check the manual
//for a given compiler to find out
//what is avilable for defines.

//for microsoft visual c
//https://docs.microsoft.com/en-us/cpp/preprocessor/predefined-macros?view=vs-2019

//for gcc, mingw, tdm
//https://gcc.gnu.org/onlinedocs/cpp/Predefined-Macros.html#Predefined-Macros

s32 main() {
  printf("the build environment is ");
  
  //determines which operating system define
  //has been set by the compiler so we can find
  //out what is being used
  #if defined(_WIN32)
    // Windows (x64 and x86) specific code...
    puts("windows");
  #elif defined(__unix__)
    // Unix specific code...
    puts("unix");
  #elif defined(__linux__)
    // Linux specific code...
    puts("linux\n");
  #elif defined(__APPLE__)
    // Mac OS specific code...
    puts("mac/osx");
  #else
    puts("unknown")
  #endif

  return 0;
}
(edited)
NOTE: Keep in mind the way this code is setup, the code will emit variations depending on what Operating System this code has been executed on.  This should not to be regarded as the best way to detect these variations, but this merely a general idea on some of the basic uses of these features of the preprocessor.
Emitted by the Compiler Post Preprocessing [Unix]: (edited)
typedef int32_t s32;

s32 main() {
  printf("the build environment is ");
  puts("unix");

  return 0;
}
General Output:
the build environment is unix
Emitted by the Compiler Post Preprocessing [Windows]:
typedef int32_t s32;

s32 main() {
  printf("the build environment is ");
  puts("windows");

  return 0;
}
(edited)
General Output:
the build environment is windows

JANKY EXAMPLE: Basic program showing how you might setup debug output and control it with #define, #if, #else, #endif and the general setup of function main. (edited)
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;
typedef float f32;

#define isDebugging //comment out to disable debugging

#ifdef isDebugging
  #define debug(toPrint) puts(toPrint)
  #define debugArg(toPrint,value) printf(toPrint,value)
  #define debugArgV(...) printf(__VA_ARGS__)
#else
  #define debug(toPrint)
  #define debugArg(toPrint,value)
  #define debugArgV(...)
#endif

s32 main() {
  s32 intVar = 12;
  f32 floatVar = 78.123456;

  debug("This is a test");
  debugArg("int val = %i\n", intVar);
  debugArgV("int val = %i\tfloat val = %.2f\n", intVar, floatVar);

  return 0;
}

NOTE: This introduces the \_VA_ARGS__ macro and the use of the ellipsis [...].  When using the ellipsis, this is effectively a variable set of arguments of arbitrary length.  GCC uses the __VA_ARGS___ macro to represent all the arguments that were passed to the method that uses the ellipsis as part of its argument list.  Since debugArgV takes a full argument list like printf normally would, we can use the ellipsis and the associated \_VA_ARGS___ macro to pass the variable argument making this macro as flexible as printf would be normally.  We will explore this later in greater detail in the Intermediate coding section of the book.

Emitted by the Compiler Post Preprocessing [#define isDebugging]: (edited)
typedef int32_t s32;
typedef float f32;

s32 main() {
  s32 intVar = 12;
  f32 floatVar = 78.123456;

  puts("This is a test");
  printf("int val = %i\n",intVar);
  printf("int val = %i\tfloat val = %.2f\n", intVar, floatVar);

  return 0;
}
General Output:
This is a test
int val = 12
int val = 12    float val = 78.12
Emitted by the Compiler Post Preprocessor [//#define isDebugging]:
typedef int32_t s32;
typedef float f32;

s32 main() {
  s32 intVar = 12;
  f32 floatVar = 78.123456;

  ;  //the debug statements have been removed
  ;  //it is perfectly legal in C to have blank
  ;  //statements with only the semi-colon remaining

  return 0;
}
General Output:
 
As we can see with the #define isDebugging uncommented, or commented will either leave in or completely remove our debug statements.  This is a much better method than littering your code with older style #if isDebugging wrapped around each block of code you are using for debug output.  This method can be expanded to suit your needs.

Basic program with output showing extensive use of macros to implement a very basic virtual machine. (edited)

  #include <stdio.h>
#include <stdint.h>

#define false 0 
#define true  1

typedef int32_t  s32;
typedef uint32_t u32;

#define ADD      0
#define SUB      1
#define MUL      2
#define IDIV     3
#define JMPLCEQ  4
#define JMPLCNEQ 5
#define JMPLCLT  6
#define JMPLCGT  7
#define JMP      8
#define LBL      9
#define SETLC    10
#define INCLC    11
#define DECLC    12
#define PUSH     13
#define POP      14
#define PUT      15
#define END      16
 
s32 main() {
  s32 stack[2500];
  s32 sp = -1;
  s32 ip = 0;
  s32 lc = 0;
  s32 lbls[2500];
  s32 atEnd = false;

  u32 code[] = {
    PUSH,5,
    PUSH,12,
    PUSH,4,    
    IDIV,
    ADD,
    SETLC,10,
    LBL,1,   
    PUT,
    PUSH,1,    
    ADD,
    DECLC,
    JMPLCNEQ,1,0,
    END
  };

  s32 codeLen = sizeof(code) / sizeof(u32);

  do {
    if (code[ip] <= IDIV) {
      //process maths operations
      s32 r = stack[sp--]; 
      s32 l = stack[sp];
      switch (code[ip++]) {
        #define mathOp(name, op) case name: stack[sp] = (int)(l op r); break;
        mathOp(ADD, +)
        mathOp(SUB, -)
        mathOp(MUL, *)
        mathOp(IDIV, /)
      }
    } else if (code[ip] <= JMPLCGT) {
      //process jump comparators
      #define arg(name) s32 name = code[ip++];
      arg(op); arg(jt); arg(v);
      
      switch (op) {
        #define jmpOp(name, op) case JMPLC##name: ip = (lc op v) ? lbls[jt] : ip++; break;
        jmpOp(EQ,  ==)
        jmpOp(NEQ, !=)
        jmpOp(LT,  <)
        jmpOp(GT,  >)
      }      
    } else {
      //process all other opcodes
      switch (code[ip++]) {
        #define otherOp(name, block) case name: block; break;
        otherOp(JMP,   ip = lbls[code[ip]])
        otherOp(LBL,   lbls[code[ip]] = ip+1; ip++)
        otherOp(SETLC, lc = code[ip++])
        otherOp(INCLC, lc++)
        otherOp(DECLC, lc--)
        otherOp(PUSH,  stack[++sp] = code[ip++])
        otherOp(POP,   sp--)
        otherOp(PUT,   printf("%d\n", stack[sp]))
        otherOp(END,   atEnd = true)
        default: {
          //terminate, bad opcode encode found...
          printf("[%d] Bad Encode\n", ip - 1);
          atEnd = true;
          break;
        }
      }
    }
  } while (!atEnd && ip < codeLen);
 
  puts("[END]\nPress enter...");
  getc(stdin);
  return 0;
}

Emitted by the Compiler Post Preprocessing:
typedef int32_t  s32;
typedef uint32_t u32;

s32 main() {
  s32 stack[2500];
  s32 sp = -1;
  s32 ip = 0;
  s32 lc = 0;
  s32 lbls[2500];
  s32 atEnd = 0;

  u32 code[] = {
    13,5,
    13,12,
    13,4,
    3,
    0,
    10,10,
    9,1,
    15,
    13,1,
    0,
    12,
    5,1,0,
    16
  };

  s32 codeLen = sizeof(code) / sizeof(u32);

  do {
    if (code[ip] <= 3) {
      s32 r = stack[sp--];
      s32 l = stack[sp];

      switch (code[ip++]) {
        case 0: stack[sp] = (s32)(l + r); break;
        case 1: stack[sp] = (s32)(l - r); break;
        case 2: stack[sp] = (s32)(l * r); break;
        case 3: stack[sp] = (s32)(l / r); break;
      }
    } else if (code[ip] <= 7) {
      s32 op = code[ip++]; s32 jt = code[ip++]; s32 v = code[ip++];

      switch (op) {
        case 4: ip = (lc == v) ? lbls[jt] : ip++; break;
        case 5: ip = (lc != v) ? lbls[jt] : ip++; break;
        case 6: ip = (lc < v) ? lbls[jt] : ip++; break;
        case 7: ip = (lc > v) ? lbls[jt] : ip++; break;
      }
    } else {
      switch (code[ip++]) {
        case 8: ip = lbls[code[ip]]; break;
        case 9: lbls[code[ip]] = ip+1; ip++; break;
        case 10: lc = code[ip++]; break;
        case 11: lc++; break;
        case 12: lc--; break;
        case 13: stack[++sp] = code[ip++]; break;
        case 14: sp--; break;
        case 15: printf("%d\n", stack[sp]); break;
        case 16: atEnd = 1; break;
        default: {
          printf("[%d] Bad Encode\n", ip - 1);
          atEnd = 1;
          break;
        }
      }
    }
  } while (!atEnd && ip < codeLen);

  puts("[END]\nPress enter...");
  
  _IO_getc(stdin);
  return 0;
}


                                   NOTE: This is a good example of code that has a lot of replication that can be easily replaced by macros.  Despite this code being relatively simplistic in nature, it relies heavily on case statements that have their associated break statements.  Code of this type generates a lot of extra typing.  Simple macros can save typing, help reduce errors in repetitive code, and in general be used to generate code for you.  One of the advantages of using the preprocessor, we can maintain tokens that make sense which will be replaced once the code in compiled.  The function getc in this case is used to get a single character from the keyboard, but has been replaced by the preprocessor with __IO_getc_.  This is because getc is implemented internally and is replaced by the compiler to the association within the C Standard Library implementation used.  The example code above does implement a very basic integral stack based virtual machine.  It is very limited in capabilities, but does support a decent subset of instructions.  An array called code[] is used to hold the program that will be executed by the virtual machine.  Output from the program executed is below. (edited)
General Output:
8
9
10
11
12
13
14
15
16
17
[END]
Press enter...

Part 11: Operator Precedence
The problem with C, the standard doesn't actually define Operator Precedence, so the following table is derived from the base grammar of the C language.  There are a few anomalies, but in general this can be regarded as the order things will fire in if you have complex or compound statements using multiple operators.  Operator order in the following table is first to last priority.

Order  Operators                                                          Associativity
----------------------------------------------------------------------------------------
1      #define                                                            Replacement
2      var++ var-- () [] . -> (cast){list}                                Left to Right   
3      ++var --var +var -var !var ~var (cast) *var &var sizeof _Alignof   Right to Left
4      * / %                                                              Left to Right
5      + -                                                                Left to Right
6      << >>                                                              Left to Right
7      < <= > >=                                                          Left to Right
8      == !=                                                              Left to Right
9      &                                                                  Left to Right
10     ^                                                                  Left to Right
11     |                                                                  Left to Right
12     &&                                                                 Left to Right
13     ||                                                                 Left to Right
14     **TERNARY IF** (exp) ? (true) : (false)                            Right to Left
15     = *= /= %= += -= <<= >>= &= ^= |=                                  Right to Left
16     ,                                                                  Left to Right


    Chapter 2: Queues, Stacks, Lists, Hash Maps... Oh My! (edited)

    The following implementations are not thread safe.  A static and dynamic allocation version is provided.  These examples are not documented.  Also due to their complexity and length, they will not have the traditional output examples or dissections.  The code will compile and provide basic use in an implementation of function main. If you need help reading the code, please refer to Chapter 1.


Queues
Traditional queue examples use linked lists and other jank.  We all should understand this leads to poor cache performance and memory fragmentation.  The following queue implementation shows a different model using a cyclical array structure that amortizes in the dynamic model a possible growth malloc and series of calculated memcpy calls to reogranise and linearly structure the array only when it runs out of space.  The static version of the queue should be used most times calculated to your specific requirements.

This method goes one step further and removes the typical modulus calls and replaces them with a prebaked lookup.  It adds a minor performance gain, there is test code shown for each.  The tests are not complete, and only showing plausible ways to use it, and ideas on how to write efficient code in your projects.  There are likely to be improvements that can be made, but this is a much less terrible implementation than you will find elsewhere. (edited)
Avatar

STATIC IMPLEMENTATION WITH JANKY TESTS
static_queue_with_junk_tests.c
17.19 KB

DYNAMIC IMPLEMENTATION WITH JANKY TESTS
