# Assembly DMC8 Fibonacci generator
This program is written in DMC8 assembly language and is sued to generate a fibonnaci sequence up to an inputted number n.

# How it works
The first few lines of code initialise the program and the input and output ports like so:

```
JP 0800h
ORG 0800h 

INPORT EQU 00h ; WHERE YOU ENTER THE NUMBER N
OUTPORT EQU 00h
```

The rest of the pogram is divided into three functions: START, FIB, RETURN.

----------
### START
First we retrieve the input from the input port 00h (please note that this input is in hexadecimal so the calculations for n will also be computed in this way). We then initialise a pointer (indirect addressing)
HL to memory address 0xFFD0. This pointer will be used to write the fibonacci sequence generated into RAM. For error prevention, we check if the input is 0. If it is the program will return 0. 

We will use n to determine the number of iterations we need to carry out in the program. We will immediately decrease it by two after the zero check to account for the setting of the first 






