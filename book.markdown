# Why learn C?

It drives the world and is the foundation of pretty much everything in the modern programming world.  Some examples of this are below.

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


C is also extremely portable, which is why it drives so many things.  The [GCC Compiler](https://gcc.gnu.org/) supports 70+ platforms and several architectures.  All of the code examples and C source code in this document will largely focus on Linux and Windows development.  You can find the base manual for GCC [here](https://gcc.gnu.org/onlinedocs/). MinGW has been used for the validation of sources on Windows, you can get it [here](https://sourceforge.net/projects/mingw/files/latest/download).  A general how to install MinGW and configure the path can be found [here](https://youtu.be/guM4XS43m4I). Unlike Unix-like environments, GCC does not come installed by default on Windows platforms. You can also turn on the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/) and use the Microsoft App Store to install a Unix-Like operating system and use GCC natively.  If you're on a Linux or non-windows platform, this document assumes you have a decent command of that environment.

# index
[Pre-Basics of GCC](#pre-basics-of-gcc)\
[⠀⠀Stages of the Compiler](#stages-of-the-compiler)\
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
[⠀⠀⠀⠀Example 18: Unions](#example-18-unions)\
[Part 2: Console Output & Using #include](#part-2-console-output-using-include)\
[⠀⠀Puts](#puts)\
[⠀⠀Putchar](#putchar)\
[⠀⠀Printf](#printf)\
[⠀⠀Format Specifier & Special Characters Table](#format-specifier-special-character-table)\
[⠀⠀C Output & Expansion on Type Examples](#c-output--expansion-on-type-examples)\
[⠀⠀⠀⠀Example 1: Using puts](#example-1-using-puts)\
[⠀⠀⠀⠀Example 2: Using Format Specifiers with printf](#example-2-using-format-specifiers-with-printf)\
[⠀⠀⠀⠀Example 3: Using printf with %x](#example-3-using-printf-with-x)\
[⠀⠀⠀⠀Example 4: Displaying Union Members](#example-4-displaying-union-members)
[⠀⠀Format Modifiers](#format-modifiers)\
[⠀⠀C Output & Format Modification Examples](#c-output--format-modification-examples)\
[⠀⠀⠀⠀Example 1: Left Justification with printf](#example-1-left-justification-with-printf)\
[⠀⠀⠀⠀Example 2: Zero Padding with printf](#examples-2-zero-padding-with-printf)\
[⠀⠀⠀⠀Example 3: Side-Effects using printf %x and signed numbers](#example-3-side-effects-using-printf-x-and-signed-numbers)\
[⠀⠀⠀⠀Example 4: Formating Floating Point Types with printf](#example-4-formatting-floating-point-types-with-printf)\
[⠀⠀⠀⠀Example 5: Formating double Floating Point Types with printf](#example-5-formatting-double-floating-point-types-with-printf)\
[⠀⠀⠀⠀Example 6: Formating long double Floating Point Types with printf](#example-6-formatting-long-double-floating-point-types-with-printf)\
[⠀⠀Zero is not always Zero](#zero-is-not-always-zero)\
[⠀⠀⠀⠀Example 1: Issues with Floating Point Types and Approximations](#examples-1-issues-with-floating-point-types-and-approximations)

# Pre-Basics of GCC
## Stages of the Compiler

```
   [1]             Source File (.c)
                          |
   [2]              Pre-Processor
                          |
   [3]     Generation of Assembly Code (.s)
                          |
   [4]      Generation of Object File (.o)
                          |
   [5]             Fetch Libraries
                          |
   [6]                 Linker
                          |
   [7]         Generation of Executable
```

1. Source File - Main file containing your program's syntax.

2. Pre-processor - It strips out comments from the sources.  Fetches header files (.h) and executes macros.

> -E will halt the compilation process and emit the pre-processor stage.

3. Generation of Assembly - This is an intermediate stage generating assembly that can only be used by the GCC compiler.  The GNU Assembler which is part of GCC can build this file with some minor modifications.  It is formatted in AT&T style vs. Intel which is generally easier to read.

> -S will halt the compilation process and emit the intermediate assembly stage.

4. Generation of Object File - Before the linker places the appropriate execution information at the linking stage, a general .o [object file] is created.  Libraries and other code that is meant to be used elsewhere can also be stored in this format to be included during linking with projects.

> -c will halt the compilation process and emit the bytecode stored inside the object file.  This stage is not human-readable.

5. Fetch Libraries - These will generally be stored in object file format.  Other libraries will be fetched based on what headers you have included from the C Standard Library.

6. Linker - This is where everything is tied together.  You can create appropriate header information, symbol tables, and addressing information at this stage for the final creation of your executable.

7. Generation of Executable - If everything went well and compilation was not halted by another stage, GCC will emit an executable appropriate to your platform and the specifications you supplied for its creation.

**NOTE** - When appropriate to examples later in the book, these stages will be explored in greater detail.

# Chapter 1: A Tutorial Introduction
## Part 1: Data Types

These refer to specific ways that C stores data.  Data has a specific storage size or memory footprint that it consumes.  The type associated with data determines how it will be stored and interpreted in memory.  C Data Types are broken up into 4 types.  However, we are not going to discuss Enumerated Types in any other context than -- **avoid using them**.

### Basic Types

These are the general arithmetic types that are broken down into integer and floating-point formats.

#### Integer Types

|Keyword             |Bit Width|Byte Width|Low Value||High Value|Literal Suffix
|---|:--:|:--:|--:|:--:|:--|:--:|
|char              |8  | 1|    Single Character|||N/A
|signed char       |8  | 1|                 -128| to |127|
|unsigned char     |8  | 1|                    0| to |255|
|short             |16 | 2|                -32768| to |32767|
|unsigned short    |16 | 2|                     0| to |65353|
|int               |32 | 4|        -2,147,483,648| to |2,147,483,647|
|unsigned int      |32 | 4|                     0| to |4,294,967,295|U
|long long         |64 | 8|  -9223372036854775808| to |9223372036854775807|LL
|unsigned long long|64 | 8|                     0| to |18446744073709551615|LLU

**NOTE:** GCC on Linux typically defaults to 64-bits.  On Windows, MinGW defaults to 32-bits.  For compatibility of code between 32-bit and 64-bit, make sure your _long_ Data Types are 64-bit by using _long long_ instead.  In 32-bit environments, this will make _long_ 64-bit, and in 64-bit environments, it will treat _long long_ as 64-bit _long_.

#### Floating Point Types

|Keyword         |Bit Width|Byte Width|Low Range||High Range|Precision|Literal Suffix
|:--|:--:|:--:|--:|---|:--|--:|:--:|
|float           |32|  4 |    1.2E-38| to |3.4E+38    | 6 decimal places|F
|double          |64|  8 |   2.3E-308| to |1.7E+308   |15 decimal places|
|long double     |80| 10 |  3.4E-4932| to |1.1E+4932  |19 decimal places|L

**NOTE:** The Literal Suffix fields for both Integral and Floating Point Types are used to apply a data format to values assigned to variables on declare to ensure they are recognised as a specific type.  GCC may throw warnings if you do not use them. This is specifically a case when it comes to 64-bit integral assignments, you must apply the suffix.  Also with floating point data, since _double_ is the default.  Examples in Chapter 2 will expand on the use of Literal Suffixes.

#### Enumerated Types

These are typically regarded as another arithmetic type used to define named variables that are assigned discrete integer values.  They are used in place of magic numbers or hard-coded values that can have arbitrary meanings.  The general modern view is to avoid using them.

**MAGIC NUMBERS** - Enumerated values were created to solve this problem.  However, they create more problems than they resolve.  When we consider the issue of obfuscated information by using values instead of meaningful tokens we generally refer to those as Magic Numbers.  It is generally regarded that we should not use them as initial values or in the endpoint test expressions of a while, do while, or for loops.  There is a general concern for avoiding their use in expressions, mallocs, and other statements where it may obfuscate information and taint obvious readability or understanding of the code.  You are advised to use a #define, or specific variables within contextual scope to give a meaningful name to your value.

```
1. They are not integer values, but GCC does treat them as such.
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
12. Tends to force state-driven coding.
13. They violate Data Oriented Design and Don't Repeat Yourself principles.
14. Use a #define declaration instead.  We are not C++ coders.
```
[Return to Index](#index)

### Derived Types

These include Arrays, Pointers, Structures, Unions, Functions, and Type Definitions.

#### Arrays

An Array is created from a Data Type that is generally used to store multiple elements of data.  They are zero-indexed and you declare them by specifying the total number of elements needed.  To access the last element in an Array use the total number of elements minus one.  Arrays, once declared, cannot change size.  Elements are accessed by unique integer based indices.  Data stored inside an Array, provided Pointers are not involved with the data stored in each element, will generally create a single block of contiguous memory.  Most off-by-one errors in your code will be created by trying to access information inside Arrays. You generally do not need to pass an Array by reference to a function as an argument.  In most cases when using them, they will be treated as pointers or referenced as such.

#### Pointers

These are regarded as one of the single hardest concepts to learn in programming, and the reason most people avoid coding in C.  A Pointer is a variable that uses the address of another variable for storage.  It uses an address that represents a specific location in memory.  You must declare pointers like any other variable declaration.  Confusingly, Pointers use the asterisk for dereferencing.  This simply means, to get the value stored at the location of memory the Pointer is pointing at.  The asterisk is also used as the multiplication maths operator.  Pointers have many problems associated with their use, but they are a staple in the advanced C language syntax.  To pass variables to a function by reference you must use a pointer for all Data Types, except Arrays in some cases.

C has a special kind of Pointer called the Function Pointer.  This allows the creation of a Pointer that will point at the address of a specific Function that has been declared.  There are some rules they must follow, but can be very useful when you are writing sorting or other types of algorithms that may have a comparator or some other piece of the algorithm that could change based on requirements.  Instead of creating unique Functions for each specific task of sorting by ascending or descending order, you can pass in a Function that can be used to address this.  There are other more complicated, but useful scenarios when working with graphics engines where you may have to substitute an optional chunk of your code that runs if an equivalent feature is not available on a given platform.

Other uses of Pointers and Function Pointers exist to form bridges tying certain portions of an Operating System together or to make a call inside a specific library accessing a foreign piece of code.

**NOTE** - Function pointers should be used sparingly in your code.  We need to cover some basic operations of a modern CPU to understand why. When you compile your code, the compiler creates something called bytecode.  The bytecode is a compressed representation of opcodes.  Opcodes are references to specific Operation Codes for commands inside the CPU. When a modern CPU is executing bytecode, it goes through several steps.  These steps generally follow fetch, unpack, and then execution.  The problem is created in prediction models that modern CPUs have. They attempt to determine where the operations you are executing will end up.  Modern processors use a very complicated set of algorithms inside a Data Pipeline that has a cache.  We know that anytime an indirect jump takes place, either by a general function call or a jump created by some other type of branching code.  This includes if, switch, or expressions used in loops.  These guarantee the potential to destroy the prediction cache.  If your code path is not created in a way that is generally predictable this can cause drastic performance consequences.  Always try to keep your code flow simple.  This is also a good argument for a single-entrance, single-exit coding style.

[Return to Index](#index)

#### Structures and Unions

These are your user-defined record types.  Useful when you need to combine groups of items, fields, or members of different data types that can be referenced by name to create a single type.  C doesn't have classes, or support object-oriented coding methods for the most part.  All members of a _struct_ and _union_ are publicly declared.  Defined _struct_ and _union_ types are not assigned memory until declared, and will always be stored in contiguous memory.  The only real difference between a _struct_ and _union_ type is how they are stored in memory.

> _struct_ members have distinct regions of memory allocated

> _union_ members all share the same memory region

Alignment, packing, and padding are compiler implementation-specific.  GCC manages these aspects of these Data Types for you.  In the case of needing to override the defaults, you can use GCC compiler defined macros.

**Alignment** - This tells the compiler to attempt a specific alignment during allocation to specific boundaries. Alignment can only be used to increase member boundaries. These are determined by the linker and the platform you are compiling on.  GCC by default will optimise for the platform you are compiling on.  You can assume this is the default memory layout.  Keep in mind your linker will be a limiting factor on the largest size you can align to.  This will be platform-specific.  Specifiying a byte alignment of 16 when the linker or platform can only support 8, will not not have any benefits.

> __attribute__ ((aligned ([in bytes])))

> __attribute__ ((aligned)) // default attribute in GCC

**Packing** - Specifies to the compiler that it should use the minimum footprint of memory required to represent the type.  All members of the _struct_ or _union_ Data Types will have the same equivalent packed attribute applied to them.  This will almost always affect performance negatively.  If you are using memory constrained platforms, the performance tradeoff may be required to make things fit.

> __attribute__ ((packed))

**Padding** - Is required, and can be manipulated by alignment and packing attributes. Overriding the default padding performed by GCC is likely to slow down access to members, but can save memory. Padding will only be inserted when a _struct_ member is followed by another _struct_ member that requires a larger alignment or at the end of the _struct_ to align it to a specific boundary. GCC by default is not allowed to reorder any _struct_ members to achieve optimal alignment, so programmers should be mindful of their member layouts inside their _struct_ definitions.

**Transparency** - This only applies to _union_ Data Types. Accepting multiple types of arguments in C is problematic.  There is no Function Overloading.  However, it is possible to use a transparent _union_ to accomplish being able to pass multiple strictly declared Data Types using this attribute.  For instance, in POSIX when dealing with sockets and other networking code, several functions take multiple argument Data Types.  This forces the function and the way it will be called with arguments to be treated in a special context.  This is a bypass for getting around having to use _void_ pointers which would allow any type to be passed.

> __attribute__ ((__transparent_union__))

[Return to Index](#index)

#### Functions

This is another very hard concept for programmers to grasp -- code reuse.  Functions make this possible.  They are a block of syntax statements put together to perform a specific task.  Learning when to use Functions takes a lot of practice.  When you declare a Function you can provide a Return Type, and Argument Types that you want to pass to the Function to be used by the statements inside it.  Functions can call other Functions, and use other Data Types to declare variables.

```
[return type] [name]([argument list])
int           foo   (int a, float b)
```

The C Standard Library provides numerous Functions that you can call.  These often require using the correct _#include_ statement before they can be used.  We will discuss this in detail when going over the preprocessor and the side effects associated with including and creating headers in your code.

There is one Function that must be present in all programs called main.  This is your entry point to your program.  When you execute programs this will be where the main portion of the controlling code exists.  It is required to be present.  Your main Function should always return an int type.  It can optionally have no arguments or a pair of arguments to accept information being passed to it from the command line.

The Return Type from main is used by the Operating System to determine how the program terminated.  You are expected to return 0 if the execution exit was normal, or a non-zero based value to report abnormal termination.  You will see many tutorials and examples that exclude the return value from main.  This was common many decades ago, but modern Operating Systems, especially Linux, expect the return result.  Some compilers will default to a return 0 if the statement is omitted.  For clarity in your code, you should ensure the return statement exists.

Functions can also be invoked from almost anywhere in the source code for your program.  Once a Function is created you can use it over and over.  Functions are extremely useful and practical.  They are required to keep moderate to large code bases tidy.

Many tutorials written for C, still declare Function main as Return Type void.  Any Function with a Return Type declared as void cannot return any value once a Function has completed executing its statements. This is not to slight the old-school manuals of my youth, but they promote models of coding in C that are largely outdated. Beyond this, there are features of more modern languages that C does not support. Function Overloading, is one of them, so all Function names must be unique.

**Function Overloading** - The ability to create multiple Functions with the same name declaration and different arguments.  In modern programming, this is a major drawback that C has not added the ability to use this feature of coding.  This drives many C programmers to write C in C++.  This has a host of other drawbacks.  Despite missing this syntax feature, you can still write robust and useful programs in a meaningful way with C.  A later standard has implemented Generics into C with Macros that can emulate Function Overloading.  When discussing the preprocessor, we will cover this feature.

**Argument Lists** - Functions use argument lists to deal with information you might need to pass or receive back from a function once it is done executing.  They consist of a Data Type and name separated by a comma. This book does not use the modern form of supplying void when there are no arguments accepted.  GCC does not warn if you make a function call with arguments to an empty argument listed function declare.  You will see comments on the Undefined Behaviour this technically causes, however, at best you're going to get a warning.  C compilers have a fuzzy area when it comes to empty argument lists. Since at best you will get a warning, this book excludes the promotion of using void argument lists.  The only other alternative is to use Function Prototypes.

**Function Prototypes** - Generally these create code clutter, but they can be meaningful in context and are required when declaring Function Pointers in a modified syntax. The book will detail when using Function Prototypes is generally a good idea.  Since all C Compilers are known to be single-pass, your functions must be declared before use. If a Function is declared elsewhere, externally, or compiled/linked from another foreign piece of code, you must use a Function Prototype to announce that the compiler should be aware to look for it. Otherwise, you are encouraged to reorder your main Function to the end of your code and order all other functions in a precalling fashion.  This is another heavily debated topic amongst purists.  As mentioned this book focuses on keeping code clean, easy to read, hardware-friendly, and mostly modern. Some old-school syntax is still encouraged regardless of side effects.

**SINGLE-ENTRANCE/SINGLE-EXIT** - As mentioned earlier in Pointers, there is an issue with Function Pointers creating a potential for unpredictable code.  To simplify the flow and reduce the branching potential inside your Function you should ensure that you only have a single return statement that exists at the end of each of your Functions. Placing more than one return statement inside a Function has the potential to confuse the compiler and prevent it from creating clean bytecode.  Make sure you do what you can to assist the compiler to create predictable and clean bytecode by ensuring simple program flow.  Many programmers will argue this does not matter, but it does.  You might also hear arguments that languages like GO promote the idea of multiple exits from a Function.  Please remember, that not all compilers treat all forms of code the same.  What works well in one language, is unlikely to be performant in others. C compilers are complex, they do not do well with complicated code.  They make mistakes, and often their internal prediction algorithms to optimise code will give up when you fail to keep the flow of your code simple.  See the [KISS Principle](https://en.wikipedia.org/wiki/KISS_principle).  When in doubt check your code with [Godbolt](https://godbolt.org).

**NOTE** - No process is going to save you from mistakes you're going to make in your code based on standards, compiler warnings, or style guides.  Based on the discussions around Functions, you are encouraged to understand that C can be an over-forgiving language and pretty much take whatever you throw at it. Understanding what the code is doing in C is far more important than anything you can do to generate useless warnings for mistakes you should be aware of in your code. 

[Return to Index](#index)

#### Type Definitions

To implement a Type Definition you must use the _typedef_ keyword.  This allows you to give meaningful names to things, and stop having to type the typical longer syntax required by C.   It also allows forward declarations of things.  Many libraries have custom Type Definitions to keep track of what specific parts of the library belong to what.  OpenGL comes to mind, or even just having the desire to shorten unsigned long long int to u64.  This has excellent utility when used meaningfully.  Many C purists discourage using Type Definitions, but you cannot overlook the modern desire to keep your code clean, readable, and maintainable.

There are many good discussions between Linus Torvalds and the rest of the internet on [his views](https://yarchive.net/comp/linux/typedefs.html) on programmers that abuse the _typedef_ keyword.  It can certainly be agreed that this is a completely abusable feature of C.  But like the _goto_ keyword, there are some places where it is useful.  You will be urged to ignore a feature of the language by many programmers and tutorials because most never learn when to use it in the proper context. This is an argument that prevents future growth and evolution of the understanding of the language and where C programmers may need to make changes to the Standard for the ongoing upkeep and use of the language.

Most projects and coding firms you will write code for have Style Guides.  Each guide will usually include a section on Type Definitions.  Along with other restrictions on how code should be written for the given project.  In general, if it makes things easier for you to write code, is generally self-documenting, helps with maintenance of the code base, then use it regardless of the opinions of other coders. Unless the project you are working on has a strict Style Guide.  In this case, you must follow it, regardless of preferred personal coding styles.

**NOTE** - You will see _typedef_ being used in pretty much every example in this book.  Instead of using <stdint.h>, which normally provides a _typedef_ for specific bit width data types, this book will start off using shorter forms of the int32_t for unsigned int.  Instead prefixing all unsigned types with a _u_, and signed types with an _s_.  In this case, _s64_ would be a type guaranteed to be at least 64 bits and signed.  The only base data type in C that you will see unmodified with a _typedef_ is _char_.  It has no equivalent associated signed or unsigned state.  Remember the _char_ data type is unique in that it has three distinct states _char_, _usngined char_, and _signed char_.  The _typedef_ _u8_, and _s8_ specifiy an _unsigned char_, and _signed char_ of 8 bits wide.  Floating point types will be prefixed with an _f_.  In the case of structs, unions, and other specific user types they will be prefixed with a _T_.

[Return to Index](#index)

#### Void

Despite this being a Data Type that can be used in various scenarios, some restrictions on void should be discussed.  When dealing with void, it generally means different things contextually. There are also problems with void conversions and data loss. Opportunities to create Undefined Behaviour are also in abundance. 

Unlike other Data Types, you cannot directly declare a variable as _void_ unless it is a pointer.  _void_ when used as a Function Return Data Type, signifies that a Function is incapable of returning any information from it.  Pointer Data Types declared as _void_ can be extremely flexible.  They can store any other Data Type, mixed data, memory layouts, and can also be used to point to Functions.  Many Functions inside the C Standard Library will return a _void_ pointer, or consume one as a Function Argument. 

_malloc()_ and _free()_ are good examples of this.

> void *malloc(size_t size)

> void free(void *ptr)

When declaring Function Arguments in a Function Prototype you should technically use void if the Function Argument List is meant to be nothing.  GCC for backwards compatibility maintains arbitrary Function Prototypes and definitions of functions which can lead to problems if you program using the Function Prototypes.  As mentioned in the Functions sections for Arguments Lists, this book does not use _void_ in this way. 

[Return to Index](#index)

### Basic Code Examples

#### Example 1: Variable Declarations
Basic program that has no output.

1. declaring basic variables and assigning default values
2. setup of function main 

```C
int main() {                                   // Main program entry.
  unsigned char foo = 1;                       // Variable type char named foo and assigns it a value of 1.
  signed   char bar = -10;                     // Variable type char named bar and assigns it a value of -10.
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
2. definition of an arbitrary array with default values
3. setup of function main

```C
typedef int          s32;                      // Associate type signed int with s32.
typedef unsigned int u32;                      // Associate type unsigned int with u32.

s32 main() {                                   // Main program entry.
  u32 foo[] = {0, 1, 2, 3, 4, 5, 6};           // Declare type u32 named foo.
                                               // The square brackets [] are used to
                                               // denote an array in C. In this case
                                               // we are not defining the array with a
                                               // starting size, but we are assigning 
                                               // default data to it. When using GCC,
                                               // this is a method for automatic
                                               // initialisation of the array. It will
                                               // calculate the size required for you.
  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 10: Arrays
Alternate basic program that has no output.

1. using a typedef to declare a custom Type Name
2. definition of an arbitrary array with default values
3. setup of function main

```C
typedef int          s32;                      // Associate type signed int with s32.
typedef unsigned int u32;                      // Associate type unsigned int with u32.

s32 main() {                                   // Main program entry.
  u32 foo[7] = {};                             // Declare type u32 named data.
                                               // In this case we are declaring 7 elements.
                                               // C is a 0 index based language, so this 
                                               // array will have a range of 0 to 6. By
                                               // assigning {} as the default data to it,
                                               // we are telling GCC to initialize all the
                                               // data elements to 0.
  return 0;                                    // Return status successful      
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
typedef int          s32;                      // Associate type signed int with s32.
typedef unsigned int u32;                      // Associate type unsigned int with u32.

typedef struct _TFoobar TFoobar;               // Associate struct _TFoobar with TFoobar.
                                               // We need this forward typedef because
                                               // the struct has a member data type
                                               // of itself.

struct _TFoobar {                              // You cannot use the standard typedef
  u32 foo;                                     // method of declaration when your struct
  u32 bar;                                     // contains a member of itself.
  TFoobar *foobar;                             // Members that are struct data types
};                                             // must be declared as pointers.

s32 main() {                                   // Main program entry.
  TFoobar data[15] = {};                       // Arrays of structs can be default initialised
                                               // in this case we have declared 15 elements.
                                               // This will have a range of 0 to 14.
                                               // All fields will be set to a value of 0.
  return 0;                                    // Return status successful.
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
typedef int          s32;                      // Associate type signed int with s32.
typedef unsigned int u32;                      // Associate type unsigned int with u32.

typedef struct _TFoobar TFoobar;               // Associate struct _TFoobar with TFoobar
                                               // we need this forward typedef because the
                                               // struct has a member data type of itself.

struct _TFoobar {                              // You cannot use the standard typedef
  u32 foo;                                     // method of declaration when your struct
  u32 bar;                                     // contains a member of itself.
  TFoobar *foobar;                             // Members that are struct data types
};                                             // must be declared as pointers.

s32 main() {                                   // Main program entry.
  TFoobar data[15] = {                         // Arrays of structs can be default
    { .foo = 12, .bar = 8 },                   // initialised. Each element must be
    {},                                        // contained in a secondary block of {}
    { .foo = 1 }                               // and then it can follow the rules
  };                                           // defined earlier in examples for
                                               // initialisation. Commas are used to
                                               // separate a list of consecutive
                                               // initialisations. Even though this
                                               // has 15 elements the remaining
                                               // elements will be default initialised
                                               // to 0. This is merely one method for
                                               // initialisation during declare.

  data[12] = (TFoobar){                        // Accesses element 13 [12+1 from 0 index].
    .foo = 5, .bar = 6                         // We need to perform a cast (TFoobar) then
  };                                           // it's possible to use the standard struct
                                               // field initialisation.
  return 0;                                    // Return status successful.
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
typedef int          s32;                      // Associate type signed int with s32.
typedef unsigned int u32;                      // Associate type unsigned int with u32.

typedef struct _TFoobar TFoobar;               // Associate struct _TFoobar with TFoobar.
                                               // We need this forward typedef because
                                               // the struct has a member data type
                                               // of itself.

struct _TFoobar {                              // You cannot use the standard typedef.
  u32 foo;                                     // Method of declaration when your struct
  u32 bar;                                     // contains a member of itself.
  TFoobar *foobar;                             // Members that are struct data types
};                                             // must be declared as pointers.

s32 main() {                                   // Main program entry.
  TFoobar data[15] = {                         // Arrays of structs can be default initialised.
    [ 0].foo = 12, [ 0].bar = 8,               // Each element and member can be referenced
                   [ 2].bar = 3,               // by element index in this manner also, then
    [12].foo = 5,  [12].bar = 5                // follow rules defined earlier in examples
  };                                           // for member initialisation. Commas are used
                                               // to separate a list of consecutive 
                                               // initialisations. Even though this has 15, the
                                               // remaining elements will be default initialised
                                               // to 0. This is another method for initialisation
                                               // during declaration.
  return 0;                                    // Return status successful.
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
typedef int          s32;                      // Associate type signed int with s32.
typedef unsigned int u32;                      // Associate type unsigned int with u32.

s32 main() {                                   // Main program entry.
  u32 data[] = {                               // Arrays can be default initialised using
    [  0 ... 10] = 1,                          // ranges for specific values in this manner.
    [ 11 ... 20] = 3,                          // This will define an arbitrary array with
    [ 21 ... 99] = 5,                          // 101 elements ranging from 0 to 100. It also 
    [100       ] = 0                           // works for fixed element declares of arrays
  };                                           // provided indexes fall within the range of
                                               // elements defined by the fixed value.
  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 14: Alternate Way to Typedef Structs
Basic program that has no output.

1. using a typedef to declare a custom Type Name
2. declaring a temporary name for a self-referencing struct
3. implement a very primitive form of a linked list
4. assigning things to pointers using the address of the operator
5. setup of function main

```C
typedef int s32;                               // Associate type signed int with s32.

typedef struct _TFoo {                         // Assign the initial struct name as _TFoo.
  struct _TFoo *next;                          // You must then reference struct _TFoo.
  s32           data;                          // Create a member named data inside the struct.
} TFoo;                                        // A new referencing name can be assigned as
                                               // usual. Regardless of the style you use, be
                                               // consistant.
                                               
                                               // This creates a simple linked list. Though,
                                               // you want to avoid following this style of
                                               // struct declaration if you intend to declare
                                               // allocated chains of structs this way. It
                                               // will lead to memory fragmentation and
                                               // other nasty side-effects.
                                               
                                               // Consider using an array, or if allocating,
                                               // use a single block allocation which can
                                               // be treated as an array.  DO NOT ALLOCATE
                                               // INDIVIDUAL INSTANCES.
                                               
                                               // Remember, pointers that reference a single
                                               // block of memory regardless of where it is in
                                               // memory can be treated as an array of objects.
                                               // Even void pointer memory can be cast, and
                                               // other type cast memory can be traversed as
                                               // an array of another type by changing the
                                               // cast of the pointer looking at that region
                                               // of memory.
                                               
s32 main() {                                   // Main program entry.
  TFoo foo = {};                               // Create a local instance of TFoo named foo.
  TFoo bar = {};                               // Create a local instance of TFoo named foo.
  foo.test = &bar;
  
  return 0;
}

#### Example 15: Unions
Basic program that has no output.

1. using multiple typedefs to declare custom Type Names
2. creation of a union and its declaration
3. setup of function main

```C
typedef unsigned char      u8;                 // Associate type unsigned char with u8.
typedef unsigned short     u16;                // Associate type unsigned short with u16.
typedef int                s32;                // Associate type signed int with s32.
typedef unsigned int       u32;                // Associate type unsigned int with u32.
typedef unsigned long long u64;                // Associate type unsigned long long with u64.

typedef union {                                // Declare typedef for union.
  u8  chars [8];                               // Takes 8x 1 byte to make a u64.
  u16 shorts[4];                               // Takes 4x 2 bytes to make a u64.
  u32 ints  [2];                               // Takes 2x 4 bytes to make a u64.
  u64 base;                                    // Largest type inside the union at 8 bytes.
} TMagiCaster;                                 // Assign TMagiCaster as the union name.

s32 main() {                                   // Main program entry.
  TMagiCaster foo = {};                        // Unions can be initialised to 0 the same
                                               // as structs. Any assignment to any of
                                               // the members will cause the automatic
                                               // update of all other members inside the
                                               // union. This is because each member of
                                               // the union shares the same memory address
                                               // as every other member in the union.
                                               // You gain auto-casting or assignments
                                               // between types for free.
  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 16: Problems with Unions
Basic program that has no output.

1. shows using multiple typedef to declare custom Type Names
2. how to create a union
3. data loss/confusing union behaviour
4. setup of function main.

```C
typedef unsigned char      u8;                 // Associate type unsigned char with u8.
typedef unsigned short     u16;                // Associate type unsigned short with u16.
typedef int                s32;                // Associate type signed int with s32.
typedef unsigned int       u32;                // Associate type unsigned int with u32.
typedef unsigned long long u64;                // Associate type unsigned long long with u64.
typedef float              f32;                // Associate type float with f32.
typedef double             f64;                // Associate type double with f64.
typedef double long        f80;                // Associate type double long with f80.

typedef union {                                // Declare typedef for union.
  char *pchars;                                // When you cross types in this case
  u8    chars     [8];                         // mixing pointers, and floating point
  u16   shorts    [4];                         // numbers with integers you will cause
  u32   ints      [2];                         // data loss, conversion cast problems
  u64   intBase;                               // as these types are fundamentally
  f32   floats    [2];                         // incompatible on a memory storage level.
  f64   doubles   [2];                         // Floating points and pointers traditionally
  f80   floatBase;                             // are not used in unions because of this.
} TMagiCaster;                                 // Assign TMagiCaster as the union name.

// There are special cases where you may want to mix some types but generally follow that
// pointers in unions will reference the address, and not the data at the pointer. Floating
// points will cause some form of awry behaviour when converting between them. This is not
// a good use of a union.

s32 main() {
  return 0;
}
```

[Return to Index](#index)

#### Example 17: Ideas on Dealing with Union Troubles
Basic program that has no output.

1. shows using multiple typedefs to declare custom Type Names
2. how to create a struct with an anonymous union inside it
3. setup of function main

```C
typedef unsigned char      u8;                 // Associate type unsigned char with u8.
typedef unsigned short     u16;                // Associate type unsigned short with u16.
typedef int                s32;                // Associate type signed int with s32.
typedef unsigned int       u32;                // Associate type unsigned int with u32.
typedef unsigned long long u64;                // Associate type unsigned long long with u64.
typedef float              f32;                // Associate type float with f32.
typedef double             f64;                // Associate type double with f64.
typedef long double        f80;                // Associate type double long with f80.

typedef struct {                               // Declare typedef for struct.
  union {                                      // In this case we are declaring an
    u8  chars   [8];                           // anonymous union to deal with our
    u16 shorts  [4];                           // compatible integer types and embedding
    u32 ints    [2];                           // it inside our struct. These members will
    u64 intBase;                               // still share the same memory region where
  };                                           // the members outside the union will have
  char *pchars;                                // their own regions of memory as regular
  f32 floats    [2];                           // members of a struct.
  f64 doubles   [2];
  f80 longFloat;             
} TMagiCaster;               

s32 main() {
  TMagiCaster foo = {};
  
  // You can access the members from the anonymous union as if they were base members of
  // the struct. If we named the union inside the struct, you would need to specify the
  // union name as in foo.unionName.chars to access those members inside the union. The
  // anonymous union used in this way allows for a better layout.
  
  // foo.chars      - inside anonymous union
  // foo.shorts     - inside anonymous union
  // foo.longFloat  - base member of the struct
  
  return 0;
}
```

[Return to Index](#index)

#### Example 18: Unions
Basic program that has no output.

1. using a union
2. declaring a series of anonymous struct layouts for common associations of data
3. setup of function main

```C
typedef int   s32;                             // Associate type signed int with s32.
typedef float f32;                             // Associate type float with f32.

typedef union {                                // Declare typedef for struct.
  struct {                                     // Each of these anonymous structures
    f32 x;                                     // inside the union will be treated as
    f32 y;                                     // two seperate groups of members. Each
  };                                           // anonymous struct is part of the union.
  struct {                                     // All the structs will share the same
    f32 u;                                     // memory region.
    f32 v;                                     //  set 1:
  };                                           //    foo.x
  struct {                                     //    foo.u
    f32 left;                                  //    foo.left
    f32 right;                                 //    foo.width
  };                                           //  set 2:
  struct {                                     //    foo.y
    f32 width;                                 //    foo.v
    f32 height;                                //    foo.right
  };                                           //    foo.height
  f32 members[2];                              // This array will place set 1 at index 0
} T2DVectorF32;                                // and set 2 at index 1.

s32 main() {                                   // Main program entry.
  T2DVectorF32 foo = {};                       // Default initialise all members to 0.
  
  foo.x = 0.6f;                                // Assigns a value of 0.6f to set 1.
  foo.right = 8.5f;                            // Assigns a value of 8.5f to set 2.
  
  return 0;                                    // Return status successful.
}
```

It might seem strange to cover the complexities of struct, union, typedef, and other things before the basics of general variable use and output, but since each of those things is likely to use the prior outlined references, it seemed prudent to cover those first.  This gives general exposure, so when used in the next pieces they are not new concepts.  We are going to bypass Functions, Pointers, and other types not discussed until post Console Output.

[Return to Index](#index)

# Part 2: Console Output & Using #include

Console, or Terminal output has been around since the advent of computer screens.  It is the most common way programmers can present information from within the program.  C has Functions built into the Standard Library that can be accessed from various includible libraries.  This is where the #include tag is useful.  For this context, we will be referencing the library stdio.h. 

> #include <stdio.h>
 
The Standard I/O library gives us access to several useful predefined Functions.

### Puts

This allows us to write a string of char to the Console and will append a newline character to the output automatically.  The function prototype for puts...  

> int puts(const char *str)

In this case, it returns an int value and accepts a Pointer Type of char named str.  As usual with functions that will accept char strings, they need to be NULL terminated.  In other words, make sure your char string, buffer, or other form of data has a '\0' literal on the end of it.  We will cover char strings more later.

The int return from puts will be the total number of characters written to the Console including the '\n' it appends to the end.  If there is an error, the return will be set to the constant EOF and it will set an error number you can lookup.  If you missed terminating the string with '\0', you will cause Undefined Behaviour.

### Putchar

Sometimes you just need to output a single char to the Console.  This is what putchar is for.  The function prototype for putchar.

> int putchar(int character)

It might seem odd that putchar accepts an int instead of char, but these are compatible Data Types that can be thought of as a union. Any int can be a char and any char can be an int.  We'll go over char literals and int more later. This makes putchar extremely flexible. You can refer to a specific character by an int value, or by a char literal.

The int return from putchar returns the char output to the Console. If there is an error, the return will be set to the constant EOF and it will set an error number you can look up. The GCC Macro for EOF defines it as having a value of -1. It is possible to have some other value depending on the library you are using, or the compiler. To avoid Magic Numbers, using EOF is the preferred option to test for.  These constants make your code portable.

### Errno Constants

This is a little bit of a side-track, but where the errno values come into play.  Depending on Linux or Windows versions of GCC, the constants change.  Mingw programmers have done their best guess, but errno constants are not cross-platform compatible across different operating systems.  Below will be the list for Linux then the list for Windows.  Generally, most of the errno constant descriptions leave much to the imagination.  However, some are straightforward.

#### Produced from perror() on Linux/UNIX

The man page for [perror()](https://man7.org/linux/man-pages/man3/perror.3.html) if you would like more information.

|Number|Error Code|Description|
|:---:|:---:|:---:|
|1|EPERM|Operation not permitted|
|2|ENOENT|No such file or directory|
|3|ESRCH|No such process|
|4|EINTR|Interrupted system call|
|5|EIO|I/O error|
|6|ENXIO|No such device or address|
|7|E2BIG|Argument list too long|
|8|ENOEXEC|Exec format error|
|9|EBADF|Bad file number|
|10|ECHILD|No child processes|
|11|EAGAIN|Try again|
|12|ENOMEM|Out of memory|
|13|EACCES|Permission denied|
|14|EFAULT|Bad address|
|15|ENOTBLK|Block device required|
|16|EBUSY|Device or resource busy|
|17|EEXIST|File exists|
|18|EXDEV|Cross-device link|
|19|ENODEV|No such device|
|20|ENOTDIR|Not a directory|
|21|EISDIR|Is a directory|
|22|EINVAL|Invalid argument|
|23|ENFILE|File table overflow|
|24|EMFILE|Too many open files|
|25|ENOTTY|Not a typewriter|
|26|ETXTBSY|Text file busy|
|27|EFBIG|File too large|
|28|ENOSPC|No space left on device|
|29|ESPIPE|Illegal seek|
|30|EROFS|Read-only file system|
|31|EMLINK|Too many links|
|32|EPIPE|Broken pipe|
|33|EDOM|Math argument out of domain of func|
|34|ERANGE|Math result not representable|
|35|EDEADLK|Resource deadlock would occur|
|36|ENAMETOOLONG|File name too long|
|37|ENOLCK|No record locks available|
|38|ENOSYS|Function not implemented|
|39|ENOTEMPTY|Directory not empty|
|40|ELOOP|Too many symbolic links encountered|
|42|ENOMSG|No message of desired type|
|43|EIDRM|Identifier removed|
|44|ECHRNG|Channel number out of range|
|45|EL2NSYNC|Level 2 not synchronized|
|46|EL3HLT|Level 3 halted|
|47|EL3RST|Level 3 reset|
|48|ELNRNG|Link number out of range|
|49|EUNATCH|Protocol driver not attached|
|50|ENOCSI|No CSI structure available|
|51|EL2HLT|Level 2 halted|
|52|EBADE|Invalid exchange|
|53|EBADR|Invalid request descriptor|
|54|EXFULL|Exchange full|
|55|ENOANO|No anode|
|56|EBADRQC|Invalid request code|
|57|EBADSLT|Invalid slot|
|59|EBFONT|Bad font file format|
|60|ENOSTR|Device not a stream|
|61|ENODATA|No data available|
|62|ETIME|Timer expired|
|63|ENOSR|Out of streams resources|
|64|ENONET|Machine is not on the network|
|65|ENOPKG|Package not installed|
|66|EREMOTE|Object is remote|
|67|ENOLINK|Link has been severed|
|68|EADV|Advertise error|
|69|ESRMNT|Srmount error|
|70|ECOMM|Communication error on send|
|71|EPROTO|Protocol error|
|72|EMULTIHOP|Multihop attempted|
|73|EDOTDOT|RFS specific error|
|74|EBADMSG|Not a data message|
|75|EOVERFLOW|Value too large for defined data type|
|76|ENOTUNIQ|Name not unique on network|
|77|EBADFD|File descriptor in bad state|
|78|EREMCHG|Remote address changed|
|79|ELIBACC|Can not access a needed shared library|
|80|ELIBBAD|Accessing a corrupted shared library|
|81|ELIBSCN|.lib section in a.out corrupted|
|82|ELIBMAX|Attempting to link in too many shared libraries|
|83|ELIBEXEC|Cannot exec a shared library directly|
|84|EILSEQ|Illegal byte sequence|
|85|ERESTART|Interrupted system call should be restarted|
|86|ESTRPIPE|Streams pipe error|
|87|EUSERS|Too many users|
|88|ENOTSOCK|Socket operation on non-socket|
|89|EDESTADDRREQ|Destination address required|
|90|EMSGSIZE|Message too long|
|91|EPROTOTYPE|Protocol wrong type for socket|
|92|ENOPROTOOPT|Protocol not available|
|93|EPROTONOSUPPORT|Protocol not supported|
|94|ESOCKTNOSUPPORT|Socket type not supported|
|95|EOPNOTSUPP|Operation not supported on transport endpoint|
|96|EPFNOSUPPORT|Protocol family not supported|
|97|EAFNOSUPPORT|Address family not supported by protocol|
|98|EADDRINUSE|Address already in use|
|99|EADDRNOTAVAIL|Cannot assign requested address|
|100|ENETDOWN|Network is down|
|101|ENETUNREACH|Network is unreachable|
|102|ENETRESET|Network dropped connection because of reset|
|103|ECONNABORTED|Software caused connection abort|
|104|ECONNRESET|Connection reset by peer|
|105|ENOBUFS|No buffer space available|
|106|EISCONN|Transport endpoint is already connected|
|107|ENOTCONN|Transport endpoint is not connected|
|108|ESHUTDOWN|Cannot send after transport endpoint shutdown|
|109|ETOOMANYREFS|Too many references: cannot splice|
|110|ETIMEDOUT|Connection timed out|
|111|ECONNREFUSED|Connection refused|
|112|EHOSTDOWN|Host is down|
|113|EHOSTUNREACH|No route to host|
|114|EALREADY|Operation already in progress|
|115|EINPROGRESS|Operation now in progress|
|116|ESTALE|Stale NFS file handle|
|117|EUCLEAN|Structure needs cleaning|
|118|ENOTNAM|Not a XENIX named type file|
|119|ENAVAIL|No XENIX semaphores available|
|120|EISNAM|Is a named type file|
|121|EREMOTEIO|Remote I/O error|
|122|EDQUOT|Quota exceeded|
|123|ENOMEDIUM|No medium found|
|124|EMEDIUMTYPE|Wrong medium type|
|125|ECANCELED|Operation Canceled|
|126|ENOKEY|Required key not available|
|127|EKEYEXPIRED|Key has expired|
|128|EKEYREVOKED|Key has been revoked|
|129|EKEYREJECTED|Key was rejected by service|
|130|EOWNERDEAD|Owner died|
|131|ENOTRECOVERABLE|State not recoverable|

On non-windows, you can also use this little program to figure out what your operating system might be using for error numbers and their associated meanings.

> int strerror_r(int errnum, char *buf, size_t buflen);

The following example uses this function.  On non-windows systems, this is the systems interface (XSI) compliant form of the appropriate function.  We could use the GNU version, but in this case, we are ignoring the return value regardless.  Given the issue created by a huge pool of numbers, versus some sort of identifier, this is fundamentally left over for compatibility.  Arbitrary magic numbers are bad and lead to serious ambiguity.  Future programmers should come up with some other model to modernise this mess.  

[Return to Index](#index)

#### Example 19: Sample Dump of Windows Error Numbers
Basic program that with output.

**Note** - This uses syntax and functions we have not covered yet.

1. using a typedef statement for type aliasing
2. accessing functions from the C standard library
3. converting an error number to its string equivalent
4. setting up a for loop to iterate over a finite set of values
5. printf formatting of strings and other information
6. setup of function main

```C
#include <stdio.h>                             // Provides access to standard I/O functions.
#include <string.h>                            // Provides access to standard string functions.

typedef int s32;

s32 main() {                                   // Start of the program.
  s32 buffLen = 1000;                          // Set a variable for the maximum length of
                                               // the char buffer to hold the string.
  for (s32 err = 0; err < 133; ++err)  {       // Build a loop to go from 0 to 133 counting
                                               // by 1. This will iterate over the range of
                                               // known assigned values across different
                                               // non-windows operating systems. The number
                                               // of errors is not standard, so depending on
                                               // your given operating system, it may explode.
                                               
    char buff[1000] = {};                      // Establish a buffer of characters with 1001
                                               // elements. This sets up an array. We invoke
                                               // the {} initialisation to zero the array. This
                                               // will in theory each time through the loop
                                               // fill the array which will hold a string with
                                               // '\0' null terminators. As long as we never
                                               // write more than 1000 bytes of data to the
                                               // array, there will always be a null terminating
                                               // byte for string processing or output.  Most,
                                               // if not all string functions, at least in the
                                               // C standard libraries require null termination
                                               // to be present.

    strerror_r(err,buff,buffLen);              // As mentioned we are using the XSI version
                                               // of the strerror_r function and ignoring
                                               // the return value.

                                               // err  - is the errno supplied by the loop
                                               // buff - is the char buff array to hold the string
                                               // bufflen - holds the max size of the char buff array

    printf("[errno = %03d][%s]\n", err, buff); // Builds the string output to display the errno
                                               // and the converted string equivalent of the
                                               // errno.  This format information with printf
                                               // will be dissected immediately following this
                                               // example.
  }

  return 0;                                    // Inform the operating system we exited cleanly.
}
```

Windows on the other hand has a very complex error numbering system.  You can read up more on it [here](https://learn.microsoft.com/en-us/windows/win32/debug/system-error-codes?redirectedfrom=MSDN#system-error-codes).  Neither of these operating systems share overlapping error numbers, except for 0, which is STATUS_OK or even ERROR_SUCCESS. C functions in the standard library, or otherwise generally use 0 to specify a lack of error.  There are always exceptions to this.  The functions based on alloc(), such as malloc(), calloc(), etc., return NULL (0) on a failure to allocate, and any other number to specify a pointer to the address of the allocated memory.  You are strongly advised to look up functions for your given standard library or referenced header modules of code you are using in your program.

On Linux/UNIX/FreeBSD you always have the good old MAN Pages.  For example [malloc()](https://man7.org/linux/man-pages/man3/malloc.3.html).  GCC pretty much follows the general POSIX compliance, so any MAN Page that references the POSIX standard should be valid.  Mingw does not attempt to maintain POSIX compliance on Windows, as this is not always possible.  Microsoft is not a POSIX-compliant operating system, and anyone who has coded with WinSocks over POSIX Sockets is well aware of the nightmare created by custom solutions provided inside Windows. As mentioned, trust the manual for the best advice on how to use and what to expect when you use anything from a standard library, or any 3rd party library for that matter.

There is also the matter of how errors are returned, the janky nature of system vs. non-system error handling, and the various methods of returning errors and where to find them.  Examples in this book follow system style code using the return for status and function arguments for returning or updating values.  

[Return to Index](#index)

### Printf

The beast of Console Output.  For formatted output, printf is your friend.  Remembering how to use it will make it your enemy.  If you scour the internet for printf cheat sheets, you'll find them in abundance. This is by far one of the most complex features contained in the C Standard Library.  Let's start with the prototype. 

> int printf(const char *format, ...)

There is a complex concept shown in this prototype -- the ellipsis [...]. All you need to remember is the ellipsis means, can take an arbitrary list of comma-separated arguments.  The char format string on the other hand is going to require some deeper discussion.

The format string argument in printf can be a straight char string but with Format Specifiers peppered throughout it.  Let's dissect the associated Data Types and their Format Specifiers. 

### Format Specifier & Special Characters Table

```
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
```

<sup>**NOTE [1]:** *Type char is unique from all other types. It has three unique states -- char, signed char, and unsigned char.  None of these equate to each other.  According to the C Standard char will be guaranteed to hold a single character/byte worth of data.  Function arguments that expect char will complain if you try to pass a signed or unsigned variant instead.*</sup>

<sup>**NOTE [2]:** *If the hex specifier is used for any unsigned integer Data Type it will be cast to an unsigned char and only display one byte of information.  The hex and octal specifiers can only be used to represent integer Data Types.  Floating Point Data Types require special pointer twiddling.  You will get strange output trying to use either of the conversion specifiers otherwise.*</sup>

Alright, now we have a table of nightmares and the basic knowledge to start tackling some basic output.  Let's write some examples.  The following examples will expand on topics missed above and cover a more complete set of examples based on all topics we have covered so far. 

[Return to Index](#index)

#### EOF and Error Constants

### C Output & Expansion on Type Examples

#### Example 20: Using puts
Basic program with output.

1. using a portion of the C Standard Library to access Functions for output
2. setup of function main

```C
#include <stdio.h>                             // Provides access to standard I/O functions.

typedef int s32;

s32 main() {                                   // Main program entry.
  puts("Hello World!");                        // Displays Hello World! to the console.

  return 0;                                    // Return status successful.
}
```

[Return to Index](#index)

#### Example 21: Using Format Specifiers with printf
Basic program with output.

1. showing various typedef assignments
2. general variable use
3. using a portion of the C Standard Library to access Functions for output
4. showing how to use various format specifiers
5. examples of how they can be used
6. setup of function main

```C
#include <stdio.h>

// Create typedef associations.

typedef char               c8;
typedef signed char        s8;
typedef unsigned char      u8;
typedef short              s16;
typedef unsigned short     u16;
typedef int                s32;
typedef unsigned int       u32;
typedef long long          s64;
typedef unsigned long long u64;
typedef float              f32;
typedef double             f64;
typedef long double        f80;

s32 main() {
  // Variable declarations follow.
  // [data type] [name] = [initial value];
  
  c8   cFoo  = 'A';  
  s8   sFoo  = -120;  
  u8   uFoo  = 128;
  s16  sBar  = -27543;  
  u16  uBar  = 98;
  s32  sBaz  = -1676352;
  u32  uBaz  = 'C';
  s64  sThud = -38131823283338;
  u64  uThud = 14710131619;
  f32  flob  = 0.125;
  f64  corge = 3.141592653589793;
  f80  plugh = 9.6169031625e+35;

  // Shows using the appropriate format specifier for any given type.
  // C has a special use cases for %c so that integer based 8-bit,
  // 16-bit, and 32-bit data types can all be used to represent chars.
  // This can be seen from the output information below. 64-bit
  // integer types are incapable of storing char information.

  printf("cFoo  [%%c]   = %c\n", cFoo);        
  printf("uFoo  [%%c]   = %c\n", uFoo);
  printf("sFoo  [%%c]   = %c\n", sFoo);
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
```

**Generated output:**
```
cFoo  [%c]   = A
uFoo  [%c]   = �
sFoo  [%c]   = �
cFoo  [%d]   = 65
sFoo  [%d]   = -120
uFoo  [%d]   = 128
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
```

Based on the above we can see some janky output showing up with %c specifier formatting for uFoo, sFoo and sBaz.  This has generated symbols based on where it falls in the Code Page, then determined it could not render the character.

### ASCII, Code Pages and UTF Standards

We are going to tangent for a short bit and explain the nightmare that is actually behind those glyphs and why they might be rendered that way.

ASCII (American Standard Code for Information Interchange) is a 7-bit character encoding standard initially designed for telegraph communication originally established in 1963. It assigns unique numerical codes to represent 128 characters, primarily English letters and symbols. The initial version, known as ASCII-63, was published by the American Standards Association (ASA), later renamed the American National Standards Institute (ANSI). This early version laid the foundation for subsequent revisions, with ASCII being officially standardized in 1967. The most widely recognized version is ASCII-67, which became the basis for the ASCII standard that has been widely adopted in computing and communication systems.

ASCII code pages are variations or extensions of the ASCII standard tailored to specific languages or regions, incorporating additional characters not covered in the basic ASCII set. For instance, the ISO-8859 series extends ASCII for Western European languages by utilizing 8 bits per character. Code Pages are more broadly used to define character encodings, encompassing ASCII, ISO-8859, and Unicode.

Unicode has largely superseded many ASCII code pages by providing a unified standard for characters from all languages. UTF-8, a variable-width character encoding under Unicode, has gained popularity for its ability to efficiently represent global text with one to four bytes per character.

**NOTE** - This table shows only printable characters.

|Character|Hex|Decimal|Character|Hex|Decimal|Character|Hex|Decimal
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Space|20|32|@|40|64|`|60|96|
|!|21|33|A|41|65|a|61|97|
|"|22|34|B|42|66|b|62|98|
|#|23|35|C|43|67|c|63|99|
|$|24|36|D|44|68|d|64|100|
|%|25|37|E|45|69|e|65|101|
|&|26|38|F|46|70|f|66|102|
|'|27|39|G|47|71|g|67|103|
|(|28|40|H|48|72|h|68|104|
|)|29|41|I|49|73|i|69|105|
|*|2A|42|J|4A|74|j|6A|106|
|+|2B|43|K|4B|75|k|6B|107|
|,|2C|44|L|4C|76|l|6C|108|
|_|2D|45|M|4D|77|m|6D|109|
|.|2E|46|N|4E|78|n|6E|110|
|/|2F|47|O|4F|79|o|6F|111|
|0|30|48|P|50|80|p|70|112|
|1|31|49|Q|51|81|q|71|113|
|2|32|50|R|52|82|r|72|114|
|3|33|51|S|53|83|s|73|115|
|4|34|52|T|54|84|t|74|116|
|5|35|53|U|55|85|u|75|117|
|6|36|54|V|56|86|v|76|118|
|7|37|55|W|57|87|w|77|119|
|8|38|56|X|58|88|x|78|120|
|9|39|57|Y|59|89|y|79|121|
|:|3A|58|Z|5A|90|z|7A|122|
|;|3B|59|[|5B|91|{|7B|123|
|<|3C|60| \\ |5C|92| \| |7C|124|
|=|3D|61|]|5D|93|}|7D|125|
|>|3E|62|^|5E|94|~|7E|126|
|?|3F|63|-|5F|95|Delete|7F|127|

Code Page standards can get a little janky.  As mentioned, ASCII-67, is only 7-bits, the 8-bit characters are generally what the different ASCII standards change.  Since a single byte can hold 0 to 255, means the characters from 128 to 255 make up another section of potential displayable characters.  There are vendor, language, regional, and operating system specific Code Pages. There are [hundreds of them](https://en.wikipedia.org/wiki/Code_page). The variations in the UTF standards from 8-bit, 16-bit, or 32-bit Code Pages add to the complexity.  Microsoft Windows terminals are notorious for butchering output, defaulting to legacy support, outright refusing to display proper conversions from other standard Code Pages. Linux, Unix and Mac OS are not without their quirks either, however, they tend to offer moderately to better support dealing with conversion, display, and formatting of UTF-encoded information.

Conversion from the following Code Pages is dysfunctional at best while executing under Microsoft Windows terminals.

```
57002: Devanagari (Hindi, Marathi, Sanskrit, Konkani)
57003: Bengali
57004: Tamil
57005: Telugu
57006: Assamese
57007: Odia
57008: Kannada
57009: Malayalam
57010: Gujarati
57011: Punjabi (Gurmukhi)
```

The difficulty with converting to and from certain fonts and glyphs is exacerbated when digging through pages like [this](https://ltrc.iiit.ac.in/showfile.php?filename=downloads/FC-1.0/fc.html).  It outlines the various converters and methods required to create search engines, display, and processing or modify information to and from the Devanagari family of languages.  This will also be a problem with the different dialects of Chinese and Arabic.  Code Page 936 for instance is a simplified and heavily modified version of the Chinese language.  It provides minimal support.

Compiling and executing the following code under Microsoft Power Shell or Command Prompt should display the Chinese characters embedded in the syntax correctly.

#### Example 22: Using printf with Chinese Characters


```C
#include <stdio.h>

int main() {
    // UTF-8 encoded string
    const char utf8String[] = "Hello, 你好";

    // Display UTF-8 string
    printf("UTF-8 String: %s\n", utf8String);

    return 0;
}
```

**Generated Output:**
```
UTF-8 String: Hello, 你好
```

If you get mojibake, or characters that look like "Σ╜áσÑ╜", this requires executing a command to change the Code Page.  You can use the following command in the terminal.

> chcp 936

Then rerun the application in the terminal. This is chaos.  They have generally been trying to standardise glyph and font associations since the dawn of computing. As you can tell, it has largely not gone well.  Most modern web browsers are more than capable of displaying proper UTF encodings.  Generally, it is the responsibility of the programmer to ensure the application sets and returns the terminal, or execution environment as needed for proper formatting.  This can be a daunting task.

Jonathan Blow remarked while writing The Witness about how difficult it is to address the spacing of non-standard glyphs visually.  You can see issues in this [image](http://the-witness.net/news/wp-content/uploads/2015/12/Arabic.png).  Glyphs are too close and too far away creating gaps and oddities in spacing.  This requires serious fancy coding.  Modern terminals cannot properly render this information either.  Given programmers have been working on this problem since 1967, at least at the time of this writing, we are pushing almost 6 decades of problem-solving, and still do not have a pretty way to do this.  Any programmer who has scoured the internet for solutions to display, work with, and manage libraries in UTF has several things going for them...

1. A very large savings fund in their swear jar.
2. More grey hair.
3. Years off their life from stress.
4. Unanswered questions on how to execute a solution effectively for all written languages.

Unreal Engine 4 cannot properly render Arabic.  It lacks a robust enough rendering pipeline.  This is seriously not an easy problem to solve.  I am merely raising this issue here, as current and future generations of programmers still need to address this problem.  Unreal Engine 5 is attempting to work on the problem, but from this [video](https://www.youtube.com/watch?v=Ha9LIA90EyY) you can see there are still several issues with the glyph rendering pipeline.

There are ways to get around some of the issues, but most of those require using managed, or custom engines, and avoiding terminals of any kind.  Other problems are created by Raster, Vector, True-Type, and Open-Type fonts.  Let us get back to the basics.  We will explore possible ways to solve this later when we get to methods of rendering.

[Return to Index](#index)

#### Example 23: Using printf with %x
Basic program with output.

1. showing various typedef assignments
2. general variable use
3. using a portion of the C Standard Library to access Functions for output
4. showing how to use %x \[hex specifier\]
5. examples of how it can be used
6. setup of function main.

```C
#include <stdio.h>

//create typedef associations
typedef char               c8;
typedef signed char        s8;
typedef unsigned char      u8;
typedef short              s16;
typedef unsigned short     u16;
typedef int                s32;
typedef unsigned int       u32;
typedef long long          s64;
typedef unsigned long long u64;

s32 main() {
  // Variable declarations follow.
  // [data type] [name] = [initial value];
  
  c8  cFoo  = 'A';
  s8  sFoo  = -120;
  u8  uFoo  = 128;
  s16 sBar  = -27543;
  u16 uBar  = 98;
  s32 sBaz  = -1676352;
  u32 uBaz  = 'C';
  s64 sThud = -38131823283338;
  u64 uThud = 14710131619;

  // Keep in mind the hex specifier only works with integer data types and
  // is only showing the lowercase specifier in this case. You can use %X
  // and %LX if you prefer upper case. Remember you need the %Lx or %LX for
  // 64-bit. All other unsigned integer data types will be cast to unsigned
  // char, as you'll see in the output.

  printf("cFoo  [%%x] = %x\n", cFoo);      // Will cast to a single unsigned char byte.
  printf("sFoo  [%%x] = %x\n", sFoo);      // Will cast to an unsigned int showing 4 bytes of information.
  printf("uFoo  [%%x] = %x\n", uFoo);      // Will cast to a single unsigned char byte.
  printf("sBar  [%%x] = %x\n", sBar);      // Will cast to an unsigned int showing 4 bytes of information.
  printf("uBar  [%%x] = %x\n", uBar);      // Will cast to a single unsigned char byte.
  printf("sBaz  [%%x] = %x\n", sBaz);      // Will cast to an unsigned int showing 4 bytes of information.
  printf("uBaz  [%%x] = %x\n", uBaz);      // Will cast to a single unsigned char byte.
  printf("sThud [%%Lx] = %Lx\n", sThud);   // Will cast to an unsigned long long showing 8 bytes of information.
  printf("uThud [%%Lx] = %Lx\n", uThud);   // Will cast to an unsigned long long showing up to 8 bytes of information.

  return 0;
}
```

**Generated Output:**
```
cFoo  [%x] = 41
sFoo  [%x] = ffffff88
uFoo  [%x] = 80
sBar  [%x] = ffff9469
uBar  [%x] = 62
sBaz  [%x] = ffe66bc0
uBaz  [%x] = 43
sThud [%Lx] = ffffdd51be37f376
uThud [%Lx] = 36ccacba3
```

[Return to Index](#index)

#### Example 24: Displaying Union Members

Basic program with output.

1. showing various typedef assignments
2. assigning union members
3. using an array inside a union
4. using a portion of the C Standard Library to access Functions for output
5. showing how to display Union Members.
6. setup of function main.

```
#include <stdio.h>

typedef unsigned int s32;

typedef union {
  // Because unionTest has an anonymous struct inside it, the member array will
  // automatically map each element to a member in order of the anonymous struct.
  
  struct {
    s32 state;
    s32 active;
    s32 amount;
    s32 frameNo;
  };
  
  // The array member allows you to open up different and versatile options for
  // assigning and referencing information inside the union. This is especially
  // useful for later if you require to iterate over information.

  // Unfortunately this method has a major drawback if the order of the members
  // in anonymous struct change. Be mindful in your future programs this will
  // affect initialisation and assignment throughout your program. It also creates
  // a quasi-magic number state concerning the index offsets of each mapped element.  

  // array[0] maps to state
  // array[1] maps to active
  // array[2] maps to amount
  // array[3] maps to frameNo

  // Generally you should reference the members by name in your program unless you
  // are iterating. This solves the need for enumerators and other naming conventions
  // allowing you to access information stored at specific positions inside the array
  // by name with just a little bit of extra coding.

  s32 array[4];
} unionTest;

s32 main() {
  // Though, we could initialise the union with the array member, this method
  // creates some obfuscation with the assignment.
  
  // unionTest foo = {
  //   .array = {
  //     1, 2, 3, 4
  //   }
  // };
  
  // The correct method to initialise this union would be as follows. This removes
  // the obfuscation of assignment and ensures if the order changes in the anonymous
  // struct the initialisation will still be valid reducing refactoring issues in
  // larger programs.
    
  unionTest foo = {
    .state   = 1,
    .active  = 2,
    .amount  = 3,
    .frameNo = 4
  };
    
  printf("%d %d %d %d\n", foo.array[0], foo.array[1], foo.array[2], foo.array[3]);
  printf("%d %d %d %d", foo.state, foo.active, foo.amount, foo.frameNo);
  return 0;
}
```

**General Output:**
```
1 2 3 4
1 2 3 4
```

[Return to Index](#index)

### Format Modifiers

Now that we have a general handle on the basics of printf, there is another part we need to discuss that deals with modifiers that can be applied to format specifiers.  These modifiers control justification, the number of decimal places to show with floats, and control padding with characters of the output.  We will need to create another table for some of the rules, and then generate some examples.

```
Modified Format Specifier

%[A][B][C][D]

[A] Use - to format for left justification.
[B] Specify a padding character here. [1]
[C] Use ?.? where ? is an integer value.
    First position is the total width of output. 
    Second position after the . is how many decimal positions. [2]
[D] Use your normal format specifier here.

[A][B][C] are optional.
```
<sup>**NOTE [1]** Not valid with the _char_ type.  Only Padding is valid with this Format Specifier.</sup>

<sup>**NOTE [2]** Only valid with Floating Point Data Types</sup>

Confused? It's always easier to look at code to figure out how things work.  We'll need to break down every specifier with enough context to fully explore the last remaining pieces of _printf_.

[Return to Index](#index)

### C Output & Format Modification Examples

#### Example 24: Left Justification with printf
Basic program with output.

1. showing various typedef assignments
2. general variable use
3. using a portion of the C Standard Library to access Functions for output
4. showing how to use various output specifiers
5. examples of how they can be used to left justify data
6. setup of function main.

```C
#include <stdio.h>

typedef char          s8;
typedef unsigned char u8;
typedef int           s32;

s32 main() {
  s8 sFoo  = -120;
  s8 sBar  = 7;
  s8 sBaz  = 115;
  s8 sThud = 'A';

  u8 uFoo  = 0;
  u8 uBar  = 17;
  u8 uBaz  = 247;
  u8 uThud = 'A';
  
  // Use - left justify.
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
```

**Generated Output:**
```
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
```

[Return to Index](#index)

#### Example 25: Zero Padding with printf
Basic program with output.

1. showing various typedef assignments
2. general variable use
3. using a portion of the C Standard Library to access Functions for output
4. showing how to use various output specifiers
5. examples of how they can be used to zero pad and justify data
6. setup of function main

```C
#include <stdio.h>

typedef char          s8;
typedef unsigned char u8;
typedef int           s32;

s32 main() {
  s8 sFoo  = -120;
  s8 sBar  = 7;
  s8 sBaz  = 115;
  s8 sThud = 'A';

  u8 uFoo  = 0;
  u8 uBar  = 17;
  u8 uBaz  = 247;
  u8 uThud = 'A';
  
  // Shows padding a value with leading zeroes and
  // using width-based padding.
 
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
```

**Generated Output:**
```
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
```

[Return to Index](#index)

#### Example 26: Side-Effects using printf %x and signed numbers
Basic program with output.

1. showing various typedef assignments
2. general variable use
3. using a portion of the C Standard Library to access Functions for output
4. examples showing side-effects that can occur using certain specifiers with various data
5. setup of function main.

```C
#include <stdio.h>

typedef char          c8;
typedef signed char   s8;
typedef unsigned char u8;
typedef int           s32;

s32 main() {
  c8 Thud = 'A';
  
  s8 sFoo  = -120;
  s8 sBar  = 7;
  s8 sBaz  = 115;
  
  u8 uFoo  = 0;
  u8 uBar  = 17;
  u8 uBaz  = 247;
    
  // Shows padding a value with leading zeroes with the use of width padding.
  // sFoo is going to cause value rolling. Since %x defaults to the width
  // needed, you should notice an unexpected side-effect when the compiler
  // casts the s8 to s32 for the -120. Be cautious of displaying negative
  // values using the %x specfier.
  
  printf("thud  [%%05x] %05x\n\n", thud);
  
  printf("sFoo  [%%05x] %05x\n", sFoo);
  printf("sBar  [%%05x] %05x\n", sBar);
  printf("sBaz  [%%05x] %05x\n\n", sBaz);
  
  printf("uFoo  [%%05x] %05x\n", uFoo);
  printf("uBar  [%%05x] %05x\n", uBar);
  printf("uBaz  [%%05x] %05x\n\n", uBaz);
  
  // No real difference, it just switched to uppercase.

  printf("thud  [%%05X] %05X\n\n", thud);
  
  printf("sFoo  [%%05X] %05X\n", sFoo);
  printf("sBar  [%%05X] %05X\n", sBar);
  printf("sBaz  [%%05X] %05X\n\n", sBaz);
  
  printf("uFoo  [%%05X] %05X\n", uFoo);
  printf("uBar  [%%05X] %05X\n", uBar);
  printf("uBaz  [%%05X] %05X\n\n", uBaz);

  return 0;
}
```

**Generated Output:**
```
thud  [%05x] 00041

sFoo  [%05x] ffffff88
sBar  [%05x] 00007
sBaz  [%05x] 00073

uFoo  [%05x] 00000
uBar  [%05x] 00011
uBaz  [%05x] 000f7

thud  [%05X] 00041

sFoo  [%05X] FFFFFF88
sBar  [%05X] 00007
sBaz  [%05X] 00073

uFoo  [%05X] 00000
uBar  [%05X] 00011
uBaz  [%05X] 000F7
```

[Return to Index](#index)

#### Example 27: Formating Floating Point Types with printf
Basic program with output.

1. showing various typedef assignments
2. general variable use
3. using a portion of the C Standard Library to access Functions for output
4. changing the character and width padding for floating point data
5. using the literal suffix F to cast assigned values as 32-bit floats
6. setup of function main.

```C
#include <stdio.h>

typedef int   s32;
typedef float f32;

s32 main() {
  // This shows the introduction of estimation errors
  // with floating point numbers. You will see output
  // that often does not match what you are assigning
  // to your variables. There are inaccuracy problems
  // with all Floating Point Types. Not all values
  // can be accurately represented with a standard bit
  // pattern like the Integer Types.  This leads to
  // all Floating Point Types being represented with
  // approximations of their true value.
  
  // All floating point values assigned during declare
  // are assumed to be double. You must use the F
  // modifier on values to cast them to float instead.
  
  f32 f32Foo = 10.2F;
  f32 f32Bar = 0.123456F;
  f32 f32Baz = 123456.0123456F;
  f32 f32Thud = 3.14159265358979323846F;

  // Left justify and notice the truncation on output.
  
  printf("f32Foo  [%%-f] %-f\n", f32Foo);
  printf("f32Bar  [%%-f] %-f\n", f32Bar);
  printf("f32Baz  [%%-f] %-f\n", f32Baz);
  printf("f32Thud [%%-f] %-f\n\n", f32Thud);

  // This forces more decimal places because we have
  // higher precision with more decimal places. You
  // can see errors are being introduced when extending
  // more decimal places.
  
  printf("f32Foo  [%%-.10f] %-.10f\n", f32Foo);
  printf("f32Bar  [%%-.10f] %-.10f\n", f32Bar);
  printf("f32Baz  [%%-.10f] %-.10f\n", f32Baz);
  printf("f32Thud [%%-.10f] %-.10f\n\n", f32Thud);

  // An additional series of formatting.  Note that
  // the left alignment cancels any left padding
  // values used in the format.
  
  printf("f32Foo  [%%-9.2f] %-9.2f\n", f32Foo);
  printf("f32Bar  [%%-9.2f] %-9.2f\n", f32Bar);
  printf("f32Baz  [%%-9.2f] %-9.2f\n", f32Baz);
  printf("f32Thud [%%-9.2f] %-9.2f\n\n", f32Thud);

  // General alignment formatting.
  
  printf("f32Foo  [%%9.2f] %9.2f\n", f32Foo);
  printf("f32Bar  [%%9.2f] %9.2f\n", f32Bar);
  printf("f32Baz  [%%9.2f] %9.2f\n", f32Baz);
  printf("f32Thud [%%9.2f] %9.2f\n", f32Thud);

  return 0;
}
```

**General Output:**
```
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
```

[Return to Index](#index)

#### Example 28: Formating double Floating Point Types with printf
Basic program with output.

1. showing various typedef assignments
2. general variable use
3. using a portion of the C Standard Library to access Functions for output
4. changing the character and width padding for floating point data
5. literals are double by default when dealing with Floating Point Types
6. setup of function main.

```C
#include <stdio.h>

typedef int    s32;
typedef double f64;

s32 main() {
  // This shows the introduction of estimation errors
  // with floating point numbers. You will see output
  // that often does not match what you are assigning
  // to your variables. There are inaccuracy problems
  // with all Floating Point Types. Not all values
  // can be accurately represented with a standard bit
  // pattern like the Integer Types.  This leads to
  // all Floating Point Types being represented with
  // approximations of their true value.
  
  f64 f64Foo = 10.2;
  f64 f64Bar = 0.123456;
  f64 f64Baz = 123456.0123456;
  f64 f64Thud = 3.14159265358979323846;

  // Left justify and notice the truncation on output.
  
  printf("f64Foo  [%%-lf] %-lf\n", f64Foo);
  printf("f64Bar  [%%-lf] %-lf\n", f64Bar);
  printf("f64Baz  [%%-lf] %-lf\n", f64Baz);
  printf("f64Thud [%%-lf] %-lf\n\n", f64Thud);

  // This forces more decimal places because we have
  // higher precision with more decimal places. You
  // can see errors are being introduced when extending
  // more decimal places.
  
  printf("f64Foo  [%%-.25lf] %-.25lf\n", f64Foo);
  printf("f64Bar  [%%-.25lf] %-.25lf\n", f64Bar);
  printf("f64Baz  [%%-.25lf] %-.25lf\n", f64Baz);
  printf("f64Thud [%%-.25lf] %-.25lf\n\n", f64Thud);

  // An additional series of formatting.  Note that
  // the left alignment cancels any left padding
  // values used in the format.
  
  printf("f64Foo  [%%-9.2lf] %-9.2lf\n", f64Foo);
  printf("f64Bar  [%%-9.2lf] %-9.2lf\n", f64Bar);
  printf("f64Baz  [%%-9.2lf] %-9.2lf\n", f64Baz);
  printf("f64Thud [%%-9.2lf] %-9.2lf\n\n", f64Thud);

  // General alignment formatting.
  
  printf("f64Foo  [%%9.2lf] %9.2lf\n", f64Foo);
  printf("f64Bar  [%%9.2lf] %9.2lf\n", f64Bar);
  printf("f64Baz  [%%9.2lf] %9.2lf\n", f64Baz);
  printf("f64Thud [%%9.2lf] %9.2lf\n", f64Thud);

  return 0;
}
```

**General Output:**
```
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
```

[Return to Index](#index)

#### Example 29: Formating long double Floating Point Types with printf
Basic program with output.

1. showing various typedef assignments
2. using the literal suffix L to cast assigned values as 80-bit floats
3. using a portion of the C Standard Library to access Functions for output
4. exploring E-Notation format specifiers
5. changing the character and width padding for floating point data
6. setup of function main.

```C
#include <stdio.h>

typedef int         s32;
typedef long double f80;

s32 main() {
  // Despite more precision, you will never get true representations of
  // your values.  All we are going to gain is some extra digits of
  // accuracy.  This is the unfortunate consequence of Floating Point
  // Data Types.

  f80 f80Foo = 10.2L;
  f80 f80Bar = 0.123456L;
  f80 f80Baz = 123456.0123456L;
  f80 f80Thud = 3.14159265358979323846L;

  // Left justify and observe the truncation on output.
  
  printf("f80Foo  [%%-Lf] %-Lf\n", f80Foo);
  printf("f80Bar  [%%-Lf] %-Lf\n", f80Bar);
  printf("f80Baz  [%%-Lf] %-Lf\n", f80Baz);
  printf("f80Thud [%%-Lf] %-Lf\n\n", f80Thud);

  // This forces more decimal places because we have
  // higher precision with more decimal places. You
  // can see errors are being introduced when extending
  // more decimal places.
  
  printf("f80Foo  [%%-.40Lf] %-.40Lf\n", f80Foo);
  printf("f80Bar  [%%-.40Lf] %-.40Lf\n", f80Bar);
  printf("f80Baz  [%%-.40Lf] %-.40Lf\n", f80Baz);
  printf("f80Thud [%%-.40Lf] %-.40Lf\n\n", f80Thud);

  // An additional series of formatting.  Note that
  // the left alignment cancels any left padding
  // values used in the format.
  
  printf("f80Foo  [%%-9.2Lf] %-9.2Lf\n", f80Foo);
  printf("f80Bar  [%%-9.2Lf] %-9.2Lf\n", f80Bar);
  printf("f80Baz  [%%-9.2Lf] %-9.2Lf\n", f80Baz);
  printf("f80Thud [%%-9.2Lf] %-9.2Lf\n\n", f80Thud);

  // General alignment formatting.
  
  printf("f80Foo  [%%9.2Lf] %9.2Lf\n", f80Foo);
  printf("f80Bar  [%%9.2Lf] %9.2Lf\n", f80Bar);
  printf("f80Baz  [%%9.2Lf] %9.2Lf\n", f80Baz);
  printf("f80Thud [%%9.2Lf] %9.2Lf\n\n", f80Thud);

  // E Notation will ignore the left padding since there
  // will only ever be a single digit to the left of the
  // floating point.
  
  printf("f80Foo  [%%.3Le] %.6Le\n", f80Foo);
  printf("f80Bar  [%%.3Le] %.6Le\n", f80Bar);
  printf("f80Baz  [%%.3Le] %.6Le\n", f80Baz);
  printf("f80Thud [%%.3Le] %.6Le\n", f80Thud);

  return 0;
}
```

**General Output:**
```
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
```
[Return to Index](#index)

## Part 3: Pointer Basics

As mentioned previously, Pointer Types are a troubling subject for C programmers no matter their experience.  We'll cover some scenarios with code and hopefully demystify some of the confusion surrounding them.

Example 30: Introduction to Pointers and Addressing
Basic program with output.

1. declaration of a struct and union to explore memory addressing
2. introduction to pointers to things
3. establishing a basic function pointer definition
4. using %p formatting to display the address of things
5. display the address of each member for the struct and union
6. setup of function main.

```
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
  // Every variable, pointer, structure, union, member, and function
  // are assigned an addressable location in memory on the computer.

  s32 u32Foo = 12;

  // Pointers store these addresses for lookup. The * in front of a
  // variable denotes this is a pointer the & means get the address
  // of something.

  s32 *u32Bar = &u32Foo;

  TFCP thud = {};
  TFCP *qux = &thud;

  TEHS garply = {};
  TEHS *grault = &garply;

  // We have only covered function main. To create a function pointer
  // to main we must match the return type of int, give the function
  // pointer a name (*name), and an argument list referenced by the
  // following (). Then you can assign the address of function main
  // to the function prototype as matched the prototype.
  
  s32 (*fp)() = &main;

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
```

**General Output:**
```
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
```

NOTE: Every time you execute this program these memory addresses will be different.  This is only the current snapshot of the memory layout at the time the example was executed.  You should expect things to move around in memory.  The references that follow are based on this current snapshot for the machine it was executed on.

[Return to Index](#index)

### Deeper Dissection of Example 30: 

If we remember back when we were looking at our bitwidths and byte requirements of individual Types there are some things we can glean from what we are seeing in this output.  Let's dissect this a little to figure out what the computer this is running on has done and things to be mindful of.

```
s32 u32Foo = 12;
s32 *u32Bar = &u32Foo;

Address of  u32Foo = 0x7ffd0424af08
Address at *u32Bar = 0x7ffd0424af08
Address of *u32Bar = 0x7ffd0424af00
```

In the code we declared u32Foo before \*u32Bar, yet in memory based on the addresses we can see \*u32Bar was placed in memory before u32Foo.  How can we determine this from those addresses?  Like any representation of a number, those hex-formatted addresses are still read from right to left.  We can split them up into byte pairs and then determine the most significant portion of what we are looking at.

```
Byte Pairs
01 02 03 04 05 06
7f|fd|04|24|af|08 u32Foo appears 8 bytes after *u32Bar in memory
7f|fd|04|24|af|00 *u32Bar is 8 bytes

//we are only looking at byte pair 06 when determining the 8 bytes used [08 - 00 = 8]
//or by looking at the addresses as a whole [7ffd0424af08 - 7ffd0424af00 = 8]
```

The next problem we should address is the out-of-order problem in memory.  Any time you declare something in C it can cause Memory Fragmentation depending on how it was declared.  Memory Fragmentation will be discussed in more detail when we begin dealing with malloc and free a bit later.  Individual variables in this case clearly show the order they are declared in does not guarantee that same order in memory.  We can also learn from looking at this, that any declared pointer is using 8 bytes of memory.  So pointers are 64-bit based on the architecture this code was compiled on.  This can change depending on your system configuration, and compiler setup also.  Let's look at another feature of the addresses shown.

```
Address of  u32Foo = 0x7ffd0424af08
Address at *u32Bar = 0x7ffd0424af08
Address of *u32Bar = 0x7ffd0424af00
```

When we say pointers store an address of something, we can clearly see this is true.  The address stored at \*u32Bar is the same address of the variable u32Foo.  This should be the case because we assigned the address of u32Foo to \*u32Bar when we declared \*u32Bar.  By using the amperstand \[&] we fetched the address of u32Foo.  We will see this replicates in the same way when we deal with the other pieces of this example.

Let's take a look at how the struct TFCP addresses and pointers are laid out in memory.  

```
Address of    thud = 0x7ffd0424aef0
        thud.flob  = 0x7ffd0424aef0
        thud.corge = 0x7ffd0424aef4
        thud.plugh = 0x7ffd0424aef8
Address at    *qux = 0x7ffd0424aef0
Address of    *qux = 0x7ffd0424aee8
```

We can see from the addresses of u32Foo and \*u32Bar and the addresses here that we have moved to a different region of memory. The struct TFCP appears before those other variables.  Byte pair 05 changed from AF \[175\] to AE \[174\], where 175 > 174, so we know we are in an early region of memory. Since memory on any computer is addressed in bytes, smaller memory addresses are always going to be in a region of memory before the next largest memory address. This is what allows us to look at memory layouts and figure out where something is, and based on things around it, and approximate how many bytes it may be consuming. In the case of struct TFCP we'll also be able to figure something else out. The members thud.flob, thud.corge, thud.plugh, and byte pair 06 show they are laid out in order by fours. This makes sense because they are declared as s32 which was type defined from an int, which we know uses 4 bytes of memory. Also, remember that \*qux holds the address pointing to the start of struct TFCP, but the address of \*qux, like any pointer is going to have its own address as well. 

NOTE:  The C Standard guarantees that any struct declaration will always have member layout in the order it is declared unless you use an alternate alignment modifier on the struct.

```
If unions give you problems visualising, this is another way of thinking about how memory is laid out. We'll look closer at the union TEHS.

Address of  garply = 0x7ffd0424aee0
    garply.eggs    = 0x7ffd0424aee0
    garply.ham     = 0x7ffd0424aee4
    garply.spam[0] = 0x7ffd0424aee0
    garply.spam[1] = 0x7ffd0424aee4
Address at *grault = 0x7ffd0424aee0
Address of *grault = 0x7ffe28e72538
```

Unions as we know, can share regions of memory with other members depending on how the union was declared.

```
typedef union {
  struct {
    s32 eggs;
    s32 ham;
  };
  s32 spam[2];
} TEHS;
```

The union declares a group of member variables inside a nameless struct. Then we declare spam as an array with 2 elements as another member. Logically, we should be able to conclude from this declaration layout that eggs will map to spam\[0] and ham will map to spam\[1]. By looking at the addresses of each of the member variables we can see this is the case. This is the basic fundamental concept of a pointer. When you update a union member, the associated union member will also update. A pointer will do the same thing since it points to the address of something. We can also conclude that anything we do with the pointer has the potential to update what the pointer is pointing to. Before we explore this, we'll finish reviewing the \*fp declaration.

```
Address of  main() = 0x400540
Address at     *fp = 0x400540
Address of     *fp = 0x7ffd0424aed0
```

As mentioned, everything pretty much has an address, right down to the compiled byte code encoded internally to the executable. Function main() is no different. There are cases where this will prove to be very useful. Like all pointers \*fp points to something and has its own address. Pointers can point to other pointers. Unlike other pointers though, a function pointer can call/invoke the function it is pointing to. This will be covered later when we go over functions.  We must finish going over pointers.

Example 2: 
Basic program with output.

showing how to declare variables, structures, unions, an introduction to pointers, locate the address of things, and declaring function main. 

Basic program with output, showing how we can use pointers to map different data types, output showing that when we update the pointer the thing we point to also updates, and a method for determining what Endianness your current hardware is using, and layout for function main.

```
#include <stdio.h>

typedef unsigned char u8;
typedef int s32;
typedef unsigned long long u64;

s32 main() {
  // We are creating a simple byte map of a u64
  // integer so we need at least 8 bytes. Then we
  // intialise all u8 [byte] elements in the map
  // to 0.
  
  u8 u64Map[8] = {};
  
  // Setup an unsigned 64-bit integer, filling
  // every bit with something so we create 8 bytes
  // of data. Don't forget we need the ULL to
  // signify our hex value is 64-bit.
  
  u64 foo = 0xffeeddccbbaa9988ULL;
  
  // Remember arrays are pointers. This allows us to
  // use the name u64map, as we saw above, because it
  // stores the start address of u64map[0]. We don't
  // need to do this. It's merely for reinforcement
  // of a concept.
  
  u8 *bar = u64Map;
  
  // This creates an unsigned char pointer and casts
  // our unsigned 64-bit integer to an unsigned 8-bit
  // char pointer.
  
  u8 *fuzz = (u8 *)&foo;
  
  // We need to remember to use %Lx for 64-bit
  // integers.
  
  printf("foo = %Lx\n\n", foo);
  
  // Once we map our pointers, just like mentioned when
  // discussing pointers, by updating any elements of the
  // pointer bar, we are updating u64map elements. We can
  // see the side effects of this below.
  
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
```

**General Output:**
```
foo = ffeeddccbbaa9988

bar[0] u64Map[0] = 88 88
bar[1] u64Map[1] = 99 99
bar[2] u64Map[2] = aa aa
bar[3] u64Map[3] = bb bb
bar[4] u64Map[4] = cc cc
bar[5] u64Map[5] = dd dd
bar[6] u64Map[6] = ee ee
bar[7] u64Map[7] = ff ff
```

Looking at the way the array mapped byte by byte from the integer we can see it mapped backwards.  Depending on the architecture you are using this may change.  What we see here is an effect caused by Little-Endianness.  If we were on a Big-Endianness architecture the array would be mapped from left to right and would appear as it is displayed.  Here's a basic table on architecture endianness.

### Endianness

```
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
```

The problem with this might not be apparent immediately, however, if we store data in binary formats, pass information across networks, then store data in some other way that may do encoding with a certain Endianness, things are going get a little wonky.  It's unlikely you'll be coding on a majority of these platforms, but a career in software engineering might have you crossing paths with older systems still in the wild running legacy code, or with newer systems that have unique eco-systems.  Migrating data from one architecture to another will require having some understanding of how integer data will be stored.  Modern coding does create some problems specifically when creating games, especially ones that are multi-player crossing platforms.  If you support phones, you're going to be running into ARM based architecture which is BI-Endianness and will be determined by the operating system installed on the device.  While your server may be running on some other architecture that will be different Endianness.  Regardless, you are encouraged to research the hardware and operating system limitations so you can determine how things are stored in memory.

Here's another table showing Endianness by Operating Systems.

```
Endianness

Little                  Big                     Determined by Hardware
----------------------------------------------------------------------
Android                 Apple Mac OS            Linux
Apple OSX               HP UNIX                 Solaris
iOS                     Amiga OS                IBM Linux
Microsoft Windows
HP VMS
OS/2
```

Generally most architectures and operating systems are moving exclusively towards Little-Endianness.  Neither of the above tables should be considered complete or exhaustive, but are provided merely to show examples that there are different circumstances where you should be considering how you think about data storage on your given platform.  There are cases where networking protocols, specifically TCP come to mind that are Big-Endian.  For the time being we'll cover a few more basics of pointers showing how we might take Endianness into consideration.  Future examples of code will generally ignore Endianess unless specifically required.

## Part 5: Using sizeof()

As we expand into our understanding of pointers and memory, there is a useful Operator called sizeof.  It is calculated during compile time and will result in the compiler returning a value that will be representative of the size in bytes of the things you requested the sizeof.

#### Example 1:
Basic program with output, showing the use of sizeof, a brief introduction to padding and working with addresses, an introduction malloc, also free, and the basic use of main.

```
#include <stdio.h>
#include <stdlib.h>

typedef char               s8;
typedef unsigned char      u8;
typedef short              s16;
typedef unsigned short     u16;
typedef int                s32;
typedef unsigned int       u32;
typedef long long          s64;
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
  
  // sizeof is a compiler implemented unary operator that is used
  // to determine the size of whatever you stick in between the
  // parenthesis.  The size of what you are requesting will be
  // returned in bytes as a size_t [typed] value.
  
  // size_t is generally just a typedef inside the C standard
  // libraries included with GCC.  Depending on the system,
  // size_t may be 16, 32 or 64-bits in size.  
  
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
  
  // You will see mallocs often delcared like this. This is
  // required by C++. It was common to cast C malloc calls
  // like this in case your C code was compiled with a C++
  // compiler.  However, this generally doesn't make sense
  // anymore as C++ has moved so far from C they are just
  // not compatible enough anymore to matter.
  //
  // Since malloc returns a void pointer. It is considered
  // untyped memory and can be cast to any pointer it is
  // assigned to. By using malloc you are requesting
  // memory from the operating system.
  //
  // sizeof(TFooBar) will ask for 112 bytes of memory.
  //
  // This creates a single allocated instance of struct
  // TFooBar. Memory should be better managed than single
  // instances of things. Memory management has changed
  // alot. Taking into consideration things like cache
  // lines and memory fragmentation will force developing
  // newer models of managing memory.
  //
  // TFooBar *fooBar = (TFooBar *)malloc(sizeof(TFooBar));
  //
  // malloc calls should follow the standard C form to
  // prevent silly C++ coders from thinking they can use
  // this code with a C++ compiler.
  
  TFooBar *foobar = malloc(sizeof(TFooBar));
    
  // Finally, don't forget to call free on the pointer.
  // Generally the operating system will cleanup memory
  // on exit from the program, however, we are tidy
  // conscientious C programmers and will free all
  // malloced memory before exit.  
  
  free(fooBar);
  
  return 0;
}
```

**General Output:**
```
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
```

Each of the values displayed by the example program above, short of the addresses, is measured in bytes.  If we recall back in the early part of this text, we had a table of Integer and Float Types and their associated byte/bit widths.  All the base types in this case should show the corresponding matching byte requirements.  The exception in this case is the f80 which was mapped from long double.  It shows 16 bytes being used, however, it should be known that only 10 bytes will ever be used according to the C Standard for precision.  Some padding has taken place.  This is a good way to figure out what your bit widths will be for given types in the future if you're unsure of your given limitations on a given platform, architecture, or under a given operating system.

The other section of the output deals with the sizeof a struct and its members.  As shown in this case, the C Standard dictates that the compiler for memory alignment can add padding.  In this case the 100 elements that we declared for TFooBar.foo, created a gap filled by padding of 4 bytes.  Despite the struct having a sizeof 112, the members of TFooBar only actually use 108 bytes in total.  These are useful ways to find out how your struct is using memory.  For now, your understanding is unlikely to take advantage of what all this means, but this is strictly for exposure to how you can determine these things later when you need to.

Finally, we have the malloc and free that didn't have any side-effects or purpose in this code, other than to show why we needed to cover sizeof.  We will be covering proper use of malloc and free later.  For now we're going to tie up our basics on pointers and continue to Functions.  Pointers were needed in basic understanding so we could continue to the next part of our programming understanding.

## Part 6: Introduction to Functions

It has taken a bit longer than normal to get to this part, but one of the purposes of the order of this text is to make sure we are not covering anything without first knowing or having exposure to the base concepts prior.  Functions are a very useful feature of programming.  They allow splitting up code, creating reusable sections, or just in general grouping code by purpose for what it does.  Let's dive into some examples and cover some basics.

#### Example 1:
Basic program with output, showing how to create and call a Function from main.

```
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
```

**General Output:**
```
Hello World!
```

#### Example 2:

Let's carry on with another basic program without, showing how to create and call a function with arguments from main. (edited)

```
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
```

**General Output:**
```
value of bar = 1
value of bar = -2344
value of bar = 90
```

#### Example 3:

Hopefully now based on what we've covered prior, this should be relatively easy so far.  Here's another basic program with output, showing how to create and call a function with multiple arguments from main.

```
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
```

**General Output:**
```
value of bar  = 1
value of thud = 0.030000

value of bar  = -2344
value of thud = 1.245670

value of bar  = 90
value of thud = -7.410000
```

#### Example 4:

What happens if we want to use a Function to update a value? This is called passing by reference.  Normally arguments are merely copied, or passed by value, and disposed once the Function has finished and exits.  There are ways we can create persistent states.  Over the next few examples we explore this.

Basic program with output, showing how to pass a value by reference to a function that uses a pointer from main. (edited)

```
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
```

**General Output:**
```
value of bar  = 2
value of thud = 2.000000
```

What happens if we have a lot of arguments that we need to pass to a function? In terms of much of the Linux or Windows Application Programming Interface [LAPI or WAPI] we will be running into Functions that require a lot of parameters.  There isn't much we can do when it comes to how things have been written in the past, but we can be mindful of how future programmers deal with these sorts of problems.  For instance if we look at XCreateWindow from Linux, we will see something that looks like this for a rough outline of a prototype.  


> Window XCreateWindow(display, parent, x, y, width, height, border_width, depth, 
>                      class, visual, valuemask, attributes)

Many of the LAPI and WAPI Functions have very wide argument lists.  When you begin to look at what many of these are defined as, you will begin to get a little overwhelmed.

```
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
```

This idea was to create flexibility, but created a cost to programmers with additional complexity.  Without typedefs, we create wide declarations, coupled with custom Type Definitions such as Display, Window, Visual and XSetWindowAttributes.  Each of these will add overhead to the program that must be used and populated.   While also remembering the order and what each argument is expecting.  This may have been acceptable in the past, not so sure we should be designing things this way for the preservation of sanity to next generations of programmers.  This a primary reason C has a bad reputation, generated from this type of low level nightmare.

Another problem we face when looking at C code is when it was written.  Types did not always have the same bit widths as they do now.  Up to this point we have made the assumption that we are running on modern 64-bit platforms.  When the LAPI code was written that includes XCreateWindow, int would have been 16-bit \[2 bytes], and long would have been 32-bit \[4 bytes].  Upto this point we have been using typedef statements and creating aliases such as s32 or s64.  One of the reasons this is done is to make it clear what bit width we are coding against for a given Type.  Depending on the age of C code, you must take these things into consideration.  Since architecture in the future is likely to expand from 64-bit to 128-bit, or higher we should be mindful that like in the past, Types are going to change bit widths. 

Generally in this case it would be preferable to write something in this way.  Basic general program that will not run showing a model of how this might be addressed in the future.

NOTE: WILL NOT COMPILE.  This is only for reference.

```
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
```

Over the next few examples we'll cover initialising things inside Functions and passing them back.  We have not really handled return values yet, so those will also be explored.  Depending on what we are dealing with, there are different methods for each to consider.

NOTE: As we start switching over to using stdint.h for portability there are a few caveats to remember.  There is no equivalent to char or _wchar_t_ for fixed bit width types.  The _uint8_t_ and _int8_t_ have no overlap as char is not signed or unsigned and is treated as a third unique 8-bit type.  Type _uint16_t_ and _int16_t_ also do not overlap with _wchar_t_.

Basic program with output showing how to initialise a structure from a function, return it, printing out some of its member values, and setting up function main.

```
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
```

**General Output:**
```
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
```

Basic program with output showing how to use malloc to initialise memory from a function, assigning some values within context of the allocated memory, using free, and setup of function main.

```
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
```

**General Output:**
```
buzz 0x7ffd5b98c5d8
 r   0x7ffd5b98c5d8
*r   (nil)
 r   0x7ffd5b98c5d8
*r   0x2091690
bazz.foo = 23
bazz.bar = A
buzz.foo = 23
buzz.bar = A
```

A little more dissection of the address outputs will hopefully clarify what is actually happening when we are calling function newTFBAlt and passing pointer buzz to it.  Since pointer buzz is merely type TFB and a single pointer, meaning we do not have an array, in the case of TFB \*buzz[] and we do not have any pointers to pointers in the case of TFB \*\*buzz, we must satisfy the conversion to the \*\*r argument expected in the call.  The easiest way to do this is to pass the address of buzz.  In this case the address of the pointer buzz is shown to be 0x7ffd5b98c5d8.   When we enter the function the address of \*\*r becomes the address of buzz as shown by the address matching.  When we call the malloc it will request a section of memory that also has an address that we need to store.  That address passed back from the malloc is shown to be 0x2091690.  The reason we need to use (\*r) in this case is because \*\*r points to the address of &buzz, and we know when we take \*ptr we are looking at the value of what is stored there, giving us access to the pointer being pointed to.  The first pointer is buzz, and it points to the address returned by the malloc.

Here is an example with output showing the side-effects of the above and further explaining why this fails to further reinforce the concept above.

```
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
```

**General Output:**
```
&buzz 0x7ffe55680c10
 buzz (nil)
&r 0x7ffe55680be8
 r (nil)
&r 0x7ffe55680be8
 r 0x9f1670
```

The second example shows how we would normally pass a pointer to a function so we can update its value.  We can see the address of buzz is 0x7ffe55680c10.  Things get janky when we enter the function and realise that the address of the pointer argument \*r is 0x7ffe55680be8.  This is because pointers are passed by value, and so a copy of the pointer was made locally and placed on the stack.  Even though we are passing by reference, we are only able to update the value stored at what buzz is pointing to.  In this case we can see the (nil) value stored there, however, it is stored at a different address.  Where buzz and \*r exist in memory does not match.  So the address of the pointer can never truly be updated, because we do not actually have the true address of the thing we are trying to assign it to.  This is why we need the second indirection with a pointer to a pointer.  We must be able to preserve the address in the by reference call, not just the value being passed by reference.

The \*r creates a pointer to an address of a value.  What we need for preservation of the malloc address is a pointer to an address of a pointer to an address of a value.  That is where the \*\*r comes in.   Because we must pass the address of something as the argument not just what the pointer is pointing to we have changed the conditions of the by reference call.   The second indirection gives us the ability to access address.

If we think about how we normally would deal with a variable, then a pointer, and accessing the value at that pointer.

```
int buzz = 0;
int *bar = &buzz;
printf("buzz  %i\n", *bar);
```

We know buzz has an address on the stack and holds a value of 0.  Assigning the address of buzz to bar allows us to access the value of buzz through a dereference to the value stored at what bar is pointing to by using \*bar.

```
int buzz = 0;
int *foo = &buzz;
int **bar = &foo;
printf("foo   %i\n", *foo);
printf("buzz  %i\n", **bar);
```

Double indirection of pointers above is what we are actually requiring.  We need a point that can point to the value it holds.  When we call the function with _newTFBAlt(&buzz);_ we end up with something like this.

```
TFB *buzz = NULL;
TFB **r = &buzz;
*r = (TFB *)malloc(sizeof(TFB));
```

In this case we have built the proper chain for the persistence of the address passed back by the malloc.  When passing things as arguments to functions we need to be mindful of where things are pointing, and what they are pointing to.  This is a perfect example of pointer complexity that creates immense confusion.  Just remember, if you must malloc something inside a function and pass it by reference as an argument, always add one more level of pointer indirection than what the pointer has been declared as.  Make sure you pass the address, and use the proper level of dereferencing.

NOTE: The last thing we need to remember, POINTERS ARE ALWAYS PASSED BY VALUE.  You will never be able to update an address of a pointer because of this.  To accomplish this, ADD ONE EXTRA LEVEL OF INDIRECTION SO THE POINTER CAN BE PASSED BY REFERENCE.  When calling the function, PASS THE ADDRESS OF THE POINTER YOU ARE TRYING TO UPDATE.   Then make sure you DEREFERENCE ONE LEVEL OF INDIRECTION TO ACCESS THE ORIGINAL POINTER.  Everything should be okay. (edited)
If you fail to remember this, you will end up seeing a lot of this...

> Segmantation fault

One last group of examples will cover passing arrays and their special treatment within C.  Arrays are treated as pointers when referred to by their name and always passed by reference.

Basic program with output showing how to pass an array, setup a function call, use sizeof for basic length calculations, and general setup of function main. (edited)

```
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
```

**General Output:**
```
len = 13
[Hello World!]
post foo [hello world!]
```

Passing multi-dimensional arrays is little more complicated, you just need to remember that the last dimension needs to match element bounds of the array you will be passing.  Other than that, no fancy pointer stuffs required.  Here's another basic program with output showing how to use strlen, pass a multi-dimensional array to a function, modify a some things in it verifying the by reference state of arrays, and the general setup of function main.

```
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
```

**General Output:**
```
len = 60
bar[0] len = 12 [Hello World!]
bar[1] len =  6 [Foobar]
bar[2] len = 17 [Multi-Dimensional]

post foo
thud[0] [hello world!]
thud[1] [foobar]
thud[2] [multi-dimensional]
```

Basic program with output showing how to pass data between functions, allocate a buffer, introduction to memset, and general setup of function main. (edited)

```
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
```

**General Output:**
```
len = 12 address = 0x7fff7842e370 [aaaaaaaaaaaa]
```

So far we have only been dealing with one form of function main.  The following example will be the last one we explore for Function use.  There are times when we need to pass information to a program when it starts.  This is done with command line arguments.  The next basic example has output, and shows how to reconfigure main to accept arguments from the command line.

```
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
```

**Command Line Input:**
```
./main foo bar
```

**General Output:**
```
number of arguments received = 3
args[0] = [./main]
args[1] = [foo]
args[2] = [bar]
```

Now that we have hit some the basic building blocks of coding, in order to move forward there is a need to understand some other basic concepts around Operators and Expression building.  In order to move into branching and flow control these topics need to be addressed first.

## Part 7: Operators and Expressions

In C, there are several types of Operators to explore.  They fall into groups, such as Mathematical, Unary, Relational, Logical, Bitwise, Assignment, Comma and Conditional.  Each group of Operators are used to create Expressions.  Expressions in C are made up of Variables, Functions and Operators. These are important for various flow and branch control uses in our programs.  Let's begin with exploring what we can do with these and how they will relate to future examples and programs we will be exploring in the book. 

### Mathematical Operators

Useful for basic maths operations.

```
Operator     Description
------------------------------------------------
  +          Adds
  -          Subtracts
  *          Multiplies
  /          Divides
  %          Modulus [Remainder from Division]
```

#### Example

Basic program with ouput showing how to use each of the Mathematical Operators, and general setup of function main.

```
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
```

**General Output:**
```
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
```

The only Operator that tends to cause confusion is the Modulus Operator [%].  Let's dissect the output from the arrays that we built help in groupX, groupY and groupZ.

```
s32 groupX[] = {0 % 2, 1 % 2, 2 % 2, 3 % 2, 4 % 2, 5 % 2, 6 % 2};

Modulus [groupX]
-----------------------
       0 1 2 3 4 5 6
result 0 1 0 1 0 1 0
```

Modulus works by producing the remainder result from a division operation.

```
        R
0 / 2 = 0
1 / 2 = 1
2 / 2 = 0
3 / 2 = 1
4 / 2 = 0
5 / 2 = 1
6 / 2 = 0
```

This is useful if you need to restrict numbers to a range.  It will create a repeating cycle that has great utility.  We'll see the modulus operator in use when we get to writing some of our Containers, specifically in the Queue example.

### Roll Over and Value Side-Effects

One other thing we need to address is the side-effect of the following Expression.  

```
u64 sBaz  = 6754 - 8653;
```

This causes what is known as Roll Over.  Since u64 is declared as _typedef uint64_t u64_, this is an unsigned type.  The value of 8653 is greater than 6754, so when the subtraction operation takes place, C does not complain at all, it just rolls over to 18446744073709551615 which is the unsigned long long maximum value and continues the subtraction beyond 0.  This is why we see a strange value when we look at the result for sBaz.  

```
baz  = 18446744073709549717
```

There are no exceptions, or any warnings of any kind, where other languages would throw something like an out of bounds error.  C does not guarantee errors of this nature.  If you see strange results, you have likely caused Roll Over, some other form of Undefined Behaviour or you caused a segmantation fault and crashed your program.

```
#include <stdio.h>
#include <stdint.h>

typedef int32_t  s32;
typedef int64_t  s64;
typedef uint64_t u64;

int main() {
  // If we take the unsigned long long max value and subtract
  // the roll over value that was output above we see another
  // peculiarty that is likely to trip up programmers.
  
  u64 uFoo = 18446744073709551615ULL - 18446744073709549717ULL;

  printf("%Lu\n", foo);

  // The original expression above that showed the roll over
  u64 uBaz  = 6754 - 8653;

  printf("%Lu\n", sBaz);

  // Taking a signed long long and doing the same is going to
  // create a value that has a signed part and be larger by
  // one than the rolled over expression using the ULL values.
  
  s64 sFoo = 6754 - 8653;

  printf("%Ld\n", sBaz);
  
  return 0;
}
```

**Generated Output:**
```
1898
18446744073709549717
-1899
```

We need to consider the range of values to understand what is actually taking place here.

> u64 uBaz  = 6754 - 8653;

Then ranges to consider are the 0 to 6754.  We need to remember there is 0 here.  Before the Roll Over takes place, we cross the 0 accounting for our off by one error.

> u64 uFoo = 18446744073709551615ULL - 18446744073709549717ULL;

When we takes the above expression, this has already crossed the 0 to 6754 and then subtracted 1898 from the _unsigned long long_ max which gives us the Roll Over value of 18446744073709549717.  This is a problem if you forget during the ranges we actually had 6755 numbers that were passed through during the subtraction before we took the remaining value of 1898 from the _unsigned long long_ max.  

You can see the values do not match on the expressions with uFoo and sFoo when you try to account for what is going on.

> 1898 and abs(-1899) are off by one

NOTE: Do not forget to account for these types of annomalies when you're trying to figure out what happened.  This is another area where off by one errors are most likely to occur.  Side-effects of Roll Over can be problematic if you're trying to maths out what is happening.  Remember to always take into account signed and unsigned minimum and maximums. When in doubt, always write code that tests what the compiler is doing on your given hardware.  It is the only way to get an authoritive answer.

> "The handling of overflow, divide check, and other exceptions in expression evaluation is not defined by the language.  Most existing implementations of C ignore overflow in evaluation of signed integral expressions and assignments, but this behavior is not guaranteed."
> K&R (Second Edition) [Page 200]

This has not been updated in the C standard for the most part either.  This is compiler dependent.  Below we'll look at some of things you might encounter as side-effects.  Here is a basic program with output showing features of Roll Over, and setup of function main.

```
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
```

**Compiler Output:**
```
main.c: In function ‘main’:
main.c:16:18: warning: division by zero [-Wdiv-by-zero]
   printf("%d", 3 / 0);
                  ^
```

**General Output:**
```
-32768 - 1 = 32767
32767 + 1 = -32768
Floating point exception (core dumped)
```

C is going to require you get to know your compiler.  As you can see from the warning, it is complaining about the divide by zero.  Which is Undefined Behaviour so every compiler is going to do something different.  In the case of GCC, it causes a segmentation fault (core dump) in relation to floating point maths.  We can clearly see the Roll Over taking place on the minimum and maximum values.  Here's another basic program with output showing other features of Roll Over, and setup of function main.

```
#include <stdio.h>
#include <stdint.h>
#include <limits.h>

typedef int32_t s32;
typedef uint16_t u16;

s32 main() {
  // All unsigned types default to 0 as their minimum.
  u16 foo = 0; 
  u16 bar = UINT16_MAX;
  
  printf("%u - 1 = %u\n", foo, (u16)(foo - 1));
  printf("%u + 1 = %u\n", bar, (u16)(bar + 1));

  return 0;
}
```

**General Output:**
```
0 - 1 = 65535
65535 + 1 = 0
```

NOTE: If you are encountering oddities, check your maths, range, limits, bounds, operators, casts, and heed warnings from the compiler.  This did not cover Not A Number [NAN], Infinity [INF] and other things that go wrong with Floating Point Types.  You are encouraged to explore with code what your specific compiler is going to do in relation to what you are expecting.  They may not always agree.  If things are still exploding, hit godbolt, dump debug values, worst case ask for help if you're just lost. 

### Unary Operators

These Operators come in a few different contexts.

```
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
```

As always, let's write some code.  We'll gloss over &, \*, and sizeof operator, since we already covered those in the Pointer Basics section.  Here is a basic program with output covering the - and + Unary Operators, and setup of function main. (edited)

```
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
```

**General Output:**
```
(s32)+foo  [-23]
bar        [-12]
+bar       [-12]
-bar       [12]
bar = -bar [12]
```

In conclusion, the +  prefix operator, at least in the context of GCC, is useless.  This may differ based on the compiler you are using.  Next we will look at the decrement and increment operators. (edited)

```
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
```

**General Output:**
```
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
```

We do need to address some common problems programmers get into with the increment and decrement operators.  They are famous for creating undefined behaviour and other oddities.  Let's explore a few of them.  Keep in mind in each of these scenarios it will be impossible to predict what the compiler is going to do, or the sequence modern processes may execute it.  The following are guaranteed to produce unpredictable results and should be avoided.  The following examples may produce the results you are expecting, but this is not going to be consistently predictable everywhere.

#### Examples of Undefined Behaviour from Increment or Decrement Side-Effects

```
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  s32 foo = 42;
  s32 bar = 8;

  printf("%i\n\n", ++foo + bar++ - ++bar);

  return 0;
}
```

**Compiler Output [compiled with -Wall]:**
```
main.c: In function ‘main’:
main.c:10:31: warning: operation on ‘bar’ may be undefined [-Wsequence-point]
   printf("%i\n\n", ++foo + bar++ - ++bar);
```

**General Output:**
```
41
```

```
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  s32 foo = 42;
  foo = ++foo;

  printf("%i\n\n", foo);

  return 0;
}
```

**Compiler Output [compiled with -Wall]:**
```
main.c: In function ‘main’:
main.c:8:7: warning: operation on ‘foo’ may be undefined [-Wsequence-point]
   foo = ++foo;
```

**General Output:**
```
43
```

```
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
```

**Compiler Output [compiled with -Wall]:**
```
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
```

**General Output:**
```
foo[0] = 0
foo[1] = 1
foo[2] = 2
```

```
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
```

**Compiler Output [compiled with -Wall]:**
```
main.c: In function ‘main’:
main.c:17:27: warning: operation on ‘foo’ may be undefined [-Wsequence-point]
   undefinedBehaviour(foo, ++foo);
```

**General Output:**
```
4
```

NOTE: When you introduce a side-effect of this nature, you cause UNDEFINED BEHAVIOUR across your entire program.  The moment you lose the ability to predict what your code will do, and why, you can no longer guarantee stability, or expected results.  This is very bad.  There are other scenarios created with pointers and other things.  We'll explore those when we get to strings.  Do not use or reference something and modify it in the same expression, this will guarantee potential for unwanted side-effects.

Now that we have tackled some of the problems and basics of the increment and decrement operator lets go over some examples of the ! operator.

Basic program with output showing how the ! operator works, and setup of function main.

```
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
```

**General Output:**
```
bar  0
baz  0
thud 0
fuzz 0
foo  1
```

We are going to skip over the & and sizeof operators as we've covered them prior and end this group with looking at the unary bitwise operator ~.

Basic program with output showing how the ~ operator works, and general setup of function main.  

```
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
```

**General Output:**
```
Base
foo [%c]  (
foo [%hhu] 40     //bit wise 00101000

Post 1st ~
foo [%c]  �
foo [%hhu] 215    //bit wise 11010111   

Post 2nd ~
foo [%c]  (
foo [%hhu] 40     //bit wise 00101000
```

Useful when you want to completely flip the bits of something you're working on.  When you're dealing with a scenario that needs flags, or attributes, or some other things inside an API, you'll find bitwise operators to be very useful. (edited)

### Relational Operators

Below is a table of each of the operators in this group.  As always, we'll keep it brief, then dive into some code.

```
Operator   Definition
--------------------------------------
   >       greater than
   <       less than
  >=       greater than or equal to
  <=       less than or equal to
  ==       tests for equality
  !=       tests for inequality
```

Basic program with output showing how each of the Relational Operators works, a trick on how to use an array and some strings to fetch values based on tests conditions, and setup of function main.

```
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
```

**General Output:**
```
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
```

### Logical Operators

This is a short group, we have already explored one with the Unary Operator !.  The other two logical operators are as follows.

```
Operator   Description
  &&       logical and
  ||       logical or
   !       logical not
```

Basic program with output showing how the Logical Operators function, and general setup of function main.

```
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
```

**General Output:**
```
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
```

As mentioned we're skipping the ! operator and moving on to the next group of operators.

### Bitwise Operators

C provides six bit manipulation operators and are listed in the table below. These are most effectively used on Integer Types. Floating Point Types do not store their data in linear order and are made up of parts.

NOTE: Performing bitwise operations on Float Types without a strong understanding of their parts will cause Undefined Behaviour.

```
Operator  Description
--------------------------------------
   &      bitwise and
   |      bitwise or
   ^      bitwise exclusive or (xor)
   <<     bitwise left shift
   >>     bitwuse right shift 
   ~      bitwise not
```

Basic program with output showing the use of operators right shift, and, or, xor, and the general setup of function main. (edited)

```
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
```

**General Output:**
```
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
```

Basic program with output showing how the left and right shift operators function, and general setup of function main.

```
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
```

**General Output:**
```
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
```

### Assignment Operators

There are a total of 11 operators of this kind available in C.  Now that we have covered the a majority of the basic operators the table below will show how they can be combined with the simple equals Assignment Operator to form Compound Assignment Operators.

```
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
```

Basic program with output showing the general use of the Assignment Operators, several functions, and as always setup of function main.

```
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
```

**General Output:**
```
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
```

### Comma Operator

We are only going to introduce it here.  No code showing its use will follow at this point.  This is technically an Unary Operator, and has very limited places where it can be used.  Its primary use is for sequencing side-effects from other expressions or operations.  Like many other operators in C, it shares multiple purposes generating confusion if context is not understood.  The , operator in this context should not be confused with compound variable declarations, function arguments lists, structure or union layouts.  Our use of the , operator will be limited in the future to for loops, macros, auxiliary computations of expressions in the same statement, complex returns, and avoiding the need for blocks and associated { block } braces.  Since we have not covered most of the parts of where this operator is used, it will be detailed later in each of the future programming concepts as we go over them.

### Conditional Operator

Sometimes we need to make assignments based on a decision. This is our introductory branching operator.  It's made up a few parts that must follow a specific order.  It uses an evaluation expression and has two state expressions representing true and false based on the logical result of the expression.  You will also hear the Conditional Operator commonly referred to as a ternary if statement.

Basic program with output showing an example using the ternary if statement, and the general setup of function main. (edited)

```
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
```

**General Output:**
```
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
```

Basic program with output showing some other examples of ternary if statements, and general setup of function main.

```
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
```

**General Output:**
```
12
```

NOTE: Many online tutorials, books, and manuals may show something along the lines of this as a possible correct usage of ternary if statements.  

```
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
```

This is not a good usage.  Basic example with output showing a better form of the above, and general setup of function main.

```
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
```

**General Output:**
```
if
```

### Zero is not always Zero

More problems are created when we consider the case of 0 with floating point numbers.  Like every other value stored inside a Floating Point Type, it will be approximated.  This creates confusion when programmers assign a value of 0 and then attempt to do comparisons only to find out 0 does not equal 0 in the world of approximated values.  We'll explore this more when we get to if branching.  This will require a basic understand of using epsilon ranges to approximate a value realtionship to 0.

#### Example 1: Issues with Floating Point Types and Approximations
Basic program with output.

1. showing various typedef assignments
2. using a portion of the C Standard Library to access Functions for output
3. exploring floating point representations of zero
4. testing certain floating point states of approximations
5. changing the character and width padding for floating point data
6. setup of function main.

```
#include <stdio.h>
#include <stdlib.h>
#include <stdint.h>

typedef int         s32;
typedef float       f32;
typedef double      f64;
typedef long double f80;

s32 main(int argc, char *argv[]) {
  f32 fltZero = 0.0F;
  f64 dblZero = 0.0;
  f80 decZero = 0.0L;
  
  printf("%.10f\n", fltZero);
  printf("%.10lf\n", dblZero);
  printf("%.10Lf\n", decZero);

  fltZero = 10.0F - 10.0F;
  dblZero = 10.0 - 10.0;
  decZero = 10.0L - 10.0L;

  printf("%.10f\n", fltZero);
  printf("%.10lf\n", dblZero);
  printf("%.10Lf\n", decZero);

  printf("(0.0 == 0.0F) %s\n", (0.0 == 0.0F) ? "True" : "False");

  // Everything looks fine to this point. Floating Point Types
  // do have a representation of 0.0 that can be exactly
  // stored. Things start to get janky when you start mixing
  // Floating Point Types. The more you work with floating point
  // data you are going to run into these results that produce
  // approximations of zero. It is generally not considered
  // good form to perform equality checks against various forms
  // of floating point data.

  printf("(23.45f == 23.45) %s\n", (23.45F == 23.45) ? "true" : "false");
  
  dblZero = 23.45F - 23.45;
  printf("%.10lf\n", dblZero);
 
  return 0;
}
```

**General Output**
```
0.0000000000
0.0000000000
0.0000000000
0.0000000000
0.0000000000
0.0000000000
(0.0 == 0.0F) True
(23.42f == 23.42) false
0.0000000763
```

[Return to Index](#index)

## Part 8: Introduction to Branching

In C there are if, else if and else statements that can make up one for of branching.  There is also the switch, case, default statements.  The ternary if operator we just went over, return statements we have been we have been using in every one of our examples to this point, and a few others that are generally discouraged from use.  These include continue, goto, labels and the function exit.  One last but slightly deficient important statement is break.  Limitations of the break statement in some contexts requires we drag the goto statement into use.

As we have already found, there are many cases where an if statement is easily replaced.  But we will start with it, and show alternatives if available. (edited)

Basic example with output showing how to create the simplest form of a branching setup for loop control using goto, and a general setup of function main.

NOTE: This is merely for example, and not a general recommendation on how to solve a problem.  It's a prime example of the mess goto statements make.  Early programming languages did not have the syntax to create better models of code structure.  The Assembly Language uses a lower model of this style of label and goto statement, except they are a series of instructional codes based on jmp which is short for jump. (edited)

```
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
```

**General Output:**
```
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
```

Now that we know what not to do with a basic introduction to the goto and labels, we'll move on to more basic examples of using if, else if, and else, and general setup of function main.

```
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
```

**Command Line Input:**
```
./main
```

**General Output:**
```
Not enough arguments passed from the command line.
```

**Command Line Input 1:**
```
./main foo
```

**General Output:**
```
count = 2
```

**Command Line Input 2:**
```
./main foo bar
```

**General Output:**
```
count = 3
```

**Command Line Input 3:**
```
./main foo bar baz
```

**General Output:**
```
Too many arguments passed from the command line.
```

Basic example with output showing how to setup another basic if, else if block of statements and condition where thinking about initialisation of a declare can take the place of an else, also general setup of function main.

```
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
```

**General Output:**
```
A
F
D
B
C
```

Basic example showing how to test for the failure of a malloc call, and general setup of function main.

```
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
```

**General Output:**
```
Got 1 MB of memory successfully.
Got 500 MB of memory successfully.
Got 1 GB of memory successfully.
Got 1 TB of memory successfully.
Got 10 TB of memory successfully.
Failed to get 100 TB of memory.
```

We don't know actually how much memory we could allocate on this given system, but it's somewhere between 10 terabytes and less than 100 terabytes of RAM.  This is pretty considerable.  The typical modern desktop computer maxes out as of the writing of this manual between 8 GB and 16 GB according to the latest Steam Hardware Survey [May 2021].  When the code above was run it was executed on a cloud based server which has considerably more memory than a computer you may have access to.

NOTE: Remember that the Operating System, Drivers, Services, and other Software that may be running on the system will be consuming memory.  Just because your machine may have 8 GB of RAM, you may at any given point in time only have access to about 4 GB of RAM that are not in use.  RAM is not unlimited like many courses teach, and should be treated as a finite resource and managed accordingly.

Basic program with output showing how to read and parse simple arguments from the command line, nest if statements, format complex expressions for readability, and general setup of function main.

```
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
```

**Command Line Input 1:**
```
./main
```

**General Output:**
```
Please supply a single character from the command line.
Example:
  ././main [a..z]|[A..Z]|[0..9]

Or a number followed by an operator and another number
  Single digit numbers only.
  Operators [a]dd, [s]ubtract, [m]ultiply, [d]ivide are known.

Example:
  ././main 5 a 9
```

**Command Line Input 2:**
```
./main a
```

General Output:
Lower case letter.

**Command Line Input 3:**
```
./main Z
```

**General Output:**
```
Upper case letter.
```

**Command Line Input 4:**
```
./main 7
```

**General Output:**
```
Number
```

**Command Line Input 5:**
```
./main {
```

**General Output:**
```
Unrecognised
```

**Command Line Input 6:**
```
./main foo bar this
```

**General Output:**
```
Malformed command line arguments...

Please supply a single character from the command line.
Example:
  ././main [a..z]|[A..Z]|[0..9]

Or a number followed by an operator and another number
  Single digit numbers only.
  Operators [a]dd, [s]ubtract, [m]ultiply, [d]ivide are known.

Example:
  ././main 5 a 9
```

**Command Line Input 7:**
```
./main 5 a 9
```

**General Output:**
```
14
```

**Command Line Input 8:**
```
./main 5 d 0
```

**General Output:**
```
Undefined Behaviour - Cannot divide by zero...

Please supply a single character from the command line.
Example:
  ././main [a..z]|[A..Z]|[0..9]

Or a number followed by an operator and another number
  Single digit numbers only.
  Operators [a]dd, [s]ubtract, [m]ultiply, [d]ivide are known.

Example:
  ././main 5 a 9
```

**Command Line Input 9:**
```
./main 5 p 2
```

**General Output:**
```
Malformed command line arguments...

Please supply a single character from the command line.
Example:
  ././main [a..z]|[A..Z]|[0..9]

Or a number followed by an operator and another number
  Single digit numbers only.
  Operators [a]dd, [s]ubtract, [m]ultiply, [d]ivide are known.

Example:
  ././main 5 a 9
```

### Introduction to Switch, Case, Default and Break

There's a few things we need go over in the basics, but otherwise, switch statements are a much cleaner mechanism than if statements generally.  Once you learn to use ternary if statements and switch statements, you won't be using if statements that much.

Basic example with output showing the basic setup of a switch statement, function pointer review, and general setup of function main. (edited)

```
#include <stdio.h>
#include <stdint.h>

typedef char c8;
typedef int32_t s32;

\\ special typedef for a function pointer type to handle
\\ each of the calls inside the caller function and
\\ satisfy a format for the function we can accept
\\
\\ void callSwitchFunc(c8 *name, switchDelegate func)
\\
\\ this will let us pass individual functions and invoke
\\ them reusing the output capabilities of that function

typedef s32 (*switchDelegate)(s32);

//NOTE: none of the following examples of switch statements
//should be considered good form

s32 standardSwitch(s32 foo) {
  s32 r = 0;
 
\\ as mentioned above the code here would be a better
\\ solution to the following and you could do something
\\ like this for each of these other examples also
\\ but as mentioned the idea is just to show form and
\\ layout of each basic switch state
\\  
\\ s32 val[] = {-1,2,3,6,1,4,5};  
\\ return val[(foo < 1 || foo > 6) ? : 0 : foo];
\\
\\ the basic standard switch statement starts off with
\\ switch (expression)
\\ switch statements must contain their case and default
\\ options inside a brace block {}  
\\ each option of a switch statement is denoted by
\\ case value:
\\ followed by C statements of code and must end each
\\ case option with a break statement to prevent a
\\ side-effect called waterfalling
\\ if you are familiar with other programming languages
\\ most will treat each case statement independently
\\ exiting the switch statement without processing any
\\ other case options
\\ this is not the case with C and you must be mindful
\\ of your break statements
\\ the method of catching your else conditions in switch
\\ is by using the default option
\\ it should be your last case option in the switch block

  switch (foo) {
    case 1:  r = 2; break;
    case 2:  r = 3; break;
    case 3:  r = 6; break;
    case 4:  r = 1; break;
    case 5:  r = 4; break;
    case 6:  r = 5; break;
    default: r = -1;
  }

  return r;
}

s32 waterfallSwitch(s32 foo) {
  s32 r = 0;
    
  switch (foo) {
    // if a case statement does not invoke a break
    // it will carry onto the next case automatically
    // until it hits a break somewhere
    // this can be advantageous if you want a series
    // of case options to perform the same option
    
    case 1: 
    case 2:
    case 3:
    case 4:
    case 5:
    case 6:  r =  1; break;
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
```

**General Output:**
```
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
```

Let's quickly cover the things you can't do with case options.

```
case "string":       //strings comparisons are not valid in this context

s32 var = 2; 
case var:            //values attached to a case statement must be constant

s32 arr[] = { ... };
case arr[0]:         //again values must be constant

case >2              //you cannot use any logical operators

case 1.1f:           //floating point types are not allowed, integer types only

case 1: int x = 2;   //declares within scope cannot be declared like this
                     //they must be encapsulated in braces [see below]

case 2:              //all values within the switch block must have unique
case 2:              //case options or undefined behaviour will result
```

Things you can do with case options.

```
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
case 0xF & 20:         //as long as the values used in those expressions
case 0xFE >> 1:        //are constant

case 1 << 2 + 4:       //you are able to create complex expressions also
```

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
}
```

General Output for this example above is identical to the prior version of the code.
Most of the basic branching methods have been explained to this point.  We are not going to cover continue, or exit, as these are considered violations of either spaghetti code or single-entrance single-exit.

# Part 9: For, Do, and While Loops

In order to save typing, handle deeper states of flow and control over our code we need loops.  We encountered our first janky loop using goto and label.  The loops we will be covering in this section will effectively accomplish the same thing, just with cleanliness and features that cannot be provided with primitive spaghetti code.  There are many reasons to repeat sections of your code.  As we progress beyond this section, loops will be an important part of your continued programming journey.  The for loop will be the first one we will be covering.

Basic program with output showing how to setup and use basic for loops, and general setup of function main. (edited)

```
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  for (s32 i = 0; i < 10; ++i) {
    printf("%d %% 9 = %d\n", i, i % 9);
  }
  
  return 0;
}
```

**General Output:**
```
0 % 9 = 0
1 % 9 = 1
2 % 9 = 2
3 % 9 = 3
4 % 9 = 4
5 % 9 = 5
6 % 9 = 6
7 % 9 = 7
8 % 9 = 8
9 % 9 = 0
```

```C
#include <stdio.h>
#include <stdint.h>

typedef char    c8;
typedef int32_t s32;
typedef float   f32;

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
}
```

> General Output:

```
abcdefghijklmnopqrstuvwxyz

01 02 03 04 05 06 07 08 09 10 

0.00 0.20 0.40 0.60 0.80
```

#### Example ?: More than one way to skin a for loop

```
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  for (int x = 0; x < 100; ++x) {
    if (!(x % 10)) puts("");
    printf("%03i ", x);
  }
  puts("\n");

  for (int x = 0, y = 2; x < 100; ++x, ++y) {    
    printf("%03i ", x);
    if (y > 10) y = 1, puts("");
  }
  puts("");

  return 0;
}
```

**General Output:**
```
000 001 002 003 004 005 006 007 008 009 
010 011 012 013 014 015 016 017 018 019 
020 021 022 023 024 025 026 027 028 029 
030 031 032 033 034 035 036 037 038 039 
040 041 042 043 044 045 046 047 048 049 
050 051 052 053 054 055 056 057 058 059 
060 061 062 063 064 065 066 067 068 069 
070 071 072 073 074 075 076 077 078 079 
080 081 082 083 084 085 086 087 088 089 
090 091 092 093 094 095 096 097 098 099 

000 001 002 003 004 005 006 007 008 009 
010 011 012 013 014 015 016 017 018 019 
020 021 022 023 024 025 026 027 028 029 
030 031 032 033 034 035 036 037 038 039 
040 041 042 043 044 045 046 047 048 049 
050 051 052 053 054 055 056 057 058 059 
060 061 062 063 064 065 066 067 068 069 
070 071 072 073 074 075 076 077 078 079 
080 081 082 083 084 085 086 087 088 089 
090 091 092 093 094 095 096 097 098 099
```

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
}
```

**General Output:**
```
3 2 1 0 -1 -6 -7 -8 -9 -10 -11
```

```
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  for (s32 x, counter = 1; x < 8; ++x)
    for (s32 y = x + 1; y < 9; ++y)
      for (s32 z = y + 1; z < 10; printf("%d%d%d ", x, y, z), ++z, ++counter)
        if (counter > 8) counter = 1, puts("");

  return 0;
}
```

**General Output:**
```
012 013 014 015 016 017 018 019 
023 024 025 026 027 028 029 034 
035 036 037 038 039 045 046 047 
048 049 056 057 058 059 067 068 
069 078 079 089 123 124 125 126 
127 128 129 134 135 136 137 138 
139 145 146 147 148 149 156 157 
158 159 167 168 169 178 179 189 
234 235 236 237 238 239 245 246 
247 248 249 256 257 258 259 267 
268 269 278 279 289 345 346 347 
348 349 356 357 358 359 367 368 
369 378 379 389 456 457 458 459 
467 468 469 478 479 489 567 568 
569 578 579 589 678 679 689 789
```

```
#include <stdlib.h>
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  char list[] = {'a', 'b', 0, 'c', 0, 'd', 0 };
  char *array[] = { &list[0], &list[3], &list[5]};

  for (int index = 0; index < 3; ++index)
    for (int offset = 0; array[index][offset]; ++offset)
      printf("[%d] %c\n", index + 1, array[index][offset]);
  
  return 0;
}
```

**General Output:**
```
[1] a
[1] b
[2] c
[3] d
```

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
}
```

> General Output:

```
Ascending

ordered array:
10 11 21 27 46 63 92 

Descending

ordered array:
92 63 46 27 21 11 10
```

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
}
```

> General Output:

```
0 1 2 3 4 5 6 7 8 9 
0 1 2 3 4 5 6 7 8 9
```

A major problem exists with nested loops in C, caused by limitations with the break statement.  It is only capable of escaping one nested layer at a time.  Unfortunately with C there is no other way to escape multiple nested loops, unless the exit conditions are met for each of them, or a goto statement is used.  This can, and will create some spaghetti in your code.

```C
for (...) {
  for (...) {
    if (outlying condition) goto label;
  }
}

label:
```

NOTE: The same problem exists for any nested code that relies on the break statement.  It is very rare that you will need to use this special case, but it is presented, for example of what to do when you have no other choice.

# Part 10: The C Preprocessor

There are plenty of ways you can abuse the C language when writing code.  The Preprocessor is by far the most abused and abusive feature of the language.  When referring to the Preprocessor, we have been using at least one directive in our programs so far called #include.  All Preprocessor directives are preceded by the # symbol.  GCC executes all Preprocessor directives before any processing of your program syntax.  The most useful process we can derive from the Preprocessor is Meta-Programming.  We can literally use the Preprocessor to write C syntax in our code, manage constants, and even determine system architecture we might be running on.  This is useful if we plan on writing cross-platform code beyond the basic C syntax we have covered so far.  Libraries we can #include are determined by the Operating System and the Architecture we are compiling against.

### Preprocessor Directives in GCC

```
//TODO: NEED TO TABLE THIS
#include                 //includes a library in your code
#define                  //defines a named macro
#undef                   //destroys a macro by name
#ifdef  or #if defined   //these are equivalent... checks if a macro is defined
#ifndef or #if !defined  //these are equivalent... checks if a macro is not defined
#elif                    //works just like a regular else if
#else                    //works just like the else in a regular if
#endif                   //ends an #if directive
#pragma                  //allows you to provide additional information to the compiler
```

There are some other handy features of the Preprocessor when it comes to GCC as it has some things predefined to make things a little easier for you.

### Predefined Macros in GCC

```
//TODO: need to table this
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
```

This is far from a complete list, but generally depending on your architecture, cpu, and otherwise, there will be some way to tell what you're running on.  Unfortunately, there is no way to get a complete list, even the GCC manual excludes most of the macros it establishes for a given compilation environment. As we require them, or you develop a need, there is always information somewhere for context.  The list above is just most of the more common ones you might need to reference.

When using GCC you can use -dM with -E on a file to see what is predefined.  This will need to be done from a terminal on Windows or Linux.

> For Windows/DOS: 
```
echo | gcc -dM -E -
```

> For Non-Windows that supports /dev/null: 
```
gcc -dM -E - < /dev/null
```

### \#include
There are two forms for an \#include directive.  Filenames declared as <stdio.h> and "myheader.h".  The \<header> form searches for a file by that name from an internal list of system directories.  These are typically part of the C Standard Library or other packages that you have installed alongside your compiler.  When including using this form "header", the compiler will search the directory that contains the file \_\_BASE\_FILE\_\_.  If you need to modify directories the compiler should be searching for with either form, you can use the -I option from the command line.
  
### Common C Standard Library Headers

```
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
```
   
Most of these you will never use, and many of these we will be going over how to rewrite, or deal with the specifics in other ways.  Most of the C Standard Libraries are janky, poorly written or generic.  Modern equivalents rely on an understanding of each platform you are coding on and for.  This is especially prevalent when dealing with input and output, memory management, and threading models.  For more information on what is and isn't contained in each of these headers, you can find them on the web.  Since our concern will be more detailed and fine grained, these are merely supplied for reference when you are starting from scratch, or just need something quick and dirty.  In general you are advised to mostly avoid the C Standard Library methods, that pretty much goes for any language.

### \#define

This is the basic fundamental way we define macros in C.  It allows us to #define named and value constants, expressions, and meta-functions.  Since #define, along with all other Preprocessor Directives are not processed by any IDE or in real-time, they tend to cause massive confusion amongst programmers.  The C++ language actually frowns on the use of Preprocessor Directives in general, citing they are a direct cause for Undefined Behaviour.  Regardless, they are incredibly powerful, can help reduce errors, and keep code tidy.  Most often they are used to avoid single line functions, having to use the inline keyword, and guarantee that code will be directly replaced.

JANKY EXAMPLE: Basic program with output showing general use of #define statements, and general setup of function main.

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
```

**Emitted by the Compiler Post Preprocessing:**
```
typedef int32_t s32;

s32 main () {
  if (2 == 2 && 4 == 4) {
    puts("foo and bar checked out.");
  }

  return 0;
}
```

> General Output:
```
foo and bar checked out.
```

By using the -E command line argument to the compiler we can trigger the compiler to emit the Preprocessor stage of compiling.  All of the \#define statements without a constant or represented value were removed from the code.  All other \#define macros were replaced at this point with the values they represented.  We can see the constant values of foo and bar, the start and end, equals, and the and macros were all replaced.

JANKY EXAMPLE: Basic program with output showing how to create an argument based #define macro, and general setup of function main.

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
```

**Emitted by the Compiler Post Preprocessing:**
```
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
}
```

> General Output:
```
bar = 1
```

As we can see the buildCase and buildExpress macros can be called or used just like a function.  Argument substitution happens as direct literal replacement.  There are no conversions or casts done on what is passed to a macro.  This allows you to pass things you would not normally be allowed to pass to a standard function as an argument.  The #define directive has many uses which we will explore in later examples.

There are a few operators we should cover that allow us to do some other neat things.  They are useful for concatenating strings, or casting something passed to a macro as a string.

```
Operator   Purpose
------------------------------------------------
 #         casts to a string
 ##        joins what is to the left and right regardless of type
 \         used to denote a multi-line macro [used to escape new lines]
```

JANKY EXAMPLE: Basic program with output showing how to use the \#define directive, use of the \# operator, and setup of function main.

```C
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

s32 main() {
  #define joinStr(str1, str2) #str1 " " #str2 "!"

  puts(joinStr(hello,world));

  return 0;
}
```

**Emitted by the Compiler Post Preprocessing:**
```C
typedef int32_t s32;

s32 main() {
  puts("hello" " " "world" "!");

  return 0;
}
```

**General Output:**
```
hello world!
```

NOTE: Remember that C will join String Literals in this way automatically.

JANKY EXAMPLE: Basic program with output showing how to use the #define directive, use the ## operator, and setup of function main. (edited)
```
#include <stdio.h>
#include <stdint.h>

typedef int32_t s32;

#define joinVars(left, right) left##right

s32 main() {
  int fooBar = 4;

  printf("%i\n", joinVars(foo,Bar));

  return 0;
}
```

**Emitted by the Compiler Post Preprocessing:**
```
typedef int32_t s32;

s32 main() {
  int fooBar = 4;

  printf("%i\n", fooBar);

  return 0;
}
```

**General Output:**
```
4
```

JANKY EXAMPLE: Basic program with output showing how to use the #define directive, use the \ operator, and setup of function main.

```
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
```

**Emitted by the Compiler Post Preprocessing:**
```
typedef int32_t s32;

s32 main() {
  for (int x = 0; x < 10; ++x) printf("x" " = %i\n", x); puts("");
  for (int y = 0; y < 5;  ++y) printf("y" " = %i\n", y); puts("");
  for (int z = 0; z < 3;  ++z) printf("z" " = %i\n", z); puts("");
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
```

We need to use the \ operator with multi-line macros because the \n \[new line\] character is used as the line delimiter for macros.  They do not use the traditional ; end of statement terminator on the last line of a macro.  You do not need to use it on the last line of the macro definition.  Hopefully from this, you can begin to see the capabilities of the Preprocessor.

DOES NOT RUN: Stub code showing how to use the #define, #undef directives.
```
#define foo 3
#undef foo

#define combine(left,right) left##right
#undef combine
```

The #undef directive is useful if you need remove a macro from the known list, or to redefine a macro.  It is good practice to remove the old #define using #undef in either of these cases.

JANKY EXAMPLE: Basic program with output showing how to use the #if, #elif, #else, #endif, defined and general setup of function main. (edited)

```
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
```

NOTE: Keep in mind the way this code is setup, the code will emit variations depending on what Operating System this code has been executed on.  This should not to be regarded as the best way to detect these variations, but this merely a general idea on some of the basic uses of these features of the preprocessor.

**Emitted by the Compiler Post Preprocessing [Unix]:**
```
typedef int32_t s32;

s32 main() {
  printf("the build environment is ");
  puts("unix");

  return 0;
}
```

**General Output:**
```
the build environment is unix
```

**Emitted by the Compiler Post Preprocessing [Windows]:**
```
typedef int32_t s32;

s32 main() {
  printf("the build environment is ");
  puts("windows");

  return 0;
}
```

**General Output:**
```
the build environment is windows
```

JANKY EXAMPLE: Basic program showing how you might setup debug output and control it with #define, #if, #else, #endif and the general setup of function main. (edited)
```
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
```

NOTE: This introduces the \_VA_ARGS__ macro and the use of the ellipsis [...].  When using the ellipsis, this is effectively a variable set of arguments of arbitrary length.  GCC uses the __VA_ARGS___ macro to represent all the arguments that were passed to the method that uses the ellipsis as part of its argument list.  Since debugArgV takes a full argument list like printf normally would, we can use the ellipsis and the associated \_VA_ARGS___ macro to pass the variable argument making this macro as flexible as printf would be normally.  We will explore this later in greater detail in the Intermediate coding section of the book.

**Emitted by the Compiler Post Preprocessing [#define isDebugging]:**
```
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
```

**General Output:**
```
This is a test
int val = 12
int val = 12    float val = 78.12
```

**Emitted by the Compiler Post Preprocessor [//#define isDebugging]:**
```
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
```

**General Output:**
```

```
 
As we can see with the #define isDebugging uncommented, or commented will either leave in or completely remove our debug statements.  This is a much better method than littering your code with older style #if isDebugging wrapped around each block of code you are using for debug output.  This method can be expanded to suit your needs.

Basic program with output showing extensive use of macros to implement a very basic virtual machine.

```
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
```

**Emitted by the Compiler Post Preprocessing:**
```
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
```

NOTE: This is a good example of code that has a lot of replication that can be easily replaced by macros.  Despite this code being relatively simplistic in nature, it relies heavily on case statements that have their associated break statements.  Code of this type generates a lot of extra typing.  Simple macros can save typing, help reduce errors in repetitive code, and in general be used to generate code for you.  One of the advantages of using the preprocessor, we can maintain tokens that make sense which will be replaced once the code in compiled.  The function getc in this case is used to get a single character from the keyboard, but has been replaced by the preprocessor with __IO_getc_.  This is because getc is implemented internally and is replaced by the compiler to the association within the C Standard Library implementation used.  The example code above does implement a very basic integral stack based virtual machine.  It is very limited in capabilities, but does support a decent subset of instructions.  An array called code[] is used to hold the program that will be executed by the virtual machine.  Output from the program executed is below.

**General Output:**
```
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
```

## Part 11: Operator Precedence

The problem with C, the standard doesn't actually define Operator Precedence, so the following table is derived from the base grammar of the C language.  There are a few anomalies, but in general this can be regarded as the order things will fire in if you have complex or compound statements using multiple operators.  Operator order in the following table is first to last priority.

```
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
```

# Chapter 2: Non-Thread Safe Lists, Stacks, Queues, Hash Maps... Oh My!

The following implementations are not thread safe.  A static and dynamic allocation version is provided.  These examples are not documented.  Also due to their complexity and length, they will not have the traditional output examples or dissections.  The code will compile and provide basic use in an implementation of function main. If you need help reading the code, please refer to Chapter 1.

## Part 1: Lists

#### Static implementation of a Vectored List

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct {
  char name[100];
  int nameLen;
  int flags;
} TNode;

typedef struct {
  TNode *nodes;  
  int    count;
  int    tail;
  int    limit;
  int    lastError;
} TVectorList;

#define listFull -1
#define failed    0
#define success   1

int newVectoredList(TVectorList *list, TNode **nodes, int size) {
  int r           = failed;
  int requestSize = sizeof(TNode) * size;
  
  *nodes = malloc(sizeof(TNode) * size);
  
  if (*nodes) {  
    list->limit     = size;
    list->count     = 0;
    list->tail      = 0;
    list->lastError = success;
    
    memset(*nodes, 0, requestSize);
    
    r = success;
  }

  return r;
}

//
// ** vectorListAdd **
//
// @Accepts:
//   TVectorList *list - Should be initialised prior to use
//                       with a call to newVectoredList(...)
//
//   TNode data        - An initialised data node to add to
//                       list. Make sure TNode.name is null
//                       terminated. Function uses strncpy.
//
// @Returns:
//   success - Everything went well.
//   failed  - If the list is full when trying to add.
//
// @Sets: 
//   list->lastError:
//     success  - Everything went well.
//     listFull - Could not add to the list.

//   list->tail - to be 1 less than count to minimize
//                off by one errors and havinge to do -1
//                to count.

int vectorListAdd(TVectorList *list, TNode data) {
  int r           = success;
  list->lastError = success;
  
  list->count++;
  if (list->count <= list->limit) {
    list->tail = list->count - 1;
    
    strncpy(list->nodes[list->tail].name, data.name, data.nameLen);    
    list->nodes[list->tail].flags = data.flags;
  } else {
    list->lastError = listFull;
    r = failed;
  }
  
  return r;
}

int main() {
  TVectorList list = {};
  
  if (newVectoredList(&list, &list.nodes, 50)) {
    printf("nodes out %p\n", list.nodes[0].name);
    
    vectorListAdd(&list, (TNode) { .name = "Blah Blah",    .nameLen = 10, .flags = 2 });
    vectorListAdd(&list, (TNode) { .name = "2nd rec name", .nameLen = 13, .flags = 2 });
    vectorListAdd(&list, (TNode) { .name = "3rd rec name", .nameLen = 13, .flags = 4 });

    printf("list.nodes[0]->name = [%s]\n", list.nodes[0].name);
    printf("list.nodes[1]->name = [%s]\n", list.nodes[1].name);

    for (int i = 0; i < list.count; ++i) {
      printf("rec #%u\n", i);
      printf(".name    = %s\n",   list.nodes[i].name);
      printf(".nameLen = %d\n",   list.nodes[i].nameLen);
      printf(".flags   = %i\n\n", list.nodes[i].flags);
    }
  }

  return 0;
}
```

## Part 2: Queues

Traditional queue examples use linked lists and other jank.  We all should understand this leads to poor cache performance and memory fragmentation.  The following queue implementation shows a different model using a cyclical array structure that amortizes in the dynamic model a possible growth malloc and series of calculated memcpy calls to reogranise and linearly structure the array only when it runs out of space.  The static version of the queue should be used most times calculated to your specific requirements.

This method goes one step further and removes the typical modulus calls and replaces them with a prebaked lookup.  It adds a minor performance gain, there is test code shown for each.  The tests are not complete, and only showing plausible ways to use it, and ideas on how to write efficient code in your projects.  There are likely to be improvements that can be made, but this is a much less terrible implementation than you will find elsewhere.

**NOTE** Several people have reported this code does not build.  Several other C Compilers are incapable of building the code below.  Remember, this manual only ensures the code builds with GCC and executes.  If it does not function on another compiler, remember, not all compilers are created equal.

STATIC IMPLEMENTATION WITH JANKY TESTS

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdint.h>
#include <time.h>

typedef int32_t s32;
typedef float   f32;
typedef size_t  length;

//user record struct for example queue construction and use
typedef struct {
  f32 foo;
  f32 bar;
  s32 state;
} TF32Record;

//
//only used for the #define buildNewStaticQueueContext(recordType)
//

#define begin {
#define elsewise } else {
#define elseIf } else if
#define next }
#define endIf }
#define end }

#define queueRecordPopped 4            //used to set an element to popped state
#define queueRecordPushed 3            //used to set an element to pushed state
#define queueEmptyDataElement 2        //used to set an element to empty
#define queueSuccess 1                 //returned by all queueMethods if successful
#define queueGeneralFailure 0          //returned by all queueMethods on general failure
#define queueArrayMallocFailed -1      //returned when initialising the queue
#define queueResizeFailed -2           //returned by queueSize [dynamic only]
#define queueEmpty -3                  //returned by queuePop and queuePeek when empty
#define queueRemallocGrowthFailed -4   //used only by queueSize [dynamic only]
#define queueRecordNotFound -5         //returned by qeueueGetItem and queueContains
#define queueRecordFound -6            //returned by queueContains
#define queueOutOfBounds -7            //returned by queueGetItem when element is invalid
#define queueFull -8                   //returned on a queuePush if queue is full

#define queueMaxBuffSize 2500

#define buildNewStaticQueueContext(recordType)                                  \
                                                                                \
typedef s32  (recordType##Comparator)(recordType *left, recordType *right);     \
typedef void (recordType##Stringify) (recordType *record, char *buff);          \
                                                                                \
typedef struct {                                                                \
  s32 head;                                                                     \
  s32 tail;                                                                     \
  s32 size;                                                                     \
  s32 count;                                                                    \
  s32 *preBaked;                                                                \
  recordType *array;                                                            \
  recordType##Comparator *compare;                                              \
  recordType##Stringify  *toString;                                             \
} recordType##Queue;                                                            \
                                                                                \
void recordType##QueueDebug(recordType##Queue *queue) {                         \
  printf("size  %d\n"                                                           \
         "count %d\n"                                                           \
         "head  %d\n"                                                           \
         "tail  %d\n",                                                          \
         queue->size, queue->count, queue->head, queue->tail                    \
  );                                                                            \
                                                                                \
  for (s32 i = 0; i < queue->size; ++i) begin                                   \
    char buff[queueMaxBuffSize] = {};                                           \
    queue->toString(&queue->array[i], buff);                                    \
    printf("[%06d] %s\n", i, buff);                                             \
  next                                                                          \
                                                                                \
  puts("");                                                                     \
}                                                                               \
                                                                                \
s32 recordType##NewQueue(recordType##Queue *queue, s32 capacity) {              \
  s32 r           = queueArrayMallocFailed;                                     \
  s32 baseSize    = (sizeof(recordType) * capacity);                            \
  s32 preBakeSize = (sizeof(s32) * capacity);                                   \
                                                                                \
  queue->array = malloc(baseSize + preBakeSize);                                \
  if (queue->array) begin                                                       \
    queue->preBaked = (s32 *)(queue->array + (baseSize + 1));                   \
    for (s32 index = 0; index < capacity; ++index)                              \
      queue->preBaked[index] = (index + 1) % capacity;                          \
    queue->head = 0;                                                            \
    queue->tail = 0;                                                            \
    queue->size = capacity;                                                     \
    queue->count = 0;                                                           \
    r = queueSuccess;                                                           \
  endIf                                                                         \
                                                                                \
  return r;                                                                     \
}                                                                               \
                                                                                \
s32 recordType##NewQueueDefault(recordType##Queue *queue) {                     \
  return recordType##NewQueue(queue, 32);                                       \
}                                                                               \
                                                                                \
s32 recordType##NewQueueDefaultCapacity(                                        \
  recordType##Queue *queue,                                                     \
  s32 capacity) {                                                               \
  return recordType##NewQueue(queue, capacity);                                 \
}                                                                               \
                                                                                \
void recordType##QueueClear(recordType##Queue *queue) {                         \
  memset(queue->array, 0, sizeof(recordType) * queue->size);                    \
  queue->head = 0;                                                              \
  queue->tail = 0;                                                              \
  queue->count = 0;                                                             \
}                                                                               \
                                                                                \
s32 recordType##QueuePush(recordType##Queue *queue, recordType *record) {       \
  s32 r = queueSuccess;                                                         \
  if (queue->count < queue->size) begin                                         \
    record->state = queueRecordPushed;                                          \
    memcpy(&queue->array[queue->tail], record, sizeof(recordType));             \
    queue->tail = queue->preBaked[queue->tail];                                 \
    queue->count++;                                                             \
  elsewise                                                                      \
    r = queueFull;                                                              \
  endIf                                                                         \
                                                                                \
  return r;                                                                     \
}                                                                               \
                                                                                \
s32 recordType##QueuePop(recordType##Queue *queue, recordType *record) {        \
  s32 r = queueSuccess;                                                         \
                                                                                \
  if (queue->count) begin                                                       \
    *record = queue->array[queue->head];                                        \
    record->state = queueRecordPopped;                                          \
    queue->array[queue->head].state = queueEmptyDataElement;                    \
    queue->head = queue->preBaked[queue->head];                                 \
    queue->count--;                                                             \
  elsewise                                                                      \
    r = queueEmpty;                                                             \
    record->state = queueEmptyDataElement;                                      \
  endIf                                                                         \
                                                                                \
  return r;                                                                     \
}                                                                               \
                                                                                \
s32 recordType##PeekQueue(recordType##Queue *queue, recordType *record) {       \
  s32 r = queueSuccess;                                                         \
                                                                                \
  if (queue->count) begin                                                       \
    *record = queue->array[queue->head];                                        \
  elsewise                                                                      \
    r = queueEmpty;                                                             \
    record->state = queueEmptyDataElement;                                      \
  endIf                                                                         \
                                                                                \
  return r;                                                                     \
}                                                                               \
                                                                                \
s32 recordType##PeekQueueIndex(                                                 \
  recordType##Queue *queue,                                                     \
  s32 index,                                                                    \
  recordType *record) {                                                         \
                                                                                \
  s32 r = queueOutOfBounds;                                                     \
                                                                                \
  if ((index + 1) <= queue->count) begin                                        \
    *record = queue->array[queue->preBaked[index - 1]];                         \
    r = queueRecordFound;                                                       \
  endIf                                                                         \
                                                                                \
  return r;                                                                     \
}                                                                               \
                                                                                \
s32 recordType##QueueContains(                                                  \
  recordType##Queue *queue,                                                     \
  recordType *record,                                                           \
  s32 *index) {                                                                 \
                                                                                \
  s32 r = queueRecordNotFound;                                                  \
  s32 count = queue->size;                                                      \
  *index = queue->head;                                                         \
                                                                                \
  while (count-- > 0) begin                                                     \
    if (record->state == queueEmptyDataElement) begin                           \
      if (queue->array[*index].state == queueEmptyDataElement) begin            \
        r = queueRecordFound; break;                                            \
      endIf                                                                     \
    elseIf (queue->compare(&queue->array[*index],record)) begin                 \
      r = queueRecordFound; break;                                              \
    endIf                                                                       \
                                                                                \
    *index = queue->preBaked[*index];                                           \
  end                                                                           \
                                                                                \
  return r;                                                                     \
}

//constructs the qeueue based on the type specified to the macro
//all methods will be prefixed with this type
buildNewStaticQueueContext(TF32Record);

//will need to create two functions

//
// ** TF32RecordCompare **
//
// @Notes: Function used as the internal comparator
//         for the queue.
//
// @Accepts:
//   TF32Record *left  - 1st record to compare
//   TF32Record *right - 2nd record to compare 
//
// @Returns:
//   1 - for equal
//   0 - for not equal

s32 TF32RecordCompare(TF32Record *left, TF32Record *right) {
  return (left->foo == right->foo) &&
         (left->bar == right->bar);
}

//
//** toString **
//
//NOTES: char *buff is max length 2500 bytes - 1 byte not useable for null termination
//       array should be passed initialised with nulls
void TF32RecordToString(TF32Record *record, char *buff) {  
  snprintf(buff, 2500, "[foo = %.2f | bar = %.2f | state = %d]", record->foo, record->bar, record->state);
}

s32 main() {
  //create a queue record on the stack  
  TF32RecordQueue queue = {};
  //initialise it
  TF32RecordNewQueueDefault(&queue);

  //set the internal comparator method
  queue.compare  = &TF32RecordCompare;
  //set the internel to string method
  queue.toString = &TF32RecordToString;

  //create a record to hold anything popped from the queue
  TF32Record popped = {};

  //
  //run tests...
  //

  //create a bunch of records on the stack for testing purposes
  TF32Record records[42] = {};

  //populate a mock record
  records[0] = (TF32Record){ .foo = 1.1f, .bar = 2.0f };
  //push it to the queue
  TF32RecordQueuePush(&queue,&records[0]);

  records[1] = (TF32Record){ .foo = 2.1f, .bar = 3.0f };
  TF32RecordQueuePush(&queue,&records[1]);

  //pop a record from the queue
  TF32RecordQueuePop(&queue, &popped);

  //there is a define setting the to string limit
  char buff[queueMaxBuffSize] = {};
  queue.toString(&popped, buff);
  printf("%s\n\n", buff);

  TF32RecordQueuePop(&queue, &popped);
  queue.toString(&popped, buff);
  printf("%s\n\n", buff);

  //populate a bunch of records in the test array
  for (s32 i = 2, result; i < 42; ++i) {
    records[i] = (TF32Record) { .foo = i, .bar = i*2 };
    //TF32RecordQueueDebug(&queue);
  }
  
  return 0;
}
```
**General Output**
```
[foo = 1.10 | bar = 2.00 | state = 4]

[foo = 2.10 | bar = 3.00 | state = 4]

could not push... full.
[foo = 33.00 | bar = 66.00 | state = 3] - found at index 1

[foo = 19.00 | bar = 38.00 | state = 3] - pulled from index 19

size  32
count 32
head  2
tail  2
[000000] [foo = 32.00 | bar = 64.00 | state = 3]
[000001] [foo = 33.00 | bar = 66.00 | state = 3]
[000002] [foo = 2.00 | bar = 4.00 | state = 3]
[000003] [foo = 3.00 | bar = 6.00 | state = 3]
[000004] [foo = 4.00 | bar = 8.00 | state = 3]
[000005] [foo = 5.00 | bar = 10.00 | state = 3]
[000006] [foo = 6.00 | bar = 12.00 | state = 3]
[000007] [foo = 7.00 | bar = 14.00 | state = 3]
[000008] [foo = 8.00 | bar = 16.00 | state = 3]
[000009] [foo = 9.00 | bar = 18.00 | state = 3]
[000010] [foo = 10.00 | bar = 20.00 | state = 3]
[000011] [foo = 11.00 | bar = 22.00 | state = 3]
[000012] [foo = 12.00 | bar = 24.00 | state = 3]
[000013] [foo = 13.00 | bar = 26.00 | state = 3]
[000014] [foo = 14.00 | bar = 28.00 | state = 3]
[000015] [foo = 15.00 | bar = 30.00 | state = 3]
[000016] [foo = 16.00 | bar = 32.00 | state = 3]
[000017] [foo = 17.00 | bar = 34.00 | state = 3]
[000018] [foo = 18.00 | bar = 36.00 | state = 3]
[000019] [foo = 19.00 | bar = 38.00 | state = 3]
[000020] [foo = 20.00 | bar = 40.00 | state = 3]
[000021] [foo = 21.00 | bar = 42.00 | state = 3]
[000022] [foo = 22.00 | bar = 44.00 | state = 3]
[000023] [foo = 23.00 | bar = 46.00 | state = 3]
[000024] [foo = 24.00 | bar = 48.00 | state = 3]
[000025] [foo = 25.00 | bar = 50.00 | state = 3]
[000026] [foo = 26.00 | bar = 52.00 | state = 3]
[000027] [foo = 27.00 | bar = 54.00 | state = 3]
[000028] [foo = 28.00 | bar = 56.00 | state = 3]
[000029] [foo = 29.00 | bar = 58.00 | state = 3]
[000030] [foo = 30.00 | bar = 60.00 | state = 3]
[000031] [foo = 31.00 | bar = 62.00 | state = 3]

size  32
count 32
head  2
tail  2
[000000] [foo = 32.00 | bar = 64.00 | state = 3]
[000001] [foo = 33.00 | bar = 66.00 | state = 3]
[000002] [foo = 2.00 | bar = 4.00 | state = 3]
[000003] [foo = 3.00 | bar = 6.00 | state = 3]
[000004] [foo = 4.00 | bar = 8.00 | state = 3]
[000005] [foo = 5.00 | bar = 10.00 | state = 3]
[000006] [foo = 6.00 | bar = 12.00 | state = 3]
[000007] [foo = 7.00 | bar = 14.00 | state = 3]
[000008] [foo = 8.00 | bar = 16.00 | state = 3]
[000009] [foo = 9.00 | bar = 18.00 | state = 3]
[000010] [foo = 10.00 | bar = 20.00 | state = 3]
[000011] [foo = 11.00 | bar = 22.00 | state = 3]
[000012] [foo = 12.00 | bar = 24.00 | state = 3]
[000013] [foo = 13.00 | bar = 26.00 | state = 3]
[000014] [foo = 14.00 | bar = 28.00 | state = 3]
[000015] [foo = 15.00 | bar = 30.00 | state = 3]
[000016] [foo = 16.00 | bar = 32.00 | state = 3]
[000017] [foo = 17.00 | bar = 34.00 | state = 3]
[000018] [foo = 18.00 | bar = 36.00 | state = 3]
[000019] [foo = 19.00 | bar = 38.00 | state = 3]
[000020] [foo = 20.00 | bar = 40.00 | state = 3]
[000021] [foo = 21.00 | bar = 42.00 | state = 3]
[000022] [foo = 22.00 | bar = 44.00 | state = 3]
[000023] [foo = 23.00 | bar = 46.00 | state = 3]
[000024] [foo = 24.00 | bar = 48.00 | state = 3]
[000025] [foo = 25.00 | bar = 50.00 | state = 3]
[000026] [foo = 26.00 | bar = 52.00 | state = 3]
[000027] [foo = 27.00 | bar = 54.00 | state = 3]
[000028] [foo = 28.00 | bar = 56.00 | state = 3]
[000029] [foo = 29.00 | bar = 58.00 | state = 3]
[000030] [foo = 30.00 | bar = 60.00 | state = 3]
[000031] [foo = 31.00 | bar = 62.00 | state = 3]

popped -> [foo = 2.00 | bar = 4.00 | state = 4]
popped -> [foo = 3.00 | bar = 6.00 | state = 4]
popped -> [foo = 4.00 | bar = 8.00 | state = 4]
popped -> [foo = 5.00 | bar = 10.00 | state = 4]
popped -> [foo = 6.00 | bar = 12.00 | state = 4]
popped -> [foo = 7.00 | bar = 14.00 | state = 4]
popped -> [foo = 8.00 | bar = 16.00 | state = 4]
popped -> [foo = 9.00 | bar = 18.00 | state = 4]
popped -> [foo = 10.00 | bar = 20.00 | state = 4]
popped -> [foo = 11.00 | bar = 22.00 | state = 4]
popped -> [foo = 12.00 | bar = 24.00 | state = 4]
popped -> [foo = 13.00 | bar = 26.00 | state = 4]
popped -> [foo = 14.00 | bar = 28.00 | state = 4]
popped -> [foo = 15.00 | bar = 30.00 | state = 4]
popped -> [foo = 16.00 | bar = 32.00 | state = 4]
popped -> [foo = 17.00 | bar = 34.00 | state = 4]
popped -> [foo = 18.00 | bar = 36.00 | state = 4]
popped -> [foo = 19.00 | bar = 38.00 | state = 4]
popped -> [foo = 20.00 | bar = 40.00 | state = 4]
popped -> [foo = 21.00 | bar = 42.00 | state = 4]
popped -> [foo = 22.00 | bar = 44.00 | state = 4]
popped -> [foo = 23.00 | bar = 46.00 | state = 4]
popped -> [foo = 24.00 | bar = 48.00 | state = 4]
popped -> [foo = 25.00 | bar = 50.00 | state = 4]
popped -> [foo = 26.00 | bar = 52.00 | state = 4]
popped -> [foo = 27.00 | bar = 54.00 | state = 4]
popped -> [foo = 28.00 | bar = 56.00 | state = 4]
popped -> [foo = 29.00 | bar = 58.00 | state = 4]
popped -> [foo = 30.00 | bar = 60.00 | state = 4]
popped -> [foo = 31.00 | bar = 62.00 | state = 4]
popped -> [foo = 32.00 | bar = 64.00 | state = 4]
popped -> [foo = 33.00 | bar = 66.00 | state = 4]
```

DYNAMIC IMPLEMENTATION WITH JANKY TESTS
