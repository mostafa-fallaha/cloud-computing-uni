### 📘 **Distributed Systems – Programming Models (Part 2)**

**Focus: Hadoop MapReduce**

---

### 🔧 **Modern Programming Models**

* Designed to:

  1. Hide low-level distributed system concerns.
  2. Let developers focus on sequential logic.
* Examples: **MapReduce**, **Pregel**, **GraphLab**.

---

### 📊 **What is MapReduce?**

* A **data-parallel** programming model for **big data**.
* Popular in industry (Google, Facebook, Yahoo).
* **Hadoop** is the open-source version of MapReduce.

#### Key Components:

1. **MapReduce engine** – handles task execution.
2. **HDFS (Hadoop Distributed File System)** – stores large datasets across clusters.

---

### 🔁 **How MapReduce Works**

#### **Phase 1 – Map**

1. Input data is split into blocks.
2. Each block is sent to a different node.
3. Each node processes its block and outputs **(key, value)** pairs.

#### **Phase 2 – Reduce**

1. Intermediate results from mappers are grouped by key.
2. Reducers aggregate values with the same key and output results.

---

### 🧠 **Example: Word Count**

* Input: Large text file.
* **Map**: Emit (word, 1) for each word.
* **Reduce**: Sum values for each word.
* Final output: (word, total count).

---

### 🌐 **Cluster & Network Setup**

* Master-slave model:

  * **JobTracker (JT)**: Master.
  * **TaskTrackers (TT)**: Slaves.
* Data locality matters: Same-rack nodes = faster bandwidth.

---

### ⚙️ **Data Components**

* **InputFormat**: Defines how input is split (default: 64MB chunks).
* **RecordReader**: Converts raw input into (K,V) for mappers.
* **Mapper**: Performs user-defined computation.
* **Partitioner**: Determines reducer destination for each (K,V).
* **OutputFormat**: Writes reducer output to HDFS.

---

### 🖥️ **Code Examples**

* **Python**: Using `multiprocessing.Pool` to sum array chunks in parallel. <br />
```python
from multiprocessing import Pool

# Define a function to sum a chunk of the array (this is the "map" part)
def sum_chunk(chunk):
    return sum(chunk)

# Main code
if __name__ == "__main__":
    # The input array to sum up
    array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

    # Number of processes (parallel workers)
    num_processes = 2 # We will split the work between 2 processes
    
    # Split the array into equal-sized chunks (in real parallelism, chunks would go to different processors)
    chunk_size = len(array) // num_processes
    chunks = [array[i:i + chunk_size] for i in range(0, len(array), chunk_size)]
    
    # Create a pool of workers (simulating parallel processors)
    with Pool(num_processes) as pool:
        # Apply the map step: each chunk is processed in parallel to compute its sum
        chunk_sums = pool.map(sum_chunk, chunks)

    # Apply the reduce step: combine the partial sums to get the final total
    total_sum = sum(chunk_sums)

    # Output the final result
    print("Sum of array elements:", total_sum)
```
* **Java**:

  * `Mapper` class: emits (word, 1).
  * `Reducer` class: sums values for each word.
  * `Driver` class: sets up and runs the MapReduce job.

---

### 📋 **Task Scheduling**

* **Pull-based**: TTs request tasks from JT (not pushed).
* Load balancing handled automatically.

---

### 🛡️ **Fault Tolerance**

* **Node Failures**:

  * If TT fails, JT reassigns its tasks.
    * If the job is still in the Map phase, JT asks another TT to re-execute all Map tasks that previously ran at the failed TT
    * If the job is in the Reduce phase, JT asks another TT to re-execute all Reduce tasks that were in-progress on the failed TT
* **Speculative Execution**:

  * Slow tasks are duplicated and completed by faster replicas.