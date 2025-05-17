# 110. Normal Function Call vs System Calls in OS

## Function Calls

Function calls are used to execute a specific block of code like a function or subroutine within a program. They run within the same execution context or address space as the calling program.

Function calls are suitable for tasks that are part of the program itself, such as:

- Performing calculations  
- Manipulating data structures  
- Invoking utility functions  

Parameters and data are passed to functions through the program's stack or registers, depending on the programming language and system architecture.

Function calls are usually resolved at compile-time or link-time, which means they have a lower execution overhead compared to system calls.

![image](https://github.com/user-attachments/assets/75de7cdc-c66e-4134-9560-87f6caf32674)

---

## System Calls

System calls provide a way for applications to request services from the operating system. Unlike function calls, system calls run in a different execution context or address space, as they need to interact with the privileged kernel mode of the OS.

### Common uses of system calls:

- File I/O (e.g., reading or writing files)  
- Process management (e.g., creating or terminating processes)  
- Memory allocation  
- Inter-process communication  

They abstract the details of the OS implementation, providing a standard way to access its services.

Parameters for system calls are passed in a different way compared to function calls, as they have to transition between user space and kernel space. This can involve passing parameters in registers, memory blocks, or the stack.

System calls are typically implemented as software interrupts or traps, which transfer control to the kernel. This transition causes system calls to have higher execution overhead compared to function calls.

---

## Difference between Function Calls and System Calls

| Aspect              | Function Calls                                                                 | System Calls                                                                 |
|---------------------|--------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| Execution Context    | Within the same execution context/address space as the calling program         | Operate in a different execution context/address space, interacting with the OS kernel |
| Purpose              | Execute specific blocks of code within the program                            | Request services from the operating system                                    |
| Usage                | Used for tasks like calculations, data manipulation, and utility functions     | Used for accessing OS functionalities like file I/O, process management       |
| Parameters Passing   | Passed via the program's stack or registers                                   | Passed differently, often bridging user space and kernel space                |
| Resolution Time      | Resolved at compile-time or link-time                                         | Resolved at runtime when invoked by the program                               |
| Overhead             | Lower execution overhead                                                       | Higher execution overhead due to context switching and kernel interaction     |
| Example              | `int sum = add(2, 3);`                                                         | `int fd = open("file.txt", O_RDONLY);`                                        |

---

## Example Application: Calculator

- **Function Calls**: In a calculator application, function calls like `add`, `subtract`, `multiply`, and `divide` are used to perform arithmetic operations. These functions are called whenever the user performs an operation like adding two numbers.

- **System Calls**: If the calculator needs to store the calculation history in a file, it would use system calls. For example, it could use system calls to write the results to a text file or read the stored history.

---

> 📘 System calls act as a controlled gateway between user applications and kernel-level operations, ensuring safety, abstraction, and efficiency.
