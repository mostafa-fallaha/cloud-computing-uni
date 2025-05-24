### 📘 **Cloud Computing – Mutual Exclusion Summary**

---

### 🔒 **What is Mutual Exclusion?**

* **Mutual exclusion** ensures that **only one process** can access a **shared resource** (e.g., file, printer) at a time.
* In distributed systems (DS), processes run on **different machines**, so coordination is harder than on a single machine.

---

### ❗ **Why Do We Need It?**

* Without proper coordination, shared data can be **corrupted**.

#### 🧾 Example: Bank Transfer

* If A transfers \$50 to B, and B transfers \$500 to A **at the same time**, both might read outdated balances, causing **money to be lost**.

#### 🎟️ Example: Ticket Booking System

* Many users can **read** seat availability.
* But if someone is **booking** (writing), others should **not read or write** — or risk **inconsistent seat info**.

---

### ⚠️ **Deadlock Example**

User A locks the printer → waits for scanner.
User B locks the scanner → waits for printer.
🔁 Both are stuck waiting = **deadlock**.

---

### 🍴 **Dining Philosophers Problem**

* Philosophers must pick up 2 chopsticks to eat.
* If all pick up their left one and wait for the right, nobody eats — **classic deadlock** scenario.

---

### 🔄 **Distributed Mutual Exclusion Algorithms**

Two main categories:

#### 1. **Permission-based**

* A process must **request permission** to access a resource from one or more coordinators.

#### 2. **Token-based**

* A **token** (a special message) gives the right to access a resource.
* Only the process **holding the token** can access the resource.

---

## 🧭 **Algorithms**

---

### 🧷 **1. Centralized Algorithm**

* One **coordinator** manages access.
* Steps:

  1. A process sends a **request** to the coordinator.
  2. If no one is using the resource → it sends **grant**.
  3. Otherwise, the coordinator **queues** the request.
  4. When current process finishes, coordinator grants the next in line.

#### Pros:

* Simple to implement.
* Guarantees mutual exclusion.

#### Cons:

* **Single point of failure** (if coordinator crashes).
* Can become a **performance bottleneck**.

---

### 🔁 **2. Token Ring Algorithm**

* Processes form a **logical ring**.
* A **token** circulates around the ring.
* A process can access the resource **only if it holds the token**.
* When done (or not interested), it **passes the token** to the next.

#### Pros:

* **No starvation**: every process eventually gets the token.
* Simple logic.

#### Cons:

* **High message overhead** (token circulates even if no one needs it).
* **Token loss** is difficult to detect.
* Must handle **dead processes** (use acknowledgments to purge them).

---

### 🗳️ **Election in Distributed Systems**

* A **coordinator** may crash. We need to **elect a new one**.
* Every process knows IDs of others but not who has failed.

#### Election Rules:

* Initiator process should be **unique**.
* Often, the process with **highest ID** is selected.
* Can also use **least load** to elect the best coordinator.

---

## 🗳️ **Election Algorithms**

---

### 🥊 **1. Bully Algorithm**

* When a process detects failure, it sends **election messages** to all **higher-ID** processes.
* If someone replies, that one **takes over** the election.
* If **no one replies**, the process **declares itself coordinator**.

#### Pros:

* Simple and works in **general topologies**.

#### Cons:

* **Message-heavy**: O(n²) in worst case.

---

### 🔄 **2. Ring Algorithm**

* Works in a **ring topology**.
* Election message circulates, each process adds its ID.
* When back at the initiator, it elects the process with the **highest ID**.
* A **coordinator message** is then circulated.

#### Pros:

* Fewer messages: **2n**.
* Simple logic.

#### Cons:

* Requires a **ring overlay**.

---

### 📊 **Comparison Table**

| Feature          | Centralized  | Token Ring | Bully Algorithm | Ring Algorithm |
| ---------------- | ------------ | ---------- | --------------- | -------------- |
| Fault-tolerant   | ❌ No         | ✅ Yes      | ✅ Yes           | ✅ Yes          |
| Message Overhead | Low          | High       | O(n²)           | 2n             |
| Fairness         | ❌ Not always | ✅ Yes      | ❌ No            | ✅ Yes          |
| Complexity       | Low          | Medium     | Medium          | Medium         |
