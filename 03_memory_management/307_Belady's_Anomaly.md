# 307. Belady's Anomaly

---

## 📌 What is Belady's Anomaly?

**Belady's Anomaly** is a counterintuitive phenomenon in page replacement algorithms where **increasing the number of page frames** allocated to a process can lead to an **increase in the number of page faults**, rather than a decrease as expected.

This anomaly is primarily observed in the **First-In-First-Out (FIFO)** page replacement algorithm.

![image](https://github.com/user-attachments/assets/44f754a4-1f0b-46f4-9d69-6dd9b58f5529)

---

## 📌 Why Belady's Anomaly Occurs?

- **Page Replacement Policy:** Belady's Anomaly is caused by the limitations of certain page replacement algorithms (like FIFO) that do not consider future access patterns.
- **Evicting Frequently Used Pages:** FIFO may evict a page that will soon be used again, even if more frames are available.
- **Lack of Future Access Awareness:** FIFO relies solely on the order of page entry, without understanding which pages are critical.

---

## 📌 Example: Belady's Anomaly with FIFO

### 🔹 Given:
- **Page Reference String:** `1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5`
- **Frames:** 3 and 4

### ✅ Using FIFO with 3 Frames:

| Step | Pages in Frames | Fault? |
|------|------------------|--------|
| 1    | 1 _ _            | ✅     |
| 2    | 1 2 _            | ✅     |
| 3    | 1 2 3            | ✅     |
| 4    | 4 2 3            | ✅     |
| 5    | 4 1 3            | ✅     |
| 6    | 4 1 2            | ✅     |
| 7    | 5 1 2            | ✅     |
| 8    | 5 1 2            | ❌     |
| 9    | 5 1 2            | ❌     |
| 10   | 3 1 2            | ✅     |
| 11   | 3 4 2            | ✅     |
| 12   | 3 4 5            | ✅     |

- **Total Page Faults with 3 Frames:** 9

### ✅ Using FIFO with 4 Frames:

| Step | Pages in Frames  | Fault? |
|------|-------------------|--------|
| 1    | 1 _ _ _           | ✅     |
| 2    | 1 2 _ _           | ✅     |
| 3    | 1 2 3 _           | ✅     |
| 4    | 1 2 3 4           | ✅     |
| 5    | 1 2 3 4           | ❌     |
| 6    | 1 2 3 4           | ❌     |
| 7    | 5 2 3 4           | ✅     |
| 8    | 5 1 3 4           | ✅     |
| 9    | 5 1 2 4           | ✅     |
| 10   | 5 1 2 3           | ✅     |
| 11   | 4 1 2 3           | ✅     |
| 12   | 4 5 2 3           | ✅     |

- **Total Page Faults with 4 Frames:** 10

### 🔎 Analysis:
- With **3 Frames:** 9 page faults.
- With **4 Frames:** 10 page faults.
- **Belady's Anomaly Occurs:** More frames caused more page faults.

---

## 📌 Causes of Belady's Anomaly

1. **FIFO Page Replacement:** FIFO does not account for future page usage and simply evicts the oldest page.
2. **Lack of Temporal Locality:** Pages that will be reused soon are evicted, causing additional page faults.
3. **Increased Frames without Optimization:** More frames provide more options for replacement, increasing the chances of a poor decision.

![image](https://github.com/user-attachments/assets/57e58f04-208a-4fdd-946c-ec873ef1109e)

---

## 📌 How to Avoid Belady's Anomaly?

- Use page replacement algorithms that consider page access frequency:
  - **Least Recently Used (LRU):** Replaces the page that has not been used for the longest time.
  - **Optimal Algorithm (OPT):** Replaces the page that will not be used for the longest time in the future (theoretical best).
  - **Clock (Second Chance) Algorithm:** A modified FIFO that gives pages a second chance before eviction.
- Monitor system performance and adjust the page replacement policy dynamically.

---

## 📌 Key Takeaways
- Belady's Anomaly highlights the **limitations of FIFO** and similar simple page replacement algorithms.
- More frames do not always guarantee better performance.
- Selecting an efficient page replacement algorithm is crucial for **optimizing system performance**.

---

> 🚀 *Understanding Belady's Anomaly is crucial for designing efficient memory management systems and choosing the right page replacement strategy for optimal performance.*

