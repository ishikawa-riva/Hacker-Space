---
description: Binary Exploitation
---

# Reverse Engineering

## Quick Introduction to Assembly

### Registers And Assembly Programming Convention

![](<assets\_md/Pasted image 20220319095929.png>)

![](<../assets\_md/Pasted image 20220319100710.png>)

![](<../assets\_md/Pasted image 20220319100820.png>)

### First Assembly Program

![](<../assets\_md/Pasted image 20220319101428.png>)

![](<../assets\_md/Pasted image 20220319101508.png>)

**Basic Assembly `Hello World` Program**

```
global _start			

section .text

HelloWorldProc:

	push rbp
	mov rbp, rsp

	; Print hello world using write syscall
	
	mov rax, 1
	mov rdi, 1
	mov rsi, hello_world 
	mov rdx, length
	syscall

	; mov rsp, rbp
	; pop rbp

	leave
	ret   ; signifies end of procedure 


_start:

	mov rcx, 0x10

PrintHelloWorld:
	
	push rcx
	call HelloWorldProc
	pop rcx
	loop PrintHelloWorld


	; exit gracefully 
	
	mov rax, 60
	mov rdi, 11
	syscall


section .data
```

#### Manuals/Help Commands

1. `man 2 syscall`
2. `less /usr/include/x86_64-linux-gnu/asm/unistd_64.h`
