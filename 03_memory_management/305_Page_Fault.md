# 305. Page Fault

---

## 📌 What is a Page Fault?

A **Page Fault** is an exception that occurs when a program attempts to access a memory page that is **not currently present in physical memory (RAM)**. It is a fundamental aspect of **virtual memory systems**, where memory is divided into fixed-size blocks called **pages**.

### 🌐 How Page Faults Work:
- Programs use **virtual memory addresses**, which may not always map to physical memory.
- When a program accesses a page not currently in RAM, a **page fault** occurs.
- The **operating system (OS)** intervenes to load the required page from secondary storage (like a hard disk or SSD) into RAM.

---

## 📌 Causes of Page Faults

### 📍 1. Demand Paging
- Most operating systems use **demand paging**, where pages are loaded into RAM **only when they are actively used**.
- If a process tries to access a page not in memory, a **page fault** triggers the OS to load it.

![image](https://github.com/user-attachments/assets/244c4a33-a3e8-42b7-9ad6-9dcb54da391d)

### 📍 2. Page Replacement
- If physical memory is full, the OS must choose a page to evict (remove) to make space for the new page.
- Replacement is managed by algorithms such as:
  - **Least Recently Used (LRU)**
  - **First-In, First-Out (FIFO)**
  - **Optimal Page Replacement**

### 📍 3. Copy-on-Write (COW)
- Multiple processes can share the same memory page until one attempts to modify it.
- When a modification is requested, the page is copied for the modifying process, causing a **page fault**.

---

## 📌 How Page Faults are Handled

![image](https://github.com/user-attachments/assets/da624179-03d1-4073-b98b-5d7926334fcb)

### 🔧 Steps for Handling a Page Fault:
1. **Page Table Lookup**:
   - The OS checks the page table of the process to determine if the accessed address is valid.
   - If the page is not in RAM, the OS verifies if it is in secondary storage (disk).

2. **Disk Access**:
   - If the page is not in RAM, the OS reads it from secondary storage (swap space or page file).
   - The page is loaded into an available frame in physical memory.

3. **Page Table Update**:
   - The OS updates the page table to reflect that the page is now in physical memory.
   - The entry is marked as "present" in RAM.

4. **Resuming Execution**:
   - The OS restarts the instruction that caused the page fault.
   - The process can now access the required page.

---

## 🌟 Types of Page Faults

- ✅ **Minor (Soft) Page Fault**:
  - Occurs when the page is not in the process's working set but is still in physical memory.
  - No disk access is required.

- ❌ **Major (Hard) Page Fault**:
  - Occurs when the page is not in physical memory and must be loaded from secondary storage.
  - Involves disk access, making it slower.

- ❌ **Invalid Page Fault**:
  - Happens if the process tries to access an invalid memory address (one that does not exist in the process's logical address space).
  - Typically leads to an error or process termination.

---

## 📌 Impact of Page Faults on System Performance

- Page faults introduce **latency**, as the OS must load pages from slower secondary storage.
- Frequent page faults can lead to:
  - Reduced CPU utilization (as the CPU waits for memory).
  - Slower program execution (due to repeated page swaps).
  - **Thrashing**: A condition where the system spends most of its time handling page faults instead of executing processes.

### 🌐 Factors Affecting Page Fault Rate:
- **Memory Size**: More physical memory reduces the chance of page faults.
- **Page Replacement Algorithm**: Efficient algorithms minimize unnecessary page replacements.
- **Application Behavior**: Programs with large memory footprints are more likely to cause page faults.
- **Disk Speed**: Faster storage (SSD vs HDD) reduces page fault latency.

---

## 📌 Optimizing Page Fault Management

To minimize the impact of page faults, operating systems use various techniques:

- 📊 **Efficient Page Replacement Algorithms**:
  - Least Recently Used (LRU)
  - First-In, First-Out (FIFO)
  - Optimal Page Replacement (theoretical)

- ⚡ **Disk Caching**:
  - Frequently used pages are cached for faster access.

- 🚀 **Prefetching Strategies**:
  - Anticipating and loading pages before they are needed.

- 🛠️ **System Configuration Tuning**:
  - Adjusting the size of the page file or swap space.
  - Modifying process priorities to balance memory usage.

---

> 📘 *Page faults are a crucial part of virtual memory systems, providing the illusion of a larger memory space than physically exists. However, efficient management is essential to maintain system performance.*
