# 202. Scheduling Algorithms (FCFS, SJF, SRTF, HRNN, RR, MLQ, MLQF)

---

## 🔁 What is CPU Scheduling?

CPU scheduling is the backbone of process management in an OS. It determines **which process gets the CPU next** from the ready queue and for how long. The goal is to:

- Maximise CPU utilisation  
- Minimise waiting and turnaround time  
- Ensure fairness and responsiveness  
- Avoid starvation  

---

## 🔑 Key Terms in CPU Scheduling

| **Term**            | **Definition**                                                               | **Simple Example**                                |
|---------------------|-------------------------------------------------------------------------------|----------------------------------------------------|
| **Burst Time (BT)** | Time required by a process to execute on the CPU                              | If a process needs 5ms to complete, its BT = 5     |
| **Arrival Time (AT)** | Time at which a process enters the ready queue                             | If a process arrives at 2ms, AT = 2                |
| **Completion Time (CT)** | Time at which a process finishes execution                             | If a process finishes at 10ms, CT = 10             |
| **Turnaround Time (TAT)** | Total time taken from arrival to completion <br> **TAT = CT − AT**     | If AT = 2 and CT = 10, then TAT = 8                |
| **Waiting Time (WT)** | Time spent waiting in the ready queue (not executing) <br> **WT = TAT − BT** | If TAT = 8 and BT = 5, then WT = 3                 |
| **Response Time (RT)** | Time from arrival to the first time the CPU starts executing the process <br> **RT = Start Time − AT** | If a process starts at 4 and AT = 2, then RT = 2   |


Schedulers use different **algorithms** to decide this, depending on system goals and process behavior.

---

## 📌 First-Come, First-Served (FCFS)

- **Non-preemptive**  
- The **oldest process** in the ready queue gets executed first.
- Simple **FIFO (First-In, First-Out)** strategy.
  
![image](https://github.com/user-attachments/assets/2e689b7f-ff3d-493e-80d2-967c2172bbb9)

### ✅ Advantages:
- Easy to implement  
- Fair in order of arrival  

### ❌ Disadvantages:
- **Poor average waiting time** if a long job arrives first  
- **Convoy effect**: small jobs wait behind large ones

```
Arrival Time: P1(0), P2(2), P3(4)
Burst Time: P1=8, P2=4, P3=1
Execution Order: P1 → P2 → P3
```

---

## 🔹 Shortest Job First (SJF)

- **Non-preemptive**  
- Picks the process with the **shortest burst time** next  
- Optimal for **minimising average waiting time**

![image](https://github.com/user-attachments/assets/7cef94c4-de2f-4950-8f91-9daf65c84e91)

### ✅ Advantages:
- Efficient use of CPU  
- Minimum average waiting time (theoretically optimal)

### ❌ Disadvantages:
- **Needs prediction** of burst time  
- Can cause **starvation** for long processes

---

## ⏱️ Shortest Remaining Time First (SRTF)

- **Preemptive version of SJF**  
- A new process **preempts** the current one if it has a shorter remaining time

![image](https://github.com/user-attachments/assets/71ec2679-61a6-4493-9c35-4efeca914884)

### ✅ Advantages:
- Minimum average waiting time in practice  
- Prioritises shorter processes dynamically

### ❌ Disadvantages:
- Frequent **context switching** = higher overhead  
- Starvation still possible  
- Complex to predict remaining time accurately

---

## 🔁 Round Robin (RR)

- **Preemptive**
- Each process gets a fixed **time quantum**
- After quantum expires, the process is moved to the back of the queue

![image](https://github.com/user-attachments/assets/4bae25d9-f2d1-422c-b772-c43b9a1f8b9e)

### ✅ Advantages:
- Fairness: every process gets CPU time  
- Suitable for **interactive/time-sharing systems**

### ❌ Disadvantages:
- Performance depends on **time quantum**:  
  - Too small → too many context switches  
  - Too large → behaves like FCFS

---

## 🧠 Highest Response Ratio Next (HRRN)

- **Non-preemptive**
- Selects process with highest response ratio:

Response Ratio (RR) = (Waiting Time + Burst Time) / Burst Time


- Balances **short and long jobs** by adjusting their priority based on wait time.

### ✅ Advantages:
- Eliminates starvation  
- Fairer than SJF  

### ❌ Disadvantages:
- Requires estimating burst time  
- Non-preemptive → less control in real-time scenarios

---

## 🪜 Multilevel Queue (MLQ)

- Divides ready queue into **separate queues** based on process type or priority  
- Each queue has its **own scheduling algorithm**

![image](https://github.com/user-attachments/assets/9f2904f0-9a16-400a-a3c0-ba6270c72fdb)

### Example Queues:
- System processes (priority 1) – FCFS  
- Interactive processes (priority 2) – RR  
- Batch processes (priority 3) – FCFS  

### ✅ Advantages:
- Organised handling of different process types  
- Allows prioritisation  

### ❌ Disadvantages:
- **Rigid**: once in a queue, a process can’t move  
- Starvation for lower-priority queues

---

## 🔄 Multilevel Queue with Feedback (MLFQ)

- Like MLQ, but processes **can move between queues**  
- Based on behaviour or **CPU usage**

![image](https://github.com/user-attachments/assets/edd056bc-b590-4f1d-8986-7e0f951a4bf2)

### Key Concepts:
- Starts in high-priority queue (short quantum)  
- If it uses too much CPU → demoted  
- If it waits too long → promoted

### ✅ Advantages:
- Prevents **starvation**  
- Adapts to process behaviour (dynamic priority)

### ❌ Disadvantages:
- **Complex to implement**  
- Requires proper tuning of demotion/promotion policies

---

## ⚖️ Quick Comparison Table

| Algorithm | Preemptive | Starvation Possible | Fairness | Complexity | Best For |
|----------|------------|---------------------|----------|------------|----------|
| FCFS     | ❌          | ✅ (long jobs early) | ✅        | Low        | Simple systems |
| SJF      | ❌          | ✅                   | ❌        | Medium     | Batch jobs |
| SRTF     | ✅          | ✅                   | ❌        | High       | Real-time |
| HRRN     | ❌          | ❌                   | ✅        | Medium     | Batch, fairness focus |
| RR       | ✅          | ❌                   | ✅        | Medium     | Interactive |
| MLQ      | ✅/❌        | ✅                   | ❌        | High       | OS with different process types |
| MLFQ     | ✅          | ❌                   | ✅        | Very High  | Complex multitasking systems |

---

## 📘 Tip:

In real-world operating systems, **combinations** of these algorithms are often used. For example:

- Linux uses a form of **MLFQ with dynamic priorities**  
- Windows uses **priority-based scheduling with preemption**  
- Real-time OS might prefer **SRTF** or **Rate Monotonic Scheduling**

---
