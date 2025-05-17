# 208. Banker's Algorithm

## 📈 What is Banker's Algorithm?

The **Banker's Algorithm** is a **deadlock avoidance** technique used in operating systems. It simulates the allocation of resources and checks if the system will remain in a safe state after the allocation.

Developed by **Edsger Dijkstra**, it mimics a banking system where a banker gives out loans (resources) ensuring the bank can still satisfy the maximum future needs of all clients (processes).

---

## 📃 Key Idea

- Avoid entering **unsafe states** that could lead to **deadlock**.
- Maintain data structures for:
  - `Available[]`
  - `Max[][]`
  - `Allocation[][]`
  - `Need[][] = Max - Allocation`

---

## 🔎 How the Algorithm Works

### 1. **Initialization**
- Set up the matrices:
  - `Available`: Number of instances of each resource type.
  - `Max`: Maximum demand from each process.
  - `Allocation`: Current resource allocation.
  - `Need`: Remaining resource needs.

### 2. **When a Request Comes**
- **Check validity**:
  - Request ≤ Need
  - Request ≤ Available

### 3. **Safety Check**
- Temporarily allocate resources.
- Simulate execution:
  - Check if all processes can complete with current available + released resources.
  - If yes, grant request.
  - If no, roll back and deny the request.

---

## ✅ Safe State Check

The system is in a **safe state** if there exists at least one sequence in which all processes can complete without leading to a deadlock.

---

## 🔧 Resource Allocation Steps

1. Accept request.
2. Check: `Request ≤ Need` and `Request ≤ Available`.
3. Pretend allocation:
   - `Available = Available - Request`
   - `Allocation = Allocation + Request`
   - `Need = Need - Request`
4. Check for a safe sequence:
   - If safe: proceed.
   - If unsafe: rollback.

---

## 📄 Example

### 📈 Given:
- Available = [3, 3, 2]

| Process | Max   | Allocation |
|---------|--------|------------|
| P1      | 7 5 3  | 0 1 0      |
| P2      | 3 2 2  | 2 0 0      |
| P3      | 9 0 2  | 3 0 2      |

### 📋 Request by P1: [1, 0, 2]
- Need P1 = [7-0, 5-1, 3-0] = [7, 4, 3]
- Check:
  - [1, 0, 2] ≤ [7, 4, 3] ✅
  - [1, 0, 2] ≤ [3, 3, 2] ✅
- Temporarily allocate:
  - Available = [2, 3, 0]
- Simulate safe sequence:
  - If found: Grant request.
  - If not: Rollback and deny.

---

> 📘 *The Banker's Algorithm ensures that resource allocation keeps the system in a safe state, thus preventing deadlocks.*
