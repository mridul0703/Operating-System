# 309. Disk Scheduling

---

## 📌 What is Disk Scheduling?

**Disk Scheduling** is a method used by operating systems to determine the order in which disk I/O requests are processed. The primary objective of disk scheduling is to **minimise the total seek time** (the time required for the disk arm to move to the desired track) and improve the **overall performance of the disk subsystem**.

![image](https://github.com/user-attachments/assets/dfdc8517-ba52-40db-b914-04762bc6ec81)

---

## 📌 Why is Disk Scheduling Important?

- **Optimises Disk Performance:** Minimises seek time, reducing the time it takes to access or write data.
- **Improves System Responsiveness:** Ensures that disk I/O requests are handled efficiently, reducing application wait times.
- **Balances Resource Utilisation:** Prevents any single process from monopolising the disk, ensuring fair access.
- **Enhances Throughput:** Maximises the number of I/O operations completed in a given time.

---

## 📌 Factors Influencing Disk Scheduling

![image](https://github.com/user-attachments/assets/55058b24-e308-4dd1-82fa-945a52d2e2bd)

1. **Seek Time:**
   - Time taken for the disk arm to move to the desired track on the disk platter.
   - Minimising seek time is the primary goal of most disk scheduling algorithms.

2. **Rotational Latency:**
   - Time it takes for the desired sector to rotate under the disk read/write head.
   - This is influenced by the speed of disk rotation (RPM).

3. **Transfer Time:**
   - Time required to read or write data once the disk head is in position.
   - Dependent on the data transfer rate of the disk.

4. **Concurrency and Fairness:**
   - Disk scheduling must balance between optimising performance and ensuring fair access to all processes.

---

## 📌 Types of Disk Scheduling Algorithms

### 1. First-Come, First-Served (FCFS)
- Processes disk I/O requests in the order they arrive.
- **Advantages:** Simple and fair.
- **Disadvantages:** Can lead to high seek times (no optimisation).

![image](https://github.com/user-attachments/assets/63b1e075-9232-4de7-957b-06e1a1315e52)

#### 🔹 Example:
- Requests: [98, 183, 37, 122, 14, 124, 65, 67]
- Initial head position: 53
- Seek Sequence: 53 → 98 → 183 → 37 → 122 → 14 → 124 → 65 → 67
- Total Seek Time: (98-53) + (183-98) + (183-37) + (122-37) + (122-14) + (124-14) + (124-65) + (67-65) = **640**

---

### 2. Shortest Seek Time First (SSTF)
- Selects the request with the shortest seek time from the current head position.
- **Advantages:** Reduces seek time compared to FCFS.
- **Disadvantages:** May cause "Starvation" for requests that are far away.

![image](https://github.com/user-attachments/assets/d130883b-6f0b-4833-90d9-b9b3a65f35d3)

#### 🔹 Example:
- Requests: [98, 183, 37, 122, 14, 124, 65, 67]
- Initial head position: 53
- Seek Sequence: 53 → 65 → 67 → 37 → 14 → 98 → 122 → 124 → 183
- Total Seek Time: (65-53) + (67-65) + (67-37) + (37-14) + (98-14) + (122-98) + (124-122) + (183-124) = **236**

---

### 3. SCAN (Elevator Algorithm)
- The disk arm moves in one direction, servicing requests until it reaches the end, then reverses direction.
- **Advantages:** Avoids starvation, provides balanced performance.
- **Disadvantages:** May cause longer wait times for requests on the far end.

![image](https://github.com/user-attachments/assets/e3779ecd-669c-42c4-bfa6-cfb2ac08328e)

#### 🔹 Example:
- Requests: [98, 183, 37, 122, 14, 124, 65, 67]
- Initial head position: 53, moving right
- Seek Sequence: 53 → 65 → 67 → 98 → 122 → 124 → 183 → 37 → 14
- Total Seek Time: (65-53) + (67-65) + (98-67) + (122-98) + (124-122) + (183-124) + (183-37) + (37-14) = **290**

---

### 4. Circular SCAN (C-SCAN)
- Similar to SCAN, but only moves in one direction and immediately returns to the start.
- **Advantages:** Provides more uniform wait times.
- **Disadvantages:** Longer seek time in some cases.

![image](https://github.com/user-attachments/assets/3528021f-03d4-46f3-a89a-3af4f6547a8c)

#### 🔹 Example:
- Requests: [98, 183, 37, 122, 14, 124, 65, 67]
- Initial head position: 53, moving right
- Seek Sequence: 53 → 65 → 67 → 98 → 122 → 124 → 183 → (End) → 14 → 37
- Total Seek Time: (65-53) + (67-65) + (98-67) + (122-98) + (124-122) + (183-124) + (199-183) + (37-0) + (14-0) = **343**

---

### 5. LOOK Algorithm
- A variation of SCAN but stops when there are no more requests in the current direction.
- **Advantages:** Avoids unnecessary movement to the end of the disk.
- **Disadvantages:** Similar to SCAN, but with less overhead.

![image](https://github.com/user-attachments/assets/c751a53e-cca5-4b9c-b408-8800fd6ecd94)

#### 🔹 Example:
- Requests: [98, 183, 37, 122, 14, 124, 65, 67]
- Initial head position: 53, moving right
- Seek Sequence: 53 → 65 → 67 → 98 → 122 → 124 → 183 → 37 → 14
- Total Seek Time: Same as SCAN → **290**

---

### 6. C-LOOK (Circular LOOK)
- A variation of C-SCAN that only goes to the last request in the direction.
- **Advantages:** Avoids unnecessary seek to the end of the disk.
- **Disadvantages:** May cause slightly longer wait times for some requests.

![image](https://github.com/user-attachments/assets/0cbf7701-c98d-4a8a-947f-de0e9b8a20ec)

#### 🔹 Example:
- Requests: [98, 183, 37, 122, 14, 124, 65, 67]
- Initial head position: 53, moving right
- Seek Sequence: 53 → 65 → 67 → 98 → 122 → 124 → 183 → 14 → 37
- Total Seek Time: (65-53) + (67-65) + (98-67) + (122-98) + (124-122) + (183-124) + (183-14) + (37-14) = **290**

---

## 📌 Disk Scheduling Algorithms Comparison

| Algorithm | Average Seek Time | Starvation | Fairness | Efficiency |
|------------|--------------------|-------------|-----------|-------------|
| FCFS       | High                | No          | Fair      | Low          |
| SSTF       | Low (Best for short) | Yes         | Less Fair | High         |
| SCAN       | Moderate            | No          | Fair      | High         |
| C-SCAN     | Moderate            | No          | Fair      | Moderate     |
| LOOK       | Moderate            | No          | Fair      | Moderate     |
| C-LOOK     | Moderate            | No          | Fair      | Moderate     |

---

## 📌 Key Takeaways
- Disk scheduling optimises the performance of the disk subsystem by minimising seek time.
- Different algorithms have different strengths and weaknesses.
- Selecting the right algorithm depends on the workload and system requirements.

---

> 🚀 *Efficient disk scheduling is essential for maintaining high-performance I/O operations and ensuring smooth system performance.*

