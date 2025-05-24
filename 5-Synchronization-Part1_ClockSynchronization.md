### 📘 **Cloud Computing – Synchronization: Clock Synchronization Summary**

#### 🕒 **Why Synchronization Matters**

* In distributed systems (DS), synchronization ensures:

  * Accurate event ordering (e.g., surveillance tracking).
  * Safe resource sharing (e.g., writing to shared files).

---

### ⏲️ **Time Synchronization Types**

* **Physical Clock Synchronization**: Align actual time across machines.
* **Logical Clock Synchronization**: Maintain correct event ordering (next topic).

---

### 🧭 **Clock Synchronization Concepts**

#### 🕹️ **1. Coordinated Universal Time (UTC)**

* Standard global time reference.
* Broadcast via satellites with \~0.5ms accuracy.

#### 🖥️ **2. Tracking Time on Computers**

* **Hardware Timer** sends periodic signals (e.g., 1000 interrupts/sec).
* Software clocks increment based on these signals.
* Real issues: timer imperfections → **clock skew** (fast/slow clocks).

##### Clock Skew

UTC is `t`. Clock on the computer have a time C(t).
* **Skew = dC/dt – 1**

  * `= 0`: Perfect clock
  * `> 0`: Fast clock
  * `< 0`: Slow clock

Skew of the clock is defined by the extent to which the frequency differs from that of a perfect clock.<br />
Frequency of the clock is defined as the ratio of the numbers of seconds counted by the software for every UTC second, freq = dc/dt.

---

### 🔧 **Clock Synchronization Algorithms**

#### 🧠 **1. Cristian’s Algorithm**

* Centralized approach:

  1. Client sends time request to server.
  2. Server replies with time and timestamps.
  3. Client estimates **offset θ** using:

     ```
     θ = ((T2 - T1) + (T3 - T4)) / 2
     θ = t3 + dTres - t4 (t3: on the server | t4: on the client)
     If θ > 0 (t3 + dTres > t4), the client should increment his time
     If θ < 0, the client should decrement his time (but not allowed) since decrementing a clock have adverse effects on several apps (e.g. make program)
     ```
  4. Client adjusts its clock **forward only**.
* ⚠️ Assumes symmetric network delays.
* 📍 Good for **intranets**, not the Internet.
* Faulty clock on the time server leads to inaccurate clock in the entire DS.
* Failure on the time server will render synchronization impossible.

#### 🔁 **2. Berkeley Algorithm**

* **Distributed** approach:

  1. Time server polls other machines.
  2. Computes average clock differences.
  3. Instructs all to gradually adjust clocks.
* 📍 Does **not** require a UTC source.
* Good for systems without central time authority.

#### 🌐 **3. Network Time Protocol (NTP)**

* Hierarchical protocol used over the **Internet**.
* **Stratum-based** structure:

  * Stratum 1: Closest to UTC source.
  * Lower strata sync with higher ones.
* Uses multiple time samples for accuracy.
* Provides **authentication**, **redundancy**, **scalability**, and **fault tolerance**.

---

### ✅ **Key Takeaways**

* Computer clocks are **imperfect** due to hardware issues.
* Synchronization is critical for **event ordering** and **data integrity**.
* **Cristian’s** is simple but central.
* **Berkeley** is decentralized.
* **NTP** is scalable, Internet-ready, and widely used.
