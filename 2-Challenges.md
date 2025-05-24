### 📘 **Cloud Computing – Distributed Systems & Challenges Summary**

#### 🧩 **What is a Distributed System?**

* A **distributed system** is a collection of independent computers that appear as a single system to users.
* Foundation of **cloud computing**: supports scalability, flexibility, and reliability across multiple machines.

---

### ⚠️ **Major Challenges in Designing Distributed Systems**

#### 1. **Heterogeneity**

* **Hardware**: Different devices with varied processing power and architectures.
* **Software**: Various OSes, programming languages, middleware.
* **Network**: Mixed network types (wired, wireless, satellite) with different protocols and speeds.
* **Examples**: Conflicting data formats, code integration issues, slow data transfer, security mismatches.

#### 2. **Security**

* Ensures data is protected from **unauthorized access and tampering**.
* **Threats**: Data theft, tampering, service disruption.
* **Solutions**:

  * **Encryption** (data at rest and in transit)
  * **Authentication** (secure login)
  * **Access control** (limit permissions)

#### 3. **Scalability**

* A scalable system remains **efficient under increased load** (more users/resources).
* **Vertical scaling**: Add more power to existing machines.
* **Horizontal scaling**: Add more machines to the network.
* **Challenges**:

  * Load balancing
  * Managing shared states
  * Cost control
  * Concurrency management

#### 4. **Failure Handling**

* More machines = higher risk of **partial failure**.
* **Types of failures**:

  * Crash, omission (missed messages), response, and Byzantine (arbitrary behavior).
* **Strategies**:

  * **Failure detection** (e.g., checksums)
  * **Masking** (e.g., redundancy)
  * **Recovery** (e.g., checkpoints)

#### 5. **Concurrency**

* Multiple clients may access shared resources at the same time.
* **Key issue**: maintaining **data consistency** across replicas.
* **Example**: Bank account updates across replicated servers.

#### 6. **Transparency**

* System should hide complexity from users:

  * **Access**: How data is accessed
  * **Location**: Where resources are
  * **Migration/Relocation**: Movement of resources
  * **Replication**: Multiple data copies
  * **Concurrency**: Shared usage
  * **Failure**: Recovery process
