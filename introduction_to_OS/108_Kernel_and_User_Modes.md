# 108. Kernel and User Modes

## 🔩 What is the Kernel?

The **kernel** is the core component of the operating system that acts as a bridge between hardware and software. It is responsible for managing resources such as CPU, memory, and I/O devices and provides essential services to run user applications.

![image](https://github.com/user-attachments/assets/2d251cb8-130c-499a-8ed1-4f6ff8f43816)

### 🧠 What *Actually* Is a Kernel?

The **kernel** is a special program that runs in **privileged mode** with full control over your computer. It manages how all other programs use the hardware.

> 🔧 The kernel is like the *manager* of the entire system—deciding who gets to use what and making sure nothing conflicts.

### 👀 How Does It Look Like?

- The kernel is a **binary executable file** loaded at boot time.
- It has **no user interface**.
- It runs in the background, in a protected area of memory.

Examples:
- Linux: `/boot/vmlinuz-6.1.0-17-amd64`
- Windows: `ntoskrnl.exe`

### 📦 Example: Saving a File

1. You press **Ctrl + S** in an app.
2. The app makes a **system call** to request saving the file.
3. The **kernel**:
   - Validates access.
   - Locates the file on disk.
   - Sends commands to the disk driver.
4. Returns control back to the application.

---

## 🧠 Kernel Mode

- The kernel operates in a **privileged** environment.
- Can access hardware directly and perform critical system-level tasks.

## 🧑‍💻 User Mode

- User applications run in **restricted** mode.
- Cannot directly access hardware or critical OS services.
- Interact with the kernel through **system calls**.

## 🔐 Privileged Mode

Also called **Supervisor Mode**:
- Reserved for kernel operations.
- Has unrestricted access to system resources.
- Handles tasks like process and memory management.

## 🛡️ Protection Rings

Protection rings define levels of privilege:
- **Ring 0** – Kernel Mode (most privileged)
- **Ring 3** – User Mode (least privileged)

![image](https://github.com/user-attachments/assets/6032284d-ad14-4d67-8355-0f1a7c5c0f2a)

Used to enforce security and prevent user programs from interfering with core system operations.

## 🔁 Transition Between Kernel and User Modes

![image](https://github.com/user-attachments/assets/86f78ff5-2197-4040-a877-b29799b6ea0c)

1. System boots → Kernel is loaded and runs in kernel mode.
2. User apps launch in **user mode**.
3. When an app needs privileged access (e.g., saving a file), it:
   - Makes a **system call**.
   - Triggers a switch to **kernel mode**.
   - Kernel handles the operation.
   - Switches back to **user mode** after execution.

The CPU switches execution contexts using a separate kernel stack and resumes user app execution once the kernel work is complete.

---

> 📘 *This note explained what the kernel is, how it interacts with hardware and user applications, and how the system securely transitions between user and kernel modes.*
