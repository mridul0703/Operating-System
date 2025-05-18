# 303. Contiguous Allocation, Paging, and Segmentation

---

## 📌 Contiguous Memory Allocation

**Contiguous Memory Allocation** is a memory management technique where each process is allocated a single continuous block of memory. This approach is simple and efficient in terms of access speed because the CPU can easily calculate the address of any location within the block.

### 🌐 Key Characteristics:
- Each process occupies a single block of contiguous memory.
- Memory blocks are allocated using strategies like **First-Fit**, **Best-Fit**, or **Worst-Fit**.
- Access speed is fast due to the continuous nature of the block.

### ⚠️ Fragmentation Issues:
- **External Fragmentation**: Occurs when free memory is available but in non-contiguous blocks, making it difficult to allocate large blocks.
- **Internal Fragmentation**: Happens when allocated blocks are slightly larger than requested, leading to wasted space.

![image](https://github.com/user-attachments/assets/7903264e-1353-4ba2-9da4-0aa9da800e94)

---

## 📌 Paging

**Paging** is a memory management technique that eliminates the need for contiguous allocation of physical memory. It divides memory into fixed-size blocks:

- **Physical Memory (RAM)** is divided into fixed-size blocks called **frames**.
- **Logical Memory (used by processes)** is divided into blocks of the same size called **pages**.
- The operating system maintains a **page table** that maps logical pages to physical frames.

### 🌟 Advantages of Paging:
- Eliminates external fragmentation.
- Pages can be placed anywhere in physical memory.
- Fixed-size pages simplify memory management.
- Allows larger programs to run on limited physical memory (through virtual memory).

### ⚠️ Disadvantages of Paging:
- Requires a **page table for each process**, consuming memory.
- Each memory access involves a **page table lookup**, which can slow performance.
- May cause **internal fragmentation** due to unused space in the last page of a process.

---

## 📋 Page Table Structure

The **Page Table** is a data structure used to store the mapping between logical addresses (pages) and physical addresses (frames). Each entry in the page table represents:

- The **page number** in logical memory.
- The corresponding **frame number** in physical memory.

### Types of Page Tables:
- **Single-Level Page Table**: A simple array of mappings, but can become large for extensive address spaces.
- **Multi-Level Page Table**: Breaks the page table into smaller tables, reducing memory usage.
- **Inverted Page Table**: Stores a single entry for each frame, making it more memory-efficient for large systems.

---

## 📌 Segmentation: Concept and Organization

**Segmentation** is a memory management technique that divides a process's memory into variable-sized segments, each representing a logical unit such as:

- Functions
- Arrays
- Data structures

![image](https://github.com/user-attachments/assets/37238fb5-ec54-4df8-9518-731a4c229483)

### 🌐 How Segmentation Works:
- Each segment has a **segment number** and a **length**.
- Memory addresses within a segment are specified by an **offset** from the segment's base address.
- The operating system uses a **Segment Table** to track each segment’s base address and length.

### 🌟 Advantages of Segmentation:
- Enhances program readability and manageability.
- Each segment can have its own access rights, improving security.
- Reduces wasted space within segments.

### ⚠️ Disadvantages of Segmentation:
- Can suffer from **external fragmentation**.
- Requires complex algorithms for memory allocation and deallocation.

---

## 🔍 Paging vs Segmentation

| Feature              | Paging                                          | Segmentation                                      |
|----------------------|-------------------------------------------------|---------------------------------------------------|
| Memory Division       | Fixed-sized blocks called pages                 | Variable-size blocks called segments               |
| Physical Memory       | Divided into frames of the same size as pages   | Divided into segments of varying sizes             |
| Address Structure     | Single-level address (page number + offset)     | Two-level address (segment number + offset)        |
| Fragmentation         | Eliminates external, may cause internal         | Can lead to external, no internal fragmentation    |
| Logical Division      | Not based on logical structure                   | Matches logical structure (functions, arrays)      |
| Ease of Management    | Simpler due to fixed-size pages                  | More complex due to variable-size segments         |
| Protection & Sharing  | Easier to manage at page level                   | More intuitive but complex                         |
| Memory Access         | Uniform size ensures consistent access time     | Variable sizes can lead to varying access times    |
| Use Case              | Common in modern OS                             | Less common, used for logical structure needs      |

---

> 📘 *Contiguous allocation, paging, and segmentation are fundamental memory management techniques, each with its own advantages and trade-offs. Understanding them is crucial for efficient memory management in operating systems.*
