# Process Management in C

This C program demonstrates process management in a Unix-like environment using the `fork`, `execvp`, and `wait` functions. It allows you to execute a command in a child process and handle signals like Ctrl-C (SIGINT), Ctrl-Z (SIGTSTP), and Ctrl-\ (SIGQUIT).

## Table of Contents
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Signal Handling](#signal-handling)
- [License](#license)

## Prerequisites
- A Unix-like operating system (e.g., Linux)
- GCC (GNU Compiler Collection) for compiling the C code

## Getting Started
1. Clone this repository to your local machine:

   '''sh
   git clone https://github.com/your-username/process-management-c.git
   
Change to the project directory:
cd process-management-c

Compile the C program using gcc:
gcc process_management.c -o process_management

Usage
Run the program with the command you want to execute as an argument. For example, to run the ls command:

./process_management ls
This will execute the ls command in a child process and demonstrate various signal handling scenarios.

Signal Handling
Ctrl-C (SIGINT) is handled by the child process.
Ctrl-Z (SIGTSTP) is handled by the child process.
Ctrl-\ (SIGQUIT) is handled by the parent process, which terminates the child and exits.
