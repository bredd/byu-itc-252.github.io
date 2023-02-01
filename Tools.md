---
title: Linux Computer Architecture Tools
---
As you learn about computer architecture and work through the labs, these tools will be valuable.

To get started, you need to make sure the tools are installed in your Linux installation (whether a physical machine, a VM, or Windows Subsystem for Linux). From your Linux command line use the following commands:
```
sudo apt update
sudo apt install gcc build-essential
sudo apt install
sudo apt-get install gcc-multilib
sudo apt-get install gdb
```

*gcc-multilib* lets you compile for 32-bit as well as 64-bit.
*gdb* installs the debugger.

## **gcc** Compiler/Linker
Compiles code in C, C++, and a variety of other languages and links code from multiple modules and libraries into an executable file.

### Commonly-used options
* `-m32` Compile and link for 32-bit mode
* `-O0` Turn off all optimizations making assembly code easier to read and debug. (That's capital "O" followed by zero.) Sometimes `-O1` with minimal optimization may be valuable. 
* `-S` Compile to assembly language - to see how things are done.
* `-S -masm=intel` Compile to intel-syntax assembly language. 
* `-S -masm=att` Compile to AT&T-syntax assembly language. (Not really necessary because that's the default.)
* `-c` Compile to an object file to be linked or dumped.
* `-fno-asynchronous-unwind-tables -fno-pie` Remove extra stuff from the generated code so you can see just what the compiler is doing. For details on what these mean see [this article](https://stackoverflow.com/questions/38552116/how-to-remove-noise-from-gcc-clang-assembly-output) and [this article](https://stackoverflow.com/questions/50105581/how-do-i-get-rid-of-call-x86-get-pc-thunk-ax) from StackOverflow.
* `-ggdb` Include debugging symbols 

### Example

Create a file called `add.c` with the following contents:
```
int add(int a, int b)
{
  return a + b;
}
```

Compile it to assembly using the following command:
```
gcc -m32 -O0 -S -fno-asynchronous-unwind-tables -fno-pie -masm=att add.c
```

This will produce a file called `add.s` with the assembly language version of the code.

Try the same thing without the -m32 option to see how 64-bit code differs from the 32-bit version.

## **objdump** Object and executable file dump tool
Dumps the contents of object and executable files including disassembling machine code.

### Commonly-used options
* `-d` Disassemble all .text (code) sections.
* `-s` Binary dump all sections.

### Example

Use the same `add.c` file from the **gcc** example. Compile it to an object file with the following command:

```
gcc -m32 -O0 -c -fno-asynchronous-unwind-tables -fno-pie -masm=att add.c
```

Now dump the contents using the following command:

```
objdump -d -s add.o
```

## **gdb** GNU Debugger
Loads a program and lets you examine it while running including setting breakpoints, examining register contents, examining variables, changing values and so forth.

We can only get you started in this document. More detail can be found here: [GDB Step By Step Introduction](https://www.geeksforgeeks.org/gdb-step-by-step-introduction/).

### Command line
Start gdb by specifying the program to be debugged on the command line.
* **gdb** a.out

Once it's running you type commands to debug the code.

### Common commands
* `set disassembly-flavor intel` Disassemble in Intel syntax
* `set disassembly-flavor att` Disassemble in AT&T syntax (this is the default)
* `disassemble <name>` Disassemble the named function
* `list` List the source code in the vicinity of the current location.
* `break <name>` Set a breakpoint on the named function
* `break *<address>` Set a breakpoint at the specified address
* `run` Start the program from the beginning
* `continue` Continue running the program after reaching a breakpoint
* `step` Go to the next instruction, diving into functions when called
* `next` Go to the next instruction, skipping over function calls
* `exit` Exit the debugger

### Example
Create a file called `add.c` with the following contents:
```
#include <stdio.h>

int add(int a, int b)
{
  return a + b;
}

int main(int argc, char **argv)
{
  printf("%d\n", add(3,5));
}
```

Compile and link the program with the following command:
```
gcc -m32 -O0 -fno-asynchronous-unwind-tables -fno-pie -ggdb add.c
```

Load the program into the debugger and try a few commands:
```
gdb a.out
disassemble add
disassemble main
break add
run
list
info registers
backtrace
continue
```
