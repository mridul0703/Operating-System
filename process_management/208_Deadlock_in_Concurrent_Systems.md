# 208. Deadlock in Concurrent Systems

## 🧨 What is Deadlock?

**Deadlock** occurs in a concurrent system when a group of processes are each waiting for resources that other processes in the group are holding. This creates a situation where **no process can proceed**, causing the system to freeze.

![image](https://github.com/user-attachments/assets/7e1d359a-0652-4fb8-bc8f-07e960e2e3d9)

---

## 🔁 Deadlock Representation

- Often represented using a **Resource Allocation Graph (RAG)**.
- A **cycle in the graph** indicates a potential deadlock.
- Deadlock signifies:
  - Processes are in an **indefinite wait**.
  - No process can proceed as resources are blocked by others.

---

## ❗ Necessary Conditions for Deadlock

To occur, **all four** of the following must be true:

1. **Mutual Exclusion**  
   A resource can be held by only one process at a time.

2. **Hold and Wait**  
   A process holds one resource and waits for another.

3. **No Preemption**  
   Resources can't be forcibly taken away from a process.

4. **Circular Wait**  
   A cycle exists where each process waits for a resource held by the next.

---

## 🔍 Detecting & Handling Deadlocks

### ✅ Deadlock Prevention

- **Break at least one** of the four necessary conditions.
- Examples:
  - Don’t allow **hold and wait** (use one-shot allocation).
  - Make resources **preemptible**.

### ✅ Deadlock Avoidance

- Dynamically assess future requests.
- Use **Banker’s Algorithm** to avoid unsafe states.

### ✅ Deadlock Detection

- Allow deadlocks to happen.
- Periodically **check for cycles** in the Resource Allocation Graph.
- Apply **recovery methods** upon detection.

### ✅ Deadlock Recovery

- **Terminate** one or more processes.
- **Preempt** resources and reassign.
- Carefully select victims to **minimize impact**.

---

## 🔧 Deadlock Prevention Techniques

### 🧊 One-Shot (All-or-Nothing) Allocation

- Request **all required resources** at once.
- Process proceeds only if all are available.

**Pros:**  
- Simplifies logic and prevents hold-and-wait.
  
**Cons:**  
- Low utilization; starvation risk; hard to predict needs.

---

### 🔁 Preemptive Resource Allocation

- System can **take back** held resources.
- Used to **break circular waits**.

**Pros:**  
- Reduces deadlocks; improves utilization.

**Cons:**  
- Requires saving process state; may degrade performance.

---

## 🍝 Dining Philosophers Problem

A classic problem that models **deadlock risk** in shared resource allocation.

![image](https://github.com/user-attachments/assets/489085b8-96b0-4985-814e-5c36c2996701)

### 🧩 Scenario:

- 5 philosophers sit at a round table.
- 1 fork between each pair.
- To eat, a philosopher must hold **both adjacent forks**.
- Deadlock occurs if each picks up their **left fork** and waits for the right.

### 🛠️ Solutions:

- **Odd-even fork picking order**
- **Limit max simultaneous eaters**
- **Use a waiter process to manage access**

---

> 📘 *Understanding deadlocks is essential for designing robust, deadlock-free concurrent systems. Proper prevention, detection, and recovery strategies ensure system reliability.*
