# 103. Multithreading

## 🔄 What is Multithreading?

**Multithreading** is the ability of a process to execute **multiple threads** concurrently, allowing it to perform multiple tasks at the same time within the **same program**.

Each **thread** runs independently but shares the **same memory and resources** of the parent process.

---

## 🧠 Why Use Multithreading?

- ✅ Improves application responsiveness  
- ✅ Utilizes CPU more efficiently  
- ✅ Enables parallelism in multi-core systems  
- ✅ Reduces resource consumption (compared to multiple processes)

---

## ⚙️ How it Works

- A **single process** can have **multiple threads**.
- All threads **share the same address space**.
- Threads can communicate easily (but must be synchronized properly).
- If one thread crashes, it can affect the whole process.

---

## 🌐 Real-Life Examples

- **Web Browser**:  
  - One thread renders UI  
  - One thread downloads data  
  - One thread plays media

- **Text Editor**:  
  - One thread handles typing  
  - One thread checks grammar/spelling  
  - One thread autosaves document

---

## 🧪 Analogy: Restaurant Kitchen

- **Process** = The restaurant.  
- **Threads** = The staff members (chef, waiter, cashier).  
- All work under the same roof and share kitchen tools and ingredients.

---

## ⚠️ Challenges in Multithreading

- **Race Conditions**: Two threads modify the same data at once.  
- **Deadlocks**: Two threads wait on each other forever.  
- **Context Switching**: Switching between threads takes CPU time.  
- **Debugging**: Harder to find bugs due to non-deterministic behavior.

---

## 🧩 Key Terms

- **Concurrency**: Multiple threads progress independently.
- **Parallelism**: Threads run truly simultaneously on multiple cores.
- **Synchronization**: Ensures correct access to shared data.
- **Thread-safe**: Code that works correctly in multithreaded environments.

---

> 💡 *Multithreading is essential for building fast, efficient, and scalable software — but it requires careful design and synchronization!*
