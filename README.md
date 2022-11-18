# x86-64 Assembly

1) Cheatsheet utility for assembling, disassembling and debugging files from terminal.

2) Assembler.sh Bash script to automate process of assembling and debugging an assembly script. 

![image](https://user-images.githubusercontent.com/118491337/202597717-2277d022-e3dd-4473-9fe1-aae28ea0e8ed.png)





------------------
MANUAL ASSEMBLING:
------------------

Instructions to assemble code and generate an executable file (Linux enviroment) :

An assembly script usually has the (.s extension)

use nasm to convert it to machine code (.o extension): nasm -f elf64 fibonacci.s

then link it using ld, it will generate the actual executable: ld -o fibonacci ficonacci.o



------------
ASSEMBLER.SH
------------

Bash script that automate the process of compiling, linking and running assembly script

usage:

./assembler.sh filename.s



--------------------------------------------
MANUALLY DISASSEMBLIGN - OBJDUMP TOOL:
--------------------------------------------

It will disassemble an executable into assembly instructions. It will allow you to study the corresponding assembly instructions of an executable file. 

objdump -M intel -d filename

Show cleaner output (no hex values):

objdump -M intel --no-show-raw-insn --no-addresses -d helloWorld

Show data section values of the executable :

objdump -sj .data helloWorld


-------------
GNU DEBUGGER:
-------------

Gnu debugger is an utility integrated in linux, used with gef extensions it allows you to debug executable applications in terminal.

INSTALL GEF (LINUX GNU HACKER PLUGIN)

wget -O ~/.gdbinit-gef.py -q https://gef.blah.cat/py
echo source ~/.gdbinit-gef.py >> ~/.gdbinit

USAGE: IT WILL DISASSEMBLE AND DEBUG AN EXECUTABLE

gdb -q ./helloWorld



-------------------
ASSEMBLER.SH + GDB:
-------------------

NOW YOU CAN USE BASH SCRIPT TO ASSEMBLE AND DEBUG AN EXECUTABLE:

./assembler.sh helloWorld.s -g


OUTPUT, you entered in gdb menu:

![Selezione_196](https://user-images.githubusercontent.com/118491337/202596562-da46264f-9b60-4ca9-be59-404e913a6435.png)


DISPLAY INFO LIST USING:

gef➤ info


PUT BREAKPOINT AT A FUNCTION:

gef➤  b _start


----------------
RUN
----------------

gef➤ r

IT WILL DISPLAY ACTUAL STATUS OF REGISTERS AND APPLICATION EXECUTION AT BRAKEPOINT.
Note: the instruction shown with the -> symbol is where we are at, and it has not yet been processed.

![image](https://user-images.githubusercontent.com/118491337/202597717-2277d022-e3dd-4473-9fe1-aae28ea0e8ed.png)

![image](https://user-images.githubusercontent.com/118491337/202597624-9646a79f-3816-4835-bdcb-9007d0baf0a9.png)
































