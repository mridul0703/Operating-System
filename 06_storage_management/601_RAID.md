# 601. RAID and Its Types

---

## What is RAID?

**RAID** (Redundant Array of Independent Disks) is a data storage technology that combines multiple physical disk drives into one logical unit to:

- Improve performance (speed)
- Provide redundancy (fault tolerance)
- Or both

Originally called "Redundant Array of Inexpensive Disks," it’s now known as "Independent Disks" to emphasize drive independence.

RAID is widely used in servers, workstations, and storage systems to enhance data reliability and access speed.

![image](https://github.com/user-attachments/assets/2296fa7f-ef25-47a2-83d2-915239f20069)

---

## Common RAID Levels

### RAID 0 (Striping)

- **How it works:** Data is split (striped) into blocks and distributed across multiple disks.
- **Advantage:** Significantly improves read/write performance by parallelizing operations.
- **Disadvantage:** No redundancy; if one disk fails, all data is lost.
- **Use cases:** High-speed requirements like video editing, gaming.
- **Storage efficiency:** 100% of total disk capacity.
  
---

### RAID 1 (Mirroring)

![image](https://github.com/user-attachments/assets/95e9f5c6-3c7e-42ba-a824-4c1fcd27d862)

- **How it works:** Data is duplicated identically on two or more disks.
- **Advantage:** Provides full redundancy; can tolerate disk failure.
- **Disadvantage:** Storage capacity is halved due to duplication.
- **Use cases:** Critical data storage like databases, financial records.
- **Performance:** Improved read speed (reads from either disk), write speed similar to a single disk.

---

### RAID 5 (Striping with Parity)

![image](https://github.com/user-attachments/assets/9310d17a-71e2-4ee2-9be8-9f79d028f742)

- **How it works:** Data and parity info are striped across multiple disks; parity helps recover data if one disk fails.
- **Advantage:** Good balance of performance, redundancy, and storage efficiency.
- **Disadvantage:** Write operations slower due to parity calculation overhead.
- **Use cases:** File servers, backup systems.
- **Storage efficiency:** Capacity of (N-1) disks, where N = total disks.

---

### RAID 10 (Striping + Mirroring)

![image](https://github.com/user-attachments/assets/6cdd48f6-31e4-49a3-a8c6-f9223453a6cc)

- **How it works:** Combines RAID 0 striping and RAID 1 mirroring.
- **Advantage:** High performance and fault tolerance.
- **Disadvantage:** Storage capacity halved due to mirroring.
- **Use cases:** Mission-critical applications requiring high availability and speed (e.g., transactional databases).
- **Fault tolerance:** Can sustain multiple disk failures if not both disks in a mirrored pair fail.

---

## RAID Summary Table

| RAID Level | Technique         | Fault Tolerance         | Performance         | Storage Efficiency     | Use Cases                        |
|------------|-------------------|-------------------------|---------------------|------------------------|---------------------------------|
| RAID 0     | Striping          | None                    | Highest read/write  | 100% capacity          | Video editing, gaming            |
| RAID 1     | Mirroring         | High (1 disk failure)   | Good read, normal write | 50% capacity          | Critical data, databases         |
| RAID 5     | Striping + Parity | Can tolerate 1 disk failure | Good read, slower writes | (N-1)/N capacity       | File servers, backups            |
| RAID 10    | Striping + Mirroring | High (multiple failures) | High read/write    | 50% capacity           | High-performance, critical apps |

---

## Choosing RAID

- **RAID 0:** Use when speed is critical, data loss acceptable.
- **RAID 1:** Use when data safety is paramount.
- **RAID 5:** Use for balanced performance, fault tolerance, and capacity.
- **RAID 10:** Use for demanding applications needing both speed and redundancy.
