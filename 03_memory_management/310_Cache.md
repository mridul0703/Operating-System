# Cache

---

## 📌 What is a Cache?

A **cache** is a high-speed memory component designed to store frequently accessed data and instructions to improve system performance by reducing memory access latency. 

![image](https://github.com/user-attachments/assets/0ad624a9-455a-47b2-9da8-65ce5a775599)

Caches are located between the CPU and main memory (RAM) and work on the principle of **locality**:
- **Temporal Locality:** Recently accessed data is likely to be accessed again soon.
- **Spatial Locality:** Data near the recently accessed location is likely to be accessed soon.

---

## 📌 Why is Cache Important?

- **Reduces Latency:** Provides faster access to frequently used data, improving CPU performance.
- **Increases Throughput:** Reduces the need to access slower main memory.
- **Enhances System Efficiency:** Minimises memory bottlenecks, especially in multi-core systems.

---

## 📌 Types of Cache Organisation

### 1. Direct-Mapped Cache
- Each memory block is mapped to a specific cache line.
- Simple and fast, but prone to **cache conflicts**.
- Uses the formula: 
  \[
  \text{Cache Index} = (\text{Memory Address}) \mod (\text{Number of Cache Lines})
  \]

![image](https://github.com/user-attachments/assets/7943d212-f6b6-452b-bf6b-452a79f2d885)

#### 🔹 Example:
- Cache Size: 4 lines
- Memory Addresses: [0, 4, 8, 12, 16]
- All these addresses map to the same cache line, causing frequent replacements.

#### 🔹 Direct-Mapped Cache Illustration:
| Memory Block | Cache Line |
|---------------|-------------|
| 0             | 0           |
| 4             | 0 (Replaces Block 0) |
| 8             | 0 (Replaces Block 4) |
| 12            | 0 (Replaces Block 8) |

---

### 2. Set-Associative Cache
- A combination of direct-mapped and fully-associative caches.
- The cache is divided into **sets**, with each set containing multiple lines.
- A memory block can be placed in any line of a specific set.
- Reduces conflict compared to direct-mapped caches.

#### 🔹 Example:
- Cache Size: 4 lines, 2-way set associative.
- Memory Addresses: [0, 4, 8, 12, 16]
- Addresses 0 and 4 can be placed in either of the two lines of Set 0.

#### 🔹 Set-Associative Cache Illustration:
| Set | Line 0 | Line 1 |
|-----|--------|--------|
| 0   | 0      | 4      |
| 1   | 8      | 12     |

---

### 3. Fully-Associative Cache
- Any memory block can be placed in any cache line.
- Highest flexibility but also the most complex.
- Requires more hardware for tag comparison.

#### 🔹 Example:
- Cache Size: 4 lines
- Memory Addresses: [0, 4, 8, 12, 16]
- All addresses can be placed in any of the 4 cache lines.

#### 🔹 Fully-Associative Cache Illustration:
| Cache Line | Memory Block |
|-------------|---------------|
| 0           | 0             |
| 1           | 4             |
| 2           | 8             |
| 3           | 12            |

---

## 📌 Cache Coherence

In multi-core or multiprocessor systems, each processor may have its own cache. **Cache coherence** ensures that all processors have a consistent view of memory.

![image](https://github.com/user-attachments/assets/4b222b12-d84c-4f43-a11e-5642412380b1)

### 🔹 Common Cache Coherence Protocols:
- **MESI Protocol (Modified, Exclusive, Shared, Invalid)**
- **MOESI Protocol (Modified, Owned, Exclusive, Shared, Invalid)**

### 🔹 How it Works:
- When a processor modifies a value in its cache, other caches are notified.
- The updated value is either propagated to other caches (write-through) or invalidated (write-invalidate).

---

## 📌 Cache Replacement Policies

When a cache is full, a **cache replacement policy** determines which block to evict:

### 1. Least Recently Used (LRU)
- Replaces the cache line that has not been accessed for the longest time.
- Optimal for most access patterns but can be complex to implement.

#### 🔹 Example:
- Cache Size: 4 lines, Access Sequence: [0, 1, 2, 0, 3, 4]
- Replacement Order: [1, 2, 3, 4] (LRU line is replaced first).

---

### 2. First-In, First-Out (FIFO)
- Replaces the cache line that was loaded first.
- Simple but may lead to poor performance in certain scenarios.

#### 🔹 Example:
- Cache Size: 3 lines, Access Sequence: [1, 2, 3, 4]
- Replacement Order: [1, 2, 3] → [2, 3, 4].

---

### 3. Random Replacement
- Selects any cache line at random for replacement.
- Fast and easy to implement but may lead to unpredictable performance.

---

### 4. Least Frequently Used (LFU)
- Replaces the cache line that has been accessed the fewest times.
- Tracks access count for each cache line.

#### 🔹 Example:
- Cache Size: 3 lines, Access Sequence: [1, 2, 3, 1, 4]
- Replacement Order: [2, 3, 4] (Block 2 has the lowest access count).

---

## 📌 Cache Hierarchy in Modern Systems

### 🔹 Multi-Level Cache (L1, L2, L3)
- **L1 Cache:** Fastest but smallest, closest to the CPU.
- **L2 Cache:** Larger but slightly slower, shared between multiple cores.
- **L3 Cache:** Even larger, shared across all CPU cores.

### 🔹 Characteristics:
| Cache Level | Size   | Speed          | Location       |
|--------------|--------|-----------------|-----------------|
| L1           | 32 KB  | Very Fast       | Closest to CPU   |
| L2           | 256 KB | Moderate        | Shared per core  |
| L3           | 8 MB   | Slowest (still fast) | Shared across CPU |

---

## 📌 Cache Performance Metrics

1. **Cache Hit:** When a requested data block is found in the cache.
2. **Cache Miss:** When a requested data block is not found in the cache.
3. **Hit Ratio:** 
   \[
   \text{Hit Ratio} = \frac{\text{Cache Hits}}{\text{Total Accesses}}
   \]
4. **Miss Penalty:** The additional time required to fetch data from main memory when a cache miss occurs.

---

## 📌 Key Takeaways
- Cache is critical for reducing memory access latency and improving CPU performance.
- Different cache organisations (Direct-Mapped, Set-Associative, Fully-Associative) provide varying levels of complexity and performance.
- Efficient cache replacement policies (LRU, FIFO, Random, LFU) optimise cache usage.
- Multi-level cache hierarchy (L1, L2, L3) provides a balance between speed and capacity.

---

> 🚀 *Efficient cache design and management are essential for achieving high-performance computing.* 

