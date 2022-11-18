# x86-64 Assembly

1) Cheatsheet utility for assembling, disassembling and debugging assembly files from terminal.

2) Assembler.sh Bash script to automate process of assembling and debugging an assembly script. 



MANUAL ASSEMBLING:


Instructions to assemble code and generate an executable file (Linux enviroment) :

An assembly script usually has the (.s extension)

use nasm to convert it to machine code (.o extension): nasm -f elf64 fibonacci.s

then link it using ld, it will generate the actual executable: ld -o fibonacci ficonacci.o




ASSEMBLER.SH


Bash script that automate the process of compiling, linking and running assembly script

usage:

./assembler.sh filename.s




DISASSEMBLING MANUAL COMMAND - OBJDUMP TOOL:


It will disassemble an executable into assembly instructions. It will allow you to study the corresponding assembly instructions of an executable file. 

objdump -M intel -d filename

Show cleaner output (no hex values):

objdump -M intel --no-show-raw-insn --no-addresses -d helloWorld

Show data section values of the executable :

objdump -sj .data helloWorld



GNU DEBUGGER:


Gnu debugger is an utility integrated in linux, used with gef extensions it allows you to debug executable applications in terminal.

INSTALL GEF (LINUX GNU HACKER PLUGIN)

wget -O ~/.gdbinit-gef.py -q https://gef.blah.cat/py
echo source ~/.gdbinit-gef.py >> ~/.gdbinit

USAGE: IT WILL DISASSEMBLE AND DEBUG AN EXECUTABLE

gdb -q ./helloWorld




ASSEMBLER.SH + GDB:


NOW YOU CAN USE BASH SCRIPT TO ASSEMBLE AND DEBUG AN EXECUTABLE:

./assembler.sh helloWorld.s -g



OUTPUT: 




















