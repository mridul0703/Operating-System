# 401. File System

---

## 📌 What is a File System?
A file system is a method and data structure that an operating system uses to:
- **Store, manage, and retrieve data** on storage devices (e.g., HDDs, SSDs, USB drives).
- **Organise data** into files and directories.
- **Maintain metadata** and manage the **allocation of space**.

---

## 📂 Hierarchical Structure

### 🔹 Concept of Hierarchical Structure
- The file system is organised like a **tree**, with:
  - **Root directory** at the top.
  - **Subdirectories** branching out from the root.
  - **Files** stored at various levels.

![image](https://github.com/user-attachments/assets/24ab07f1-199d-40f5-b88b-a9f7334c9c60)

### 🔹 Example:
```
/ (Root)
├── home/
│ ├── user1/
│ └── user2/
├── var/
│ ├── log/
│ └── tmp/
└── etc/
└── config/
```

### 🔹 Advantages of Hierarchical Structure:
- Provides an **organised layout** for data storage.
- Supports **access control** by setting permissions at different directory levels.
- Simplifies **file management and navigation**.

---

## 📌 Metadata in File Systems

**Metadata** is information about each file or directory, which helps the operating system manage and control file access.

### 🔹 Common Metadata Attributes:
| Metadata Attribute       | Description                                  |
|--------------------------|----------------------------------------------|
| **File Name**             | Name of the file or directory.               |
| **Size**                  | Size of the file in bytes.                   |
| **Type**                  | File format (e.g., .txt, .jpg, .exe).       |
| **Creation Timestamp**    | Date and time when the file was created.     |
| **Modification Timestamp**| Date and time of the last modification.     |
| **Ownership**             | User and group that own the file.           |
| **Access Permissions**    | Read, write, and execute permissions.        |

### 🔹 Why Metadata is Important:
- Provides essential information for **file management**.
- Supports **security** by controlling access to files.
- Helps the operating system track file usage and status.

---

## 📌 Access Methods in File Systems

Access methods determine how data within files can be read or written.

### 🔹 Types of Access Methods:
| Access Method    | Description                                                         | Example Use Case                   |
|-------------------|---------------------------------------------------------------------|--------------------------------------|
| **Sequential Access** | Reads data in a fixed order, one block after another.            | Reading a log file line by line.    |
| **Direct Access**     | Allows random access to any part of the file.                    | Accessing a database record.        |
| **Indexed Access**    | Uses an index to locate data quickly.                           | Retrieving data in a large database.|
| **Random Access**     | Similar to direct access but used for smaller data chunks.       | Modifying a section of a video file.|

### 🔹 Illustration of Access Methods:
- **Sequential Access:** Read → Next → Next → End.
  ![image](https://github.com/user-attachments/assets/d1352892-c81a-40a4-b761-207e187cf55e)

- **Direct Access:** Go to specific location → Read/Write.
- **Indexed Access:** Use an index to quickly find data.
  ![image](https://github.com/user-attachments/assets/b3a1c1c0-b437-4721-a169-a00f0ac33c3e)

- **Random Access:** Access any position directly.

---

## 📌 File System Operations

File systems support a variety of operations to manage files and directories:

### 🔹 Basic File Operations:
| Operation          | Description                                              |
|--------------------|----------------------------------------------------------|
| **Create**          | Establishes a new file or directory.                     |
| **Read**            | Accesses the contents of a file.                         |
| **Write**           | Modifies or appends data to a file.                      |
| **Delete**          | Removes a file or directory.                            |
| **Rename/Move**     | Changes the name or location of a file or directory.     |
| **Manage Permissions** | Sets access control for users and groups.              |

### 🔹 Example of File Operations:
- **Creating a File:** `touch file.txt` (Linux)
- **Reading a File:** `cat file.txt` (Linux)
- **Deleting a File:** `rm file.txt` (Linux)
- **Changing Permissions:** `chmod 755 file.txt` (Linux)

---

## 📌 File System Integrity

Maintaining the integrity of a file system ensures data consistency and reliability.

### 🔹 Techniques for Ensuring Integrity:
| Technique            | Description                                                  |
|----------------------|--------------------------------------------------------------|
| **Journaling**        | Keeps a log of changes to recover from crashes.              |
| **Checksums**         | Verifies data integrity by comparing stored and computed values. |
| **File System Consistency Checks (FSCC)** | Scans and repairs file system errors.    |
| **Redundancy Methods**| Uses mirroring or parity bits for fault tolerance.          |

### 🔹 Why Integrity Matters:
- Prevents **data corruption** in case of power failure or crashes.
- Ensures **reliable data access** for applications.
- Protects against **unauthorised modifications**.

---

## 📌 Types of File Systems

Different operating systems use different file system types:

| File System Type | Operating System | Features                                      |
|-------------------|-------------------|-----------------------------------------------|
| **FAT32**         | Windows           | Simple, compatible, but limited file size.   |
| **NTFS**          | Windows           | Advanced features, security, and compression.|
| **ext4**          | Linux             | Journaling, large file support, efficient.   |
| **APFS**          | macOS             | Fast, secure, with strong encryption.        |
| **HFS+**          | macOS (older)     | Hierarchical, with journaling.               |
| **exFAT**         | Windows, macOS    | Cross-platform, large file support.          |

---

## 📌 Key Takeaways
- A **file system** is a critical part of an operating system that manages how data is stored and accessed.
- The **hierarchical structure** of file systems provides an organised way to store and manage files.
- **Metadata** provides essential information about files and directories.
- Different **access methods** allow efficient data retrieval based on specific needs.
- **File system integrity** ensures data reliability and prevents corruption.

---

> 🚀 *Understanding file systems is crucial for optimising data storage, ensuring data security, and maintaining system performance.*

