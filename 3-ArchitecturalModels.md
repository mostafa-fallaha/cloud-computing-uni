### 📘 **Cloud Computing – Architectural Models Summary**

#### 🖥️ **What is a Distributed System?**

* A **distributed system** is a set of interconnected components (hardware/software) that **collaborate to solve problems**.
* Examples: Google Search (Client-Server), BitTorrent (Peer-to-Peer), Skype.

---

### 🧱 **1. Communicating Entities**

Entities in distributed systems include:

* **Devices**: User hardware (phones, laptops, sensors).
* **Servers**: Respond to device or server requests.
* **Applications**: Software that sends/receives data.
* **Threads**: Handle concurrent tasks (e.g., browser tabs).
* **Objects**: Fine-grained components of applications.

---

### 🔄 **2. Communication Paradigms**

How components exchange data:

#### a. **Inter-Process Communication (IPC)**

* Used within the same machine.
* Techniques: **Shared Memory**, **Pipes**, **Message Passing**.
* Requires manual handling (e.g., semaphores, sockets).
* Example: Producer-consumer model with mutex locks.

#### b. **Remote Invocation**

* Enables a program to call procedures/methods on a **remote machine**.
* **RPC (Remote Procedure Call)**:
    * Client-server communication with function calls
    * Data representation should be uniform
    * Can be Synchronous/Asynchronous
* **RMI (Remote Method Invocation)**:
    * Java-based, object-oriented RPC
    * Invoke methods on objects locates in different Java Virtual Machines (JVMs)
* **Web Services**: APIs like weather or news services.

Key concept: **Marshaling** (translating procedure parameters for network transmission | as bits).

#### c. **Indirect Communication**

Entities in a DS exchange messages through an intermediary (broker) that manages the distribution of messages based on the interest of the subscribers.
* **Group Communication**: One sender to many receivers.
    * Enable one-to-many communication | Efficient use of bandwidth
    * Scalability issues and message overhead
    * _Notes:_
        * Multicast: to all group members simultanously
        * Broadcast: send to everyone, only the intended group members process it
* **Publish-Subscribe**:
    * Senders (publishers) don't know subscribers
    * Subscribers express interest in specific type of messages
* **Message Queues**:
    * Senders and receivers communicate asynchronously via queues
    * Decoupling: senders and receivers do not need to interact
    * Load Balancing: multiple receivers can process messages from single queue
    * Architecture:
        * Placement of the queue: e.g. E-mail messages is optimized by the use of destination queues
        * Identity of the queue: a naming service for queues is necessary and a database of queue names to network location is maintained (can be distributed)

---

### 🧩 **3. Roles and Responsibilities**

#### a. **Client-Server Architecture**

* **Client**: Requests data.
* **Server**: Processes and responds.
* Pros: Centralized control, thin clients.
* Cons: Single point of failure, limited scalability.

#### b. **Peer-to-Peer (P2P) Architecture**

* All nodes are **equal peers**.
* Each node can act as both **client and server**.
* Example: BitTorrent downloads different parts of a file from multiple peers.
* Pros: Scalability, redundancy.
* Cons: Complexity in coordination and consistency.

---

### 🔁 **Summary Recap**

* **Entities**: Devices, servers, applications, threads, objects.
* **Communication Methods**: IPC, RPC/RMI, Web services, Group/Queue-based.
* **Architectures**: Client-Server and Peer-to-Peer.
