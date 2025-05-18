# 403. File Allocation and Deallocation

---

## 📌 File Allocation Methods
File allocation refers to the strategy used to store files on a storage device. Different allocation methods offer various trade-offs between performance, flexibility, and complexity.

![image](https://github.com/user-attachments/assets/def9bdcd-f546-411f-a5fd-c3520b3cf635)

---

### 🔹 Contiguous Allocation
- **Definition:** Stores a file in a single contiguous block of disk space.
- ✅ **Advantages:** 
  - Fast sequential access (all data is in one place).
  - Simple to implement.
- ❌ **Disadvantages:**
  - Prone to **external fragmentation** (scattered free space).
  - Difficult to resize files without enough contiguous space.
- 🚀 **Best for:** Static files with minimal modification (e.g., CD-ROMs).

---

### 🔹 Linked Allocation
- **Definition:** Stores file blocks in non-contiguous locations, with each block containing a pointer to the next block.
  ![image](https://github.com/user-attachments/assets/2e45c7f8-25b7-46b6-af1a-7689aea097d4)

- ✅ **Advantages:** 
  - No external fragmentation.
  - Easy to resize files (just add new blocks).
- ❌ **Disadvantages:**
  - Sequential access is slower (must follow pointers).
  - Random access is inefficient (must traverse the chain).
- 🚀 **Best for:** Systems with frequent file creation, deletion, or resizing.

---

### 🔹 Indexed Allocation
- **Definition:** Uses an index block containing pointers to all file blocks, enabling direct access.
  ![image](https://github.com/user-attachments/assets/00113c1e-dc5f-40ed-9b91-0a3f8be6940f)

- ✅ **Advantages:** 
  - Efficient random access (directly access any block).
  - No external fragmentation.
- ❌ **Disadvantages:**
  - Index block consumes additional space.
  - Complex management for very large files.
- 🚀 **Best for:** Systems requiring efficient random access (e.g., databases, OS files).

---

### 🔹 File Allocation Table (FAT)
- **Definition:** A table-based method where a central table (FAT) maintains pointers to file blocks.
  ![image](https://github.com/user-attachments/assets/b1488dd6-5c87-4618-8679-51391730c691)

- ✅ **Advantages:** 
  - Simple and widely compatible.
  - Easy to navigate file blocks using the table.
- ❌ **Disadvantages:**
  - Suffers from fragmentation (both internal and external).
  - Less efficient for large disks (table grows in size).
- 🚀 **Best for:** Removable storage devices (USB drives, memory cards).

---

## 📌 Comparison of File Allocation Methods

| Aspect                 | Contiguous Allocation | Linked Allocation | Indexed Allocation | FAT              |
|------------------------|-------------------------|--------------------|---------------------|-------------------|
| **Ease of Implementation** | Simple                  | Moderate            | Complex              | Simple             |
| **Sequential Access**     | High                    | Moderate            | High                 | Moderate           |
| **Random Access**         | Low                     | Low                 | High                 | Moderate           |
| **Fragmentation**         | High (External)         | Low                  | Low                  | Moderate to High   |
| **Space Utilisation**     | Low (due to gaps)       | Moderate             | High                 | Moderate           |
| **File Resizing**         | Low                     | High                 | High                 | Moderate           |

---

## 📌 File Deallocation Strategies
File deallocation involves reclaiming space previously used by files that are no longer needed.

### 🔹 Immediate Deallocation
- **Definition:** Space is instantly reclaimed when a file is deleted.
- ✅ **Advantages:** Space is quickly made available.
- ❌ **Disadvantages:** Can cause fragmentation without careful management.
- 🚀 **Best for:** Systems where immediate space availability is critical.

---

### 🔹 Delayed Deallocation
- **Definition:** Space is not immediately freed. Instead, it is marked for deletion and reclaimed later.
- ✅ **Advantages:** Reduces fragmentation, improves performance.
- ❌ **Disadvantages:** Requires periodic cleanup.
- 🚀 **Best for:** Systems with scheduled maintenance (e.g., SSDs).

---

### 🔹 Garbage Collection
- **Definition:** Periodically scans storage to identify and reclaim unused space.
- ✅ **Advantages:** Optimises storage and performance.
- ❌ **Disadvantages:** Requires background processing.
- 🚀 **Best for:** Flash-based storage (SSDs, eMMC).

---

### 🔹 Reference Counting
- **Definition:** Keeps track of the number of references to each file/block. Space is freed only when the count reaches zero.
- ✅ **Advantages:** Prevents premature deletion of shared data.
- ❌ **Disadvantages:** Overhead of maintaining reference counts.
- 🚀 **Best for:** Systems with shared files (e.g., cloud storage).

---

### 🔹 Deferred Deletion with Secure Wipe
- **Definition:** Files are marked for deletion, but their data is securely overwritten before space is freed.
- ✅ **Advantages:** Enhances security (prevents data recovery).
- ❌ **Disadvantages:** Increases deletion time.
- 🚀 **Best for:** Systems handling sensitive data.

---

## 📌 Key Takeaways
- File allocation determines how files are stored on disk, affecting performance and storage efficiency.
- Different allocation methods suit different use cases:
  - **Contiguous Allocation:** Fast for static, unchanging files.
  - **Linked Allocation:** Flexible for frequently modified files.
  - **Indexed Allocation:** Efficient for large files with random access.
  - **FAT:** Simple, widely compatible but less efficient for large disks.
- File deallocation strategies ensure efficient space reclamation and prevent data loss.

---

> 🚀 *Choosing the right allocation and deallocation methods is crucial for optimising file system performance and ensuring efficient storage management.*

