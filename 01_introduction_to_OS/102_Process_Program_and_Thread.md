# 102. Process, Program and Thread

## 🧠 What’s the Difference?

Understanding the distinction between **programs**, **processes**, and **threads** is crucial for grasping how modern operating systems work.

---

### 📘 Program

- A **program** is a **static** set of instructions written to perform a specific task.
- It exists as a file stored on disk (e.g., `.exe`, `.sh`, `.py`).
- It does **not** execute by itself—it needs to be run.

> **Example**:  
> `MS Word.exe` on your desktop is a **program**. It just sits there until you double-click it.

---

### ⚙️ Process

- A **process** is the **active execution** of a program.
- Once a program is launched, it becomes a **process** and is loaded into memory.
- The OS allocates resources (CPU time, memory, I/O access) for the process.
- Each process is isolated and managed by the OS.

> **Example**:  
> When you open MS Word, the `.exe` becomes a running **process** in RAM.

---

### 🔄 Thread

- A **thread** is the smallest unit of execution within a process.
- Threads share the same memory and resources of the parent process.
- Multiple threads allow a process to do several things at once (multithreading).
- Threads improve performance and responsiveness.

> **Example**:  
> In a browser:
> - One thread loads the webpage.  
> - Another handles user interaction.  
> - Another runs video or audio playback.

---

## 🧪 Analogy: Kitchen Example

- **Program**: A recipe book waiting to be used.  
- **Process**: The actual cooking based on a selected recipe.  
- **Thread**: The helpers doing specific jobs like chopping, stirring, or serving.

---

> 📝 *Understanding this trio is key to learning process scheduling, synchronization, and memory management later in OS!*
