# 311. Direct and Associative Mapping

---

## 📌 What is Cache Mapping?
Cache mapping is the technique used to determine where a particular block of main memory will be stored in the cache. Two primary cache mapping techniques are:
- **Direct Mapping**
- **Associative Mapping**

---

## 📌 Direct Mapping

![image](https://github.com/user-attachments/assets/8df14324-f562-4667-913b-49746eb8a83d)

### 🔹 Concept of Direct Mapping
- Each memory block is mapped to exactly **one specific location in the cache**.
- The mapping is determined using a modulo operation:
  \[
  \text{Cache Line Number} = (\text{Memory Block Address}) \mod (\text{Number of Cache Lines})
  \]
- The memory address is divided into three fields:
  - **Tag:** Identifies which block is stored in the cache line.
  - **Index:** Identifies the specific cache line.
  - **Block Offset:** Identifies the specific byte within the block.

![image](https://github.com/user-attachments/assets/c3526a3f-df8f-4dc1-a3a7-6d48fa8a514f)

### 🔹 How Direct Mapping Works
- The **Index** field determines the cache line where the data will be stored.
- The **Tag** field is used to verify if the data in the indexed line is valid and corresponds to the requested block.
- If the **Tag** matches, a **cache hit** occurs; otherwise, a **cache miss** occurs.

### 🔹 Example Calculation
- Cache Size: 16 lines
- Memory Block Address: 18
- Calculation:
  \[
  \text{Cache Line} = 18 \mod 16 = 2
  \]
- The block is stored in cache line **2**.

### 🔹 Direct Mapping Illustration:
| Memory Address | Cache Line | Tag | Valid Bit |
|----------------|-------------|-----|------------|
| 18              | 2           | T1  | 1          |
| 34              | 2 (Replaces 18) | T2 | 1          |
| 50              | 2 (Replaces 34) | T3 | 1          |

### 🔹 Advantages of Direct Mapping
- **Simple and Fast:** Easy to implement with minimal hardware.
- **Low Cost:** Requires fewer tag comparisons.

### 🔹 Disadvantages of Direct Mapping
- **High Conflict Misses:** Multiple blocks map to the same cache line, causing frequent replacements (cache thrashing).
- **Limited Flexibility:** Each memory block can only go to a specific cache line.

---

## 📌 Associative Mapping

![image](https://github.com/user-attachments/assets/b740d9f1-0338-4842-92e1-87a7f878813c)

### 🔹 Concept of Associative Mapping
- A memory block can be placed in **any cache line**.
- Requires a **tag comparison** across all cache lines to determine if a block is present.
- Offers greater flexibility and reduces the chances of conflict misses.

### 🔹 How Associative Mapping Works
- Each cache line stores both the **data block** and its **tag**.
- When accessing data, the cache searches all lines for a matching tag.
- If a matching tag is found, it is a **cache hit**.
- If not, it is a **cache miss**, and a replacement policy (like LRU) decides which line to replace.

### 🔹 Example Calculation
- Cache Size: 4 lines (fully associative)
- Memory Block Address: 18, 34, 50, 18
- Since the cache is fully associative:
  - Block 18 can be placed in any of the 4 lines.
  - Block 34 can also be placed in any available line.

### 🔹 Associative Mapping Illustration:
| Cache Line | Tag | Data   |
|-------------|-----|--------|
| 0           | T1  | Block 18 |
| 1           | T2  | Block 34 |
| 2           | T3  | Block 50 |
| 3           | T1  | Block 18 (Re-accessed) |

### 🔹 Advantages of Associative Mapping
- **High Flexibility:** Any block can be placed in any cache line.
- **Reduced Conflict Misses:** No direct mapping constraints.

### 🔹 Disadvantages of Associative Mapping
- **Complex Hardware:** Requires multiple tag comparisons (parallel search).
- **Higher Cost:** Increased power consumption due to complex hardware.

---

## 📌 Comparison Between Direct and Associative Mapping

| Aspect              | Direct Mapping                           | Associative Mapping                      |
|---------------------|-------------------------------------------|-------------------------------------------|
| **Simplicity**       | Simple to implement, minimal hardware.   | Complex due to tag comparison.            |
| **Flexibility**      | Fixed mapping (each block to one line).  | Any block can go to any cache line.       |
| **Conflict Misses**  | High, due to fixed mapping.              | Low, since blocks can be placed anywhere. |
| **Performance**      | May suffer from thrashing.               | Generally higher due to fewer misses.     |
| **Cost and Power**   | Low, due to simple hardware.             | High, due to complex comparison logic.    |

---

## 📌 Hybrid Mapping Technique: Set-Associative Mapping

### 🔹 Concept of Set-Associative Mapping
- Combines the features of both direct and associative mapping.
- The cache is divided into **sets**, and each set contains multiple lines.
- A memory block maps to a specific set but can be placed in **any line within that set**.
- Most modern CPU caches use set-associative mapping.

### 🔹 Example of 2-Way Set-Associative Mapping:
- Cache Size: 4 sets, 2 lines per set.
- Memory Addresses: 18, 34, 50, 66
- Calculation:
  - Address 18 maps to Set 2 (18 % 4).
  - Address 34 also maps to Set 2.
  - Address 50 maps to Set 2.
  - Since it is 2-way, Set 2 can hold two blocks (any of the three).

### 🔹 Set-Associative Mapping Illustration:
| Set | Line 0 (Tag) | Line 1 (Tag) |
|-----|---------------|---------------|
| 0   | -             | -             |
| 1   | -             | -             |
| 2   | T1 (Block 18) | T2 (Block 34) |
| 3   | -             | -             |

---

## 📌 Key Takeaways
- **Direct Mapping:** Simple, fast, but prone to conflict misses.
- **Associative Mapping:** Flexible, fewer misses, but complex and costly.
- **Set-Associative Mapping:** Balances between simplicity and flexibility.

---

> 🚀 *Understanding these cache mapping techniques is essential for designing efficient cache systems and optimizing CPU performance.* 

