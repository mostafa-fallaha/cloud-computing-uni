### 📘 **Cloud Computing – Consistency and Replication Summary**

#### ✅ **Why Replication?**

Replication means keeping copies of data on multiple computers. It's useful for:

1. **Performance** – Data can be fetched from the nearest replica.
2. **Availability** – If one server fails, others can still serve the data.
3. **Scalability** – Load is spread across replicas.
4. **Security** – Faulty or malicious replicas can be outvoted by correct ones.

---

#### 🔁 **Why Consistency?**

In distributed systems, replicated data must remain **consistent**. Without it, different users may see **different data** at the same time.

**Example:** Two servers show a bank balance of \$1000. One adds \$1000, another adds 5% interest — inconsistent results may follow depending on the order of operations.

---

### 🧠 **Consistency Models**

These are agreements between the data-store and processes on how updates are seen across replicas:

* **Strict Consistency**: Every read sees the latest write. Hard to implement and inefficient.
* **Loose Consistency**: Reads may return older values. Easier and more scalable.
* **Sequential Consistency**: All replicas see operations in the same sequence, but not necessarily the real-time order.
* **Total Ordering**: All replicas agree on a single global order for updates.
  * If process Pi sends a message `mi` and Pj sends `mj`, and if one correct process delivers `mi` before `mj` then every correct process delivers `mi` before `mj`
* **Sequential Ordering**: Each process's operations are seen in order, but different processes' operations can be interleaved.
  * At every process, `mi,1` should be delivered before `mi,2` , which is delivered before `mi,3` and so on...
  * At every process, `mj,1` should be delivered before `mj,2`, which is delivered before `mj,3` and so on...

---

### 🗃️ **Replica Management**

1. **Replica Server Placement**:

   * Decide where to place K replicas among N possible sites.
   * Goal: Minimize latency/cost (e.g., greedy algorithm).

2. **Content Replication and Placement**:

   * **Permanent Replicas**: Core dataset, often static.
   * **Server-Initiated Replicas**: Dynamically created by providers.
   * **Client-Initiated Replicas**: Local caches on client machines.

---

### ⚙️ **Consistency Protocols**

Define how updates are propagated and agreed upon.

#### 1. **Primary-Based Protocols**:

* One **primary** server handles all writes.
* Writes go to primary → updates sent to others → ACKs received.
* **Remote-Write**: Simple, ensures sequential consistency, but has high latency.

#### 2. **Replicated-Write Protocols**:

* **All replicas** can handle writes.
* Example: **Active Replication**:

  * Clients write to any replica.
  * Replicas forward updates to others.
  * **Challenge**: Maintaining correct operation ordering.

##### Centralized Version:

* A **sequencer** assigns operation order numbers.
* Ensures all replicas apply operations in the same order.

---

### 🧾 **Summary**

* Replication improves **performance**, **availability**, and **fault tolerance**.
* But it requires **consistency models** and **protocols** to prevent data conflicts.
* The choice of model depends on trade-offs: accuracy vs. efficiency.
