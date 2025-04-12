# 201. Process Scheduling Algorithm (Pre-emptive and Non-Preemptive)

---

## 🧠 What is Process Scheduling?

Process Scheduling is a key aspect of operating system design. It handles the efficient allocation of system resources like CPU time and memory to multiple processes or threads running at the same time. It ensures processes are executed in a way that optimises system performance, resource utilisation, and user responsiveness.

![image](https://github.com/user-attachments/assets/dec8b457-001e-4421-852d-595b9be50575)

### 📌 Process Scheduling Illustration

This mechanism allows the operating system to select a process from the **ready queue** and give it CPU time for execution. It decides:

- Which process should run next  
- How long it should run  
- When to preempt or suspend it to let other processes execute  

---

## 🔄 Pre-emptive and Non-Preemptive Scheduling

### 🔹 Preemptive Scheduling

In **Preemptive Scheduling**, the operating system **can interrupt** a currently running process and give the CPU to another process. This can happen if:

- A **higher-priority process** arrives  
- The **timer expires** (time slice is over)  
- An event needing immediate attention occurs  

Processes may be **suspended even without voluntarily yielding** the CPU.

#### ✅ Advantages

- Better **responsiveness**
- **Fair allocation** of CPU
- Supports **real-time** and multitasking systems
  
![image](https://github.com/user-attachments/assets/1aadb507-7927-4bdb-abe4-7782f2e62679)

---

### 🔹 Non-Preemptive Scheduling

In **Non-Preemptive Scheduling**, a process **keeps the CPU** until:

- It **completes** execution  
- It **waits for I/O**  
- It **yields** voluntarily  

No external process can interrupt it during execution.

#### ✅ Advantages

- **Simpler to implement**
- Lower overhead
- **Predictable** behavior (ideal for batch or embedded systems)

![image](https://github.com/user-attachments/assets/ad445655-c070-4025-98a7-10191bba39b0)

---

## 🔍 Comparison: Preemptive vs Non-Preemptive

| Aspect                | Preemptive                            | Non-Preemptive                         |
|-----------------------|----------------------------------------|----------------------------------------|
| **Interruption**      | Yes, can be interrupted                | No, runs to completion                 |
| **CPU Control**       | OS controls                            | Process retains control                |
| **Response Time**     | Shorter                                | May be longer                          |
| **Fairness**          | More fair                              | Less fair in long processes            |
| **Complexity**        | Higher (dynamic switching)             | Lower (sequential)                     |
| **Resource Use**      | More efficient                         | Can lead to inefficiencies             |
| **Best For**          | Multitasking, real-time systems        | Batch systems, embedded controllers    |

---

## 🌐 Real-World Examples

### 🟩 Preemptive Scheduling

- **Modern OS**: Windows, macOS, Linux  
- **Real-Time Systems**: Automotive ECU for quick brake or airbag response  
- **Servers**: Handle multiple clients simultaneously  

### 🟨 Non-Preemptive Scheduling

- **Embedded Systems**: Simpler IoT devices, industrial controllers  
- **Batch Processing**: Payroll or report generation systems  
- **Single-user PCs**: Running predictable workloads  

---
