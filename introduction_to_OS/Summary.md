# Understanding Program Execution: A Real-World Walkthrough

This section explains the complete execution flow of two different applications using the OS concepts we've studied:

- **Case 1**: A simple **C++ program that adds two integers**
- **Case 2**: **Writing text in Microsoft Word**

We’ll break both down by OS concepts like: program, process, thread, kernel, user mode, system calls, multitasking, etc.

---

## Case 1: C++ Program - Adding Two Integers

**Program Objective**: Take two integers as input, add them, and display the result.

### 🔹 1. Writing and Saving the Program (Source Code)
You write the following C++ code in VSCode:

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cin >> a >> b;
    cout << (a + b);
    return 0;
}
```

At this point, it's just a **program** (not a process) – a static file stored on disk.

---

### 🔹 2. Compilation (Turning Code into Executable)
When you click "Run" or compile with `g++`:
- Compiler translates your code into **machine code** (executable).
- The executable is stored on disk (e.g., `a.exe` or `main.out`).
- The OS manages this with **batch processing** (if part of automated tools) or **interactive mode**.

---

### 🔹 3. Loading the Program (Process Creation)
When you run the program:
- The OS creates a **process** from your executable.
- It sets up a **Process Control Block (PCB)** to manage the process.
- Memory, stack, heap, and code sections are allocated.
- The process starts in the **ready state**.

---

### 🔹 4. Scheduling and Execution
- **Process Scheduler** selects your program based on priority and scheduling algorithms (like round robin).
- When selected, it enters the **running state** and gets CPU time.
- If another process is running, **context switching** occurs.

---

### 🔹 5. User Input (Keyboard Interaction)
- You enter `2 3` in terminal.
- This triggers **system calls** to read input from keyboard.
- The OS transitions from **user mode to kernel mode** to access I/O hardware.
- Once input is read, it switches back to **user mode**.

---

### 🔹 6. Performing the Addition
- This is a **function call** (i.e., `a + b`), performed purely in **user space**.
- No kernel or system calls involved.
- Fast and handled entirely within the same execution context.

---

### 🔹 7. Displaying Output
- `cout << (a + b)` sends output to terminal.
- This again requires a **system call** (`write()` in Linux, for instance).
- Context switches to kernel mode, writes to the screen, and switches back.

---

### 🔹 8. Termination
- When the program ends (`return 0`), OS:
  - Cleans up memory
  - Updates PCB
  - Frees I/O resources
  - Terminates the process

The process enters the **finished state**.

---

## Case 2: Microsoft Word - Writing a Document

Let’s understand what happens when you're typing in MS Word.

---

### 🔹 1. Program Installation
- Word is a program saved on disk.
- At this stage, it's not doing anything – just like your `.cpp` file.

---

### 🔹 2. Launching MS Word
- Double-clicking Word initiates a **system call** (e.g., `exec`).
- OS creates a **process** and loads MS Word into memory.
- Allocates a **PCB**.
- Multiple **threads** are created:
  - UI Thread
  - Spellcheck Thread
  - Auto-save Thread

---

### 🔹 3. Typing Text
- Each keypress generates a **hardware interrupt**.
- The OS (in kernel mode) handles it and sends the input to the appropriate **Word thread** via **system calls**.
- The thread updates the text buffer (in user mode).

---

### 🔹 4. Auto-save
- A background **thread** periodically saves the document.
- This invokes **system calls** like `open()`, `write()`, etc.
- Switches to kernel mode to interact with file system.

---

### 🔹 5. Spell Checking and Suggestions
- Happens in **multithreading** fashion.
- One thread checks text, another handles input – simultaneously.
- Uses **shared memory**, **concurrency**, and **synchronization** (to avoid race conditions).

---

### 🔹 6. Closing Word
- All processes and threads are terminated.
- OS releases resources.
- PCB, TCB, and memory mappings are cleared.

---

## 🧠 Key OS Concepts Covered

| Concept | Case 1: C++ Addition | Case 2: MS Word |
|--------|----------------------|-----------------|
| **Program vs Process** | `.cpp` → `main.exe` → process | `word.exe` → Word process |
| **PCB / TCB** | 1 PCB, 1 thread | 1 PCB, many threads (UI, save, etc.) |
| **Kernel & User Mode** | Switches during `cin`/`cout` | Frequent switches for I/O, saving |
| **System Calls** | For I/O (`cin`, `cout`) | For file I/O, printing, clipboard |
| **Function Calls** | `add()` in user space | Formatting functions (bold, font) |
| **Scheduling** | Basic CPU scheduling | Multithreading with I/O + UI threads |
| **Multithreading** | No | Yes (heavy use) |
| **Context Switching** | Between program and other tasks | Between UI thread, spellcheck, OS |
| **Modes and Protection** | Controlled via system calls | Applies to all file system operations |

---
