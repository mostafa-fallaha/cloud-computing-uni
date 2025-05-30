### 📘 **Cloud Infrastructure – AWS Summary**

---

### 🏢 **History of AWS**

* Originally built for Amazon’s e-commerce infrastructure.
* Evolved into a commercial cloud service: **Amazon Web Services (AWS)**.
* Offers **Infrastructure-as-a-Service (IaaS)**: VMs, storage, networking.
* Users pay per use, install their OS and applications.

---

### 🌐 **AWS Core Services**

#### 1. **Amazon EC2 (Elastic Compute Cloud)**

* Runs **virtual machines** in the cloud.
* Uses **AMI (Amazon Machine Image)** to launch VMs.
* Users can start/stop multiple instances.
* Supports **load balancing** across instances.
* Each instance has a **cost per hour** and is tied to a **location**.

#### 2. **Amazon EBS (Elastic Block Store)**

* Provides **volumes** (1 GB to 1 TB) like virtual hard drives.
* Volumes can be:
    * Formatted and mounted.
    * Used by only one instance at a time.
    * Replicated to avoid data loss.

#### 3. **Amazon S3 (Simple Storage Service)**

* Stores large objects (up to 5 TB).
* Each object is stored in a **bucket** and identified by a **key**.
* Supports read, write, delete operations.
* Offers **authentication** and **integrity checks** (e.g., MD5 hash).

#### 4. **Amazon SimpleDB**

* A NoSQL key-value data store.
* Allows queries and data access via **web service requests**.
* Pay for storage and access.

#### 5. **Amazon SQS (Simple Queue Service)**

* Used for **communication between instances** via message queues.
* Each message can be “locked” during processing.
    * If processing fails, the lock expires and the message is available to other instances.
* Supports:
    * Reliable message delivery.
    * Load distribution.
    * First-come-first-served processing.

#### 6. **Amazon CloudWatch**

* Monitors application performance and resource usage.
* Collects \~12 key metrics and displays real-time graphs.

#### 7. **Amazon AutoScaling**

* Automatically adjusts the number of instances:
    * Scale **up** when load is high.
    * Scale **down** when underutilized.
* Policies based on CPU usage or other thresholds.
* Verctical Scaling is when we upgrade the instance itself (e.g. EC2 from `T2` to `M5`).
* Horizontal Scaling is when we add more instances.

---

### 🏭 **Data Centers and Infrastructure**

* AWS is available in **multiple regions** and **availability zones**.
* Each region may contain multiple zones (data centers).
* Storage is replicated within a region and can be across regions.
* Different pricing per region based on infrastructure costs.

---

### 🌐 **IP Addressing**

* Each instance gets a **public IP** (for Internet access) and a **private IP** (for internal cloud communication).
* When an instance is stopped, its IPs may be reassigned.

---

### 🧰 **Other AWS Services**

* **EMR (Elastic MapReduce)** – Hadoop on EC2.
* **Route 53** – DNS service.
* **CloudFront** – Content Delivery Network (CDN).
* **Elastic Load Balancer** – Distributes traffic across instances.