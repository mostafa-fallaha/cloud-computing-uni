### 📘 **Cloud Computing – Naming Systems Summary**

#### 📌 **What is a Naming System?**

* A **naming system** maps **names** to **addresses** or **unique identifiers** in a distributed system.
* Examples:

  * **DNS** (Domain Name System): Maps `example.com` → IP address.
  * **DFS** (Distributed File System): Maps file names to file locations.

---

### 🧩 **Types of Naming Systems**

#### 1. **Flat Naming**

* Uses **random or unstructured names** as identifiers.
* No info about location in the name.

##### **Name Resolution Techniques**:

* **Broadcasting**: Send a request to all devices. Used in small/local networks.
  * ❌ Drawback: High traffic, poor scalability, and security issues.

* **Forwarding Pointers**: A pointer is stored that redirects to the current location.
  * When a resource is registered in the system, it is associated with a unique flat name and a forwarding pointer to the actual address/location where it can be found.
  * 🔁 Good for mobile resources.
  * ❌ Issues: Overhead, consistency, potential failures.

* **Home-Based Approach**: Each entity has a fixed “home” node that always knows its location.
  * Entity updates home about its current location.
  * Example:
    * Client1 contacts Home to get Client2 address.
    * Home gives Client2 address to Client1.
    * Client1 contacts Client2.
  * 🏠 Home acts as a directory.
  * ❌ Drawback:
    * Overhead if the entity is far from its home.
    * If the entity permanently moves, then a simple Home-Based approach incurs higher communication overhead.
    * Connection set-up overheads: consider the scenario where the clients are nearer to the mobile entity than the Home.

---

#### 2. **Structured Naming**

* Uses **hierarchical or compositional names**, like file paths or domain names.
* Examples:

  * `/home/user/docs/file.txt`
  * `mail.google.com`

##### **Name Resolution in Structured Naming**:

* **Iterative**: Client queries each name server step by step.
* **Recursive**: Name servers forward the query until it's resolved, then return the answer.

---

#### 3. **Attribute-Based Naming**

* Resources are identified by a **set of attributes**, not a fixed name or path.
* Example:

  * `type=pdf`, `author=Jane`, `year=2024`
* Used in:

  * Databases
  * Directory services (e.g., LDAP)
  * Metadata-based file systems

---

### 📊 **Comparison Table**

| Feature         | Flat Naming               | Structured Naming          | Attribute-Based Naming        |
| --------------- | ------------------------- | -------------------------- | ----------------------------- |
| **Name Format** | Random identifiers        | Hierarchical paths         | Set of attributes             |
| **Query Style** | Direct lookup / broadcast | Iterative/Recursive lookup | Attribute-based search        |
| **Scalability** | Low                       | Moderate                   | High                          |
| **Use Case**    | S3 object storage         | DNS, file directories      | Search in databases / tagging |
