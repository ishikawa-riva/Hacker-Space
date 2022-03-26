# Buffer Overflows Windows\_x32

## Pre-Requisites

### Calling Conventions

#### `CDECL`

1. All Arguments are passed onto stack ( _**From Right to Left**_ i.e. last argument is pushed first into stack).
2. _**CALLER ( who is calling the function )**_ must clean the stack.
3. **`Methods which use variable number of Arguments must use this convention`**

#### `STDDECL`(Standard convention for calling WIN32 API calls)

1. All Arguments are pushed on stack from **RIGHT to LEFT**.
2. _**CALLEE ( The function which is called )**_ will clean the stack.
3. **`Can not be used for methods with variable number of arguments`** because - The CALLEE has no way of knowing what was passed.

#### `FASTCALL`

1. First Two arguments are passed in **`ECX, EDX`** registers.
2. _**All `additional` arguments are passed on stack**_.
3. _**CALLEE cleans the stack**_.

### How to exploit Buffer Overflow

For a successful buffer overflow -

1. _**We must overwrite the return address on stack, i.e ( Take Control over`Instruction Pointer`)**_
2. Can Inject Shell Code.

### About Stack

1. We **overflows** the local variables, it will overwrite the **`RETURN` address.**
2. _**Stack grows Downwards.**_

![](assets\_md/Pasted%20image%2020220319114135.png)
