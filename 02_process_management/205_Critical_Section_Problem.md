# 205 Critical Section Problem

## 🧠 What is a Critical Section?

In **concurrent programming**, a **critical section** is a segment of code that **accesses shared resources**, such as:

- Shared variables
- Data structures
- Files
- Memory

It’s **critical** because simultaneous access by multiple processes/threads can lead to:
- Data inconsistency
- Race conditions
- System crashes

---

## 🚨 The Critical Section Problem

![image](https://github.com/user-attachments/assets/abdef0de-ae2a-4d4a-9cfd-7b20430b166b)

### ❓ What Is the Problem?

When multiple threads/processes need to **access shared resources**, they must **not** access the **critical section simultaneously**.

If the critical section isn't protected:
- One thread may overwrite changes made by another
- Leads to **corrupted data**, **unexpected behavior**

---

## 🧪 Real-Life Analogy

Imagine two people trying to **withdraw money** from a joint account at the same time. Both see `$1000`, both withdraw `$800`, but now the account ends up with `-600` instead of `$200`.  
That’s a **race condition** – no proper locking of the account (resource)!

---

## 🔄 Race Condition

A **race condition** occurs when multiple threads/processes access and modify shared data **simultaneously**, and the **final outcome depends on the timing** of their execution.

### 💡 Example:
```cpp
int counter = 0;

Thread 1: counter++;  // Reads 0, adds 1 → 1
Thread 2: counter++;  // Reads 0, adds 1 → 1

Final value = 1 (but expected 2)
```

## ✅ Requirements for Solving the Critical Section Problem

To handle the critical section properly, a solution must satisfy these **three conditions**:

| Condition           | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **Mutual Exclusion**| Only one process can execute in the critical section at any given time      |
| **Progress**        | If no process is in the critical section, others waiting should be able to enter |
| **Bounded Waiting** | A process must not wait indefinitely to enter its critical section          |

---

## 🔐 Synchronization Techniques

| Mechanism            | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **Mutex / Lock**     | Ensures only one thread can enter the critical section                      |
| **Semaphore**        | Uses counters for resource availability (e.g., binary and counting semaphores) |
| **Monitors**         | High-level constructs for automatic locking/unlocking                       |
| **Atomic Operations**| Hardware-based uninterruptible operations like compare-and-swap             |

---

## 🔒 Deadlock

![image](https://github.com/user-attachments/assets/f07e81f4-2916-48e9-a490-a8be5ebb8901)

### 🧨 What is Deadlock?

A **deadlock** occurs when a group of processes are **waiting on each other indefinitely**, causing none of them to progress.

### 📌 Four Necessary Conditions:

1. **Mutual Exclusion** – A resource can be held by only one process.
2. **Hold and Wait** – A process holds one resource and waits for others.
3. **No Preemption** – A resource cannot be forcibly taken.
4. **Circular Wait** – A cycle of processes exists, each waiting on the next.

---

### 🛠 Deadlock Handling:

- **Prevention** – Eliminate one of the four necessary conditions
- **Avoidance** – Use algorithms like **Banker’s Algorithm**
- **Detection and Recovery** – Detect cycles and recover by killing or rolling back processes

---

## 🕓 Starvation

### ❗ What is Starvation?

**Starvation** occurs when a process waits indefinitely to acquire a resource because other higher-priority processes continuously preempt it.

### 🧪 Example:

In **priority scheduling**, low-priority processes may never run if high-priority processes keep arriving.

### 💉 Solution: **Aging**

Gradually increase the priority of waiting processes over time to ensure they eventually get CPU time.

---

## 🧠 Summary Comparison

| Problem         | Cause                              | Effect                | Solution                         |
|------------------|------------------------------------|------------------------|----------------------------------|
| **Race Condition** | Simultaneous access to shared data | Data inconsistency     | Mutex, semaphores, monitors      |
| **Deadlock**       | Circular wait over resources       | System hangs           | Avoid/Detect/Recover strategies  |
| **Starvation**     | Continuous preemption              | Process waits forever  | Aging, Round Robin               |

---

## 🖼 Diagram

                 Shared Resource
                (e.g., counter++)
                      ▲
                      |
            ---------------------
           |   Critical Section   |
            ---------------------
             ▲               ▲
             |               |
     +---------------+ +---------------+
     |   Thread A    | |   Thread B    |
     +---------------+ +---------------+

Without synchronization: ❌ Race Conditions ❌ Deadlocks ❌ Starvation

With synchronization: ✅ Mutual Exclusion ✅ Data Consistency ✅ Stable Execution
