### 📘 **Cloud Computing – Virtualization Summary**

---

### 🖥️ **Computer Resources Overview**

Every computer has:

1. **Processor** – Performs calculations.
2. **Memory** – Stores data (RAM = fast, short-term; HDD = slow, long-term).
3. **Communication Channels** – For networking (Ethernet, WiFi, Optical, etc.).

---

### 🧑‍💻 **Why Do We Need an Operating System?**

An OS is responsible for:

1. Providing a **user interface** (GUI or CLI).
2. Managing **applications**.
3. Managing **resources** (CPU, memory, devices).

---

### 🧩 **Resource Management in the Cloud**

* Challenges:

  * Many users, computers, OSes, applications.
  * Potential hardware failures.
* Solution: **Resource Virtualization**

---

### 🧱 **What is Virtualization?**

* Running **multiple virtual machines (VMs)** on a single physical computer.
* Each VM acts like an independent computer with its own OS and applications.
* A virtual machine is also called an instance when we talk about cloud computing.

#### 💾 **Virtual Machine (VM):**

* An **application** that simulates a computer (CPU, memory, network).
* Uses an **image** (saved system state) to create VMs.
    * An image is the state of a computer that has been saved into a file
* You can start/stop/restart multiple instances from the same image.

---

### 🌩️ **Why Virtualization is Useful for the Cloud?**

1. **Load Balancing** – VMs can be moved to less-busy machines.
2. **OS Flexibility** – Users can choose their preferred OS.
3. **Security** – VMs are **isolated** from each other (e.g., if one is hacked, others remain safe).
4. **Resource Control** – Define CPU/memory/disk limits per VM.

---

### 🖼️ **Example – Amazon EC2**

* Users create **Amazon Machine Images (AMIs)**.
* Launch multiple VMs from one image.
* Use Amazon’s tools to monitor and manage them.

---

### ⚙️ **Virtualization Approaches**

#### 1. **Full Virtualization**

* VMs are exact replicas of physical machines.
* Can run unmodified OSes like Windows or Linux.

#### 2. **Paravirtualization**

* VMs are partially simulated.
* OS and apps must be **modified** to run.

---

### 🧠 **Virtual Machine Manager (VMM / Hypervisor)**

* Manages VMs on a system.
* Two types:

  * **Bare-metal (Type 1)** – Runs directly on hardware (e.g., VMware ESX).
  * **Hosted (Type 2)** – Runs on top of a host OS (e.g., VirtualBox).

#### VMM Capabilities:

* Create, start, stop, save, monitor VMs.

---

### ⚠️ **Disadvantages of Virtualization**

1. **Performance Overhead**

   * VMM intercepts all operations → slower performance.

2. **Higher Hardware Cost**

   * Requires powerful machines (multi-core CPUs, more RAM, large disks).
