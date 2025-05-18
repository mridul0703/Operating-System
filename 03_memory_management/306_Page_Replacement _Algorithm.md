# 306. Page Replacement Algorithm

---

## 📌 What is Page Replacement?

**Page Replacement** is a process in virtual memory management where an operating system decides which memory page to remove from physical memory (RAM) to make room for a new page. It is necessary when physical memory is full, and a new page needs to be loaded due to a **page fault**.

### 🔧 How Page Replacement Works:
1. A **page fault** occurs when a required page is not in physical memory.
2. If RAM is full, the OS must select a **victim page** to evict (remove).
3. The new page is loaded into the freed space.
4. The page table is updated to reflect the changes.

---

## 📌 Types of Page Replacement Algorithms

### 1. 🔹 First-In-First-Out (FIFO) Algorithm
- Replaces the **oldest page** in memory (the one that entered first).
- Uses a **queue structure** where the oldest page is at the front.

#### 📝 Example:
- Page Reference String: **7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2**
- Frames: **3**

| Step | Pages in Frames | Fault? |
|------|------------------|--------|
| 1    | 7 _ _            | ✅     |
| 2    | 7 0 _            | ✅     |
| 3    | 7 0 1            | ✅     |
| 4    | 2 0 1            | ✅     |
| 5    | 2 0 1            | ❌     |
| 6    | 2 0 3            | ✅     |
| 7    | 2 0 3            | ❌     |
| 8    | 4 0 3            | ✅     |
| 9    | 4 2 3            | ✅     |
| 10   | 4 2 3            | ❌     |
| 11   | 0 2 3            | ✅     |
| 12   | 0 2 3            | ❌     |
| 13   | 0 2 3            | ❌     |

- **Page Faults**: 9
- **Observation**: FIFO may cause **Belady’s Anomaly** (increased page faults with more frames).

---

### 2. 🔹 Least Recently Used (LRU) Algorithm
- Replaces the **least recently used page** in memory.
- Tracks page usage history (typically using a stack or a counter).

#### 📝 Example:
- Page Reference String: **7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2**
- Frames: **3**

| Step | Pages in Frames | Fault? |
|------|------------------|--------|
| 1    | 7 _ _            | ✅     |
| 2    | 7 0 _            | ✅     |
| 3    | 7 0 1            | ✅     |
| 4    | 2 0 1            | ✅     |
| 5    | 2 0 1            | ❌     |
| 6    | 2 0 3            | ✅     |
| 7    | 2 0 3            | ❌     |
| 8    | 4 0 3            | ✅     |
| 9    | 4 2 3            | ✅     |
| 10   | 4 2 3            | ❌     |
| 11   | 0 2 3            | ✅     |
| 12   | 0 2 3            | ❌     |
| 13   | 0 2 3            | ❌     |

- **Page Faults**: 8
- **Observation**: LRU generally performs better than FIFO.

---

### 3. 🔹 Optimal (OPT) Algorithm
- Replaces the page that will **not be used for the longest time** in the future.
- It is a **theoretical best** (requires knowledge of future accesses).

#### 📝 Example:
- Page Reference String: **7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2**
- Frames: **3**

| Step | Pages in Frames | Fault? |
|------|------------------|--------|
| 1    | 7 _ _            | ✅     |
| 2    | 7 0 _            | ✅     |
| 3    | 7 0 1            | ✅     |
| 4    | 2 0 1            | ✅     |
| 5    | 2 0 1            | ❌     |
| 6    | 2 0 3            | ✅     |
| 7    | 2 0 3            | ❌     |
| 8    | 4 0 3            | ✅     |
| 9    | 4 2 3            | ✅     |
| 10   | 4 2 3            | ❌     |
| 11   | 4 2 0            | ✅     |
| 12   | 4 2 0            | ❌     |
| 13   | 4 2 0            | ❌     |

- **Page Faults**: 7
- **Observation**: Optimal has the **fewest page faults**.

---

## 📌 Comparison of Page Replacement Algorithms

| Algorithm | Principle                     | Advantages                | Disadvantages                 |
|------------|-------------------------------|----------------------------|--------------------------------|
| FIFO        | Replace oldest page           | Simple and easy to implement| May cause Belady’s Anomaly     |
| LRU         | Replace least recently used   | Good performance in practice| High overhead (tracking usage) |
| Optimal     | Replace page not needed soon | Best theoretical performance| Not practical (future knowledge)|

---

## 📌 Practical Considerations for Page Replacement

- Choosing the right algorithm depends on:
  - **Access Pattern**: Frequent reuse favors LRU.
  - **System Constraints**: Limited memory may benefit from FIFO.
  - **Performance Needs**: High-performance systems may use hybrid approaches.

- Real operating systems use more sophisticated methods like:
  - **Clock (Second Chance) Algorithm**
  - **Enhanced Second Chance Algorithm**
  - **Least Frequently Used (LFU) Algorithm**

---

> 📘 *Efficient page replacement is crucial for maintaining system performance in virtual memory environments. The choice of algorithm can significantly impact how well a system handles page faults and manages available memory.*

