# Assembly DMC8 Fibonacci generator
This program is written in DMC8 assembly language and is sued to generate a fibonnaci sequence up to an inputted number n.

### Disclaimer
1. In this program you may notice that register A is used to carry out operations. Despite the deeds documentation indicating otherwise you cannot perform many of the arithmetic operations on registers other than A.
2. Before running thsi program on the deeds software you must change the RAM to 32k.
   
# How it works
The first few lines of code initialise the program and the input and output ports like so. Please note that the output port is there for debugging purposes.

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
HL to memory address 0xFFD0. This pointer will be used to write the fibonacci sequence generated into RAM. For error handling, we check if the input is 0. If it is the program will return 0. Similarly we will check if the input is 1. If so we will return 0, 1. These are our two base cases. If both pass we can continue our program.

We will use n to determine the number of iterations we need to carry out in the program. We will immediately decrease it by two after the zero check to account for the setting of the first two numbers. The counter will be then stored into register E. Registers B and C will be used to keep track of the last two fibonacci numbers generated. In this function they will be set to 0 and 1 respectively. These numbers will also be saved into memroy at this stage.

----------
### FIB
We will reload the counter into register A to use the `CP` command and check if number of iterations has been reached. If it has we will terminate the program. We then decrease the counter for the new iteration we will perform and save into E. We will then add content in register's B and C to obtain our next fibonnaci number. We will proceed to shift the numbers stored in B and C so they keep track of the two new last numbers generated.

----------
### RETURN
We will write the last number generated into memory and we will terminate the program.










