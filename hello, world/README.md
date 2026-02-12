## Overview 
super simple hello world program, thought it was right to start with this.

TIL (Today I learned):
- Watched [this](https://www.youtube.com/watch?v=6o74Kdpy5pk) really good video on Ocaml and studied what "core dump" is
- Studied how Ocaml compiles and why running `ocamlc -o hello,\ world helloworld.ml` leads to 3 different files being created
***

## Core dumps vs Seg fault

Firstly, I realised that the awful segmentation faults I get in my code all the time are in fact, a result of core dumps (or to be more apt, a result of my skill issue with code lmao). Usually a <b>segmentation fault</b> occurs in C/C++ if you try to access some memmory outisde of the assigned memory. 
To be more specific, this can happen if:
- you try to write in a <b>read-only</b> memory location.
- stack overflow
- divide by 0
<br/>
A <b>core dump</b> is written by the operating system once the file crashes, it captures the program's state just before the failure occurs and can be accessed by the developer to study what caused the crash. It contains detailed info about the memory, variables and execution points.
<br/>
Now, why does this matter in Ocaml?
<br/>
This is because Ocaml does not commonly generate core dumps like in C/C++. Ocaml can be described as a <b>memory safe</b> language, due to its automatic memory management. In most cases, things that cause seg faults in C/C++ are not allowed at all in Ocaml or more specifically, they raise exceptions/errors. That being said, Ocaml can generate core dumps as well but in rarer cases. This does help a lot if you work with pointers because those seg faults are especially annoying. 

## Ocaml compilation
ocamlc is the batch compiler for OCaml.
When ocamlc is run, it compiles the source code into OCaml bytecode. As a result, three files are produced: one with no extension, a .cmi file, and a .cmo file.

The file with no extension is the bytecode executable.

The .cmi file is the <b>compiled module interface</b>. It contains the module’s type information and is used by the compiler to type-check other modules and ensure interface compatibility.

The .cmo file is the <b>compiled module object</b>. It contains the module’s bytecode implementation, along with metadata such as dependencies and safety information. The bytecode is stored in a binary format, so it is not human-readable, and tools like `ocamlobjinfo` only display the metadata, not the instructions themselves.

When `ocamlrun` is called, the executable will be run by the bytecode interpreter.

![compilation of Ocaml](https://sookocheff.com/post/ocaml/the-ocaml-compiler-pipeline/assets/bucklescript.png)

## Fun Fact
one of the first rust compilers was written in Ocaml :)


