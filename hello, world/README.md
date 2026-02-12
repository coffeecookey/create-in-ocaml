## Overview 
super simple hello world program, thought it was right to start with this.

TIL (Today I learned):
- Watched [this](https://www.youtube.com/watch?v=6o74Kdpy5pk) really good video on Ocaml and studied what "core dump" is
- Then I studied what a register is
- Studied how Ocaml compiles and why running `ocamlc -o hello,\ world helloworld.ml` leads to 3 different files being created

#### Core dumps vs Seg fault

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


