# 402. Types of File Systems

---

## 📌 Disk-Based File Systems
Disk-based file systems are used to manage data on physical storage devices like hard drives, SSDs, and optical discs.

![image](https://github.com/user-attachments/assets/cb1d90c6-d358-4f5b-b2cc-2d2164ed9520)

### 🔹 FAT (File Allocation Table)
- One of the oldest file systems, known for **simplicity and wide compatibility**.
- Used in removable media like USB drives and memory cards.
- Variants: **FAT12, FAT16, FAT32** (differ in file and partition size limits).
- ✅ Pros: Compatible with most operating systems.
- ❌ Cons: Lacks advanced features, limited scalability.

### 🔹 NTFS (New Technology File System)
- Primary file system for **Windows**.
- Supports **large volumes, file compression, encryption, and access control lists (ACLs)**.
- ✅ Pros: Reliable, secure, supports large files.
- ❌ Cons: Primarily used in Windows; limited support in other OS without third-party tools.

### 🔹 ext4 (Fourth Extended File System)
- Widely used in **Linux** environments.
- Supports **large file sizes, journaling, extents (for efficient storage)**.
- ✅ Pros: Reliable, efficient, fast file system checks.
- ❌ Cons: Primarily Linux-focused; limited support in other OS.

### 🔹 HFS+ (Hierarchical File System Plus)
- Used in **older macOS systems** (replaced by APFS).
- Supports **large file sizes, journaling**, and efficient storage management.
- ✅ Pros: Reliable, supports macOS features.
- ❌ Cons: Replaced by APFS in newer macOS versions.
  
![image](https://github.com/user-attachments/assets/1afd2237-51a6-481e-98a7-61311c60a54d)

---

## 📌 Network File Systems
Network file systems allow multiple users or systems to access and manage data stored on a central server over a network.

### 🔹 NFS (Network File System)
- Primarily used in **Unix and Linux environments**.
- Allows accessing files over a network as if they were on local disks.
- ✅ Pros: Efficient file sharing, scalable.
- ❌ Cons: Security depends on proper configuration.

![image](https://github.com/user-attachments/assets/cc0ef6cd-dbed-468b-824f-7b7f98500d36)

### 🔹 CIFS/SMB (Common Internet File System/Server Message Block)
- Primarily used in **Windows networks** for file and printer sharing.
- Provides features like **file locking, authentication, and encrypted communication**.
- ✅ Pros: Widely supported, secure with modern SMB versions.
- ❌ Cons: Can be complex to configure securely.

### 🔹 AFS (Andrew File System)
- A distributed file system for large networks.
- Offers **Kerberos authentication, volume management, and caching**.
- ✅ Pros: Secure, scalable.
- ❌ Cons: More complex to set up and manage.

### 🔹 DFS (Distributed File System - Windows)
- Allows creating a **single namespace for multiple file servers and shares**.
- Provides **redundancy and load balancing**.
- ✅ Pros: Simplifies data access, scalable.
- ❌ Cons: Windows-specific, requires proper configuration.

---

## 📌 Distributed File Systems
Distributed file systems manage data across multiple servers, offering high availability, fault tolerance, and scalability.

### 🔹 HDFS (Hadoop Distributed File System)
- Designed for storing and processing **large datasets** in distributed computing.
- ✅ Pros: Fault-tolerant, scalable, efficient for big data.
- ❌ Cons: Primarily designed for large-scale data; not ideal for general-purpose use.

### 🔹 GFS (Google File System)
- Developed by Google for **large-scale data processing**.
- Succeeded by **Colossus**.
- ✅ Pros: Optimized for large, sequential data reads and writes.
- ❌ Cons: Proprietary; not directly available outside Google.

### 🔹 Ceph
- A unified, distributed storage system supporting **object, block, and file storage**.
- ✅ Pros: Highly scalable, reliable, self-healing.
- ❌ Cons: Requires complex setup and configuration.

### 🔹 GlusterFS
- A scalable network file system for **data-intensive tasks** (cloud storage, media streaming).
- ✅ Pros: Scalable, supports data replication and volume management.
- ❌ Cons: May have performance overhead in certain setups.

### 🔹 Amazon S3 (Simple Storage Service)
- Object storage service from **Amazon Web Services (AWS)**.
- ✅ Pros: Highly scalable, durable, accessible via API.
- ❌ Cons: Costs can increase with high usage.

---

## 📌 Specialized File Systems
These file systems are designed with specific use cases in mind, offering unique features.

### 🔹 ZFS (Zettabyte File System)
- Known for **data integrity, scalability, and advanced storage management**.
- ✅ Pros: Data deduplication, compression, snapshots, self-healing.
- ❌ Cons: More resource-intensive, complex setup.

### 🔹 Btrfs (B-tree File System)
- A modern Linux file system focused on **fault tolerance and easy administration**.
- ✅ Pros: Snapshots, compression, multi-device support.
- ❌ Cons: Not as mature as ext4; may require careful management.

### 🔹 F2FS (Flash-Friendly File System)
- Optimized for **NAND flash-based storage devices** (SSDs, eMMC).
- ✅ Pros: High performance, efficient data allocation.
