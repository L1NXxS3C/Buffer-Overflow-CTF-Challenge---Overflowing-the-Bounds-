Description
Welcome to the Buffer Overflow CTF Challenge! Your task is to exploit a vulnerable program by taking advantage of a buffer overflow in order to execute a hidden function and retrieve the flag.

The program asks for user input but is poorly designed, making it vulnerable to buffer overflows. If you manage to overwrite the program's execution flow, you'll be able to jump to a hidden function that will print the flag.

Your goal is to:
- Analyze the binary
- Craft a buffer overflow exploit
- Redirect the program's execution to unlock the hidden flag.

# Difficulty Level: Hard  
This challenge is designed for advanced CTF players. No hints are provided, and exploitation will require deep understanding of buffer overflow techniques, GDB debugging, and return address manipulation.

---

 Instructions

1. Download the Binary:
   - You have been provided with a binary named hard_overflow. Your job is to exploit it!

2. Run the Binary:
   
   ./hard_overflow
   
   The program will prompt you to enter some input. This input is processed in a vulnerable way, allowing you to craft an exploit.

3. Analyze the Binary:
   Use tools such as:
   - objdump to inspect the binary and find interesting functions.
   - gdb to step through the program, identify the buffer overflow, and find the return address offset.
   
   Hint: The flag is hidden within a function. Can you find it?

4. Craft Your Exploit:
   You will need to carefully craft an input that exploits the buffer overflow, allowing you to take control of the program's execution. Redirect it to the hidden function to retrieve the flag!

---

 Environment Setup

You will need:
- A Linux environment (the challenge was tested on Ubuntu).
- Tools like gdb, objdump, and Python for scripting the exploit.
- Make sure to disable ASLR (Address Space Layout Randomization) to make exploitation easier:
   
   sudo sysctl -w kernel.randomize_va_space=0
   

To compile the vulnerable binary yourself (if needed), use the following flags to disable security mitigations:
gcc -o hard_overflow hard_overflow.c -fno-stack-protector -z execstack -no-pie

---

 Exploitation Steps

1. Find the Vulnerability: Use GDB to analyze the buffer overflow in the vulnerable_function. Find how much input is required to overflow the buffer and control the return address.
   
2. Locate the Hidden Function: Use objdump or GDB to find the address of the hidden function that prints the flag.

3. Create Your Payload: Craft an exploit that overwrites the return address and redirects execution to the hidden flag function.

4. Get the Flag: Run the program with your exploit to trigger the hidden function and retrieve the flag.
