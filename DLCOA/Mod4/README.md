# Mod 4

| Computer Architecture | Computer Organization |
|--|--|
| Architecture (CA) is the `What`. | Organization (CO) is the `How`. |  
| It's the functional behavior of the computer from the programmer's point of view. | It's how those architectural features are physically implemented in the hardware. |
|  It includes the instruction set, addressing modes, and data types. | It deals with how components like the CPU, memory, and I/O are connected and work together. |

## Von Neumann Architecture 

1. Stored-Program Concept
- Both data and instructions are stored in the same main memory (RAM).

![images](https://github.com/DeviprasadShetty9833/Sem_III_Notes/blob/23aef3064bc453f481943a05e02ed83c772249b0/DLCOA/assets/VonNeumann.png)

## Components
- Central Processing Unit (CPU): The brain of the computer. It consists of:
  - Arithmetic Logic Unit (ALU): Performs all mathematical calculations (add, subtract) and logical operations (AND, OR, NOT).
  - Control Unit (CU): Directs the operation of the processor. It interprets instructions and coordinates the activities of all other hardware components.
  - Registers: Small, high-speed memory locations inside the CPU for temporary storage of data, instructions, and addresses (e.g., Program Counter, Instruction Register, Accumulator).
- Memory Unit (Main Memory/RAM): A single, unified storage space for both data and instructions. Each location in memory has a unique address.
- Input/Output (I/O) Systems: Allow the computer to communicate with the external world (e.g., keyboard, mouse, monitor, printer).
- System Bus: A single communication path that connects all the major components.


### **Module 5: Memory Organization**

#### **5.1 Introduction to Memory, Memory Hierarchy and Characteristics**

**1. What is Computer Memory?**
*   Memory is the electronic storage space for instructions and data that a computer needs to access quickly.
*   It is a fundamental component; without it, the OS, hardware, and software cannot function.
*   It acts as a storage unit for data to be processed and the instructions required for processing.

**2. Memory-CPU Communication**
*   **System Bus:** The main communication channel between the CPU and memory.
    *   **Data Bus:** Transfers the actual data.
    *   **Address Bus:** Carries the memory address for read/write operations.
    *   **Control Bus:** Sends control signals (e.g., Read, Write).
*   **Memory Controller:** Manages the data flow and synchronizes signals. In modern systems, it is integrated into the CPU.
*   **Process:**
    1.  CPU places a memory address on the Address Bus.
    2.  CPU sends a Read/Write command on the Control Bus.
    3.  For a Read: Memory controller retrieves data and sends it to the CPU via the Data Bus.
    4.  For a Write: CPU sends data via the Data Bus to be stored in memory.

**3. Memory Hierarchy**
*   It is a pyramid-like structure that organizes computer storage based on **access speed, cost, and capacity**.
*   The hierarchy exists to bridge the speed gap between the fast CPU and slower main memory, optimizing performance and cost.
*   **Levels (Top to Bottom):**
    1.  **Registers:** Inside the CPU, fastest, smallest, most expensive.
    2.  **Cache Memory (L1, L2, L3):** Very fast, small, located close to the CPU.
    3.  **Main Memory (RAM):** Slower than cache, larger capacity, volatile.
    4.  **Secondary Storage (HDD/SSD):** Non-volatile, large capacity, slow.
    5.  **Tertiary Storage (Magnetic Tape, Optical Disk):** Used for backup/archival, very slow, very high capacity.

**4. Characteristics of Memory Hierarchy**
*   **Access Time:** Increases as we move down the hierarchy.
*   **Capacity:** Increases as we move down the hierarchy.
*   **Cost per Bit:** Decreases as we move down the hierarchy.
*   **Performance:** The hierarchy improves overall system performance by keeping frequently used data in faster memory.

**5. Advantages of Memory Hierarchy**
*   **Faster Access:** Frequently used data is available in high-speed cache.
*   **Cost-Effective:** Expensive memory (like cache) is used sparingly.
*   **Efficient Resource Use:** Optimizes the use of different memory types.
*   **Increased Capacity:** Large amounts of data can be stored in secondary memory.
*   **Increased Processing Speed:** CPU spends less time waiting for data.

**6. Disadvantages of Memory Hierarchy**
*   **High Cost:** Faster memory components are expensive.
*   **Complex Design:** Requires sophisticated management algorithms.
*   **Latency Issues:** Cache misses lead to slower data access from lower levels.
*   **Higher Power Consumption:** Maintaining multiple active memory levels consumes more power.
*   **Cache Coherence Problem:** In multi-core systems, keeping caches synchronized is complex.

---

#### **5.2 Classification of Memories**

**1. Primary Memory (Main Memory)**
*   Directly accessible by the CPU.
*   Volatile (loses data when power is off).
*   **Types:**
    *   **RAM (Random Access Memory):**
        *   **SRAM (Static RAM):** Uses transistors (flip-flops). Faster, more expensive. Used for Cache.
        *   **DRAM (Dynamic RAM):** Uses capacitors. Needs periodic refreshing. Slower, cheaper. Used for Main Memory.
    *   **ROM (Read Only Memory):**
        *   Non-volatile. Used to store firmware (e.g., BIOS).
        *   **Types:**
            *   **MROM:** Masked, factory-programmed.
            *   **PROM:** Programmable by user once.
            *   **EPROM:** Erasable with Ultraviolet light.
            *   **EEPROM:** Electrically Erasable and Programmable.

**2. Secondary Memory (Auxiliary Memory)**
*   Not directly accessible by the CPU (accessed via I/O modules).
*   Non-volatile, permanent storage.
*   Large capacity, slower than primary memory.
*   **Types:**
    *   **Magnetic Tapes:** Sequential access, high capacity, low cost. Used for backups.
    *   **Magnetic Disks (HDD):** Random access, high capacity. Data stored on spinning platters.
    *   **Optical Disks (CD-ROM, DVD):** Laser-based, removable storage.
        *   **CD-ROM:** Read-only, ~600 MB capacity.
        *   **WORM (Write Once, Read Many):** User can write once.
        *   **DVD:** Higher capacity (4.7 GB to 17 GB).

**3. Cache Memory**
*   A very high-speed memory placed between the CPU and Main Memory.
*   Stores frequently used data and instructions to speed up CPU access.
*   **Advantages:** Faster than main memory, reduces access time.
*   **Disadvantages:** Very expensive, small capacity.

---

#### **5.3 Cache Memory**

**1. Levels of Cache: L1 and L2**
*   **L1 Cache:**
    *   Located directly inside the CPU core.
    *   Smallest and fastest (1-2 cycle access time).
    *   Dedicated to a single core.
*   **L2 Cache:**
    *   Larger than L1 but slower.
    *   Can be shared among multiple cores or dedicated.
    *   Acts as a buffer between L1 and Main Memory.

**2. Cache Performance**
*   **Cache Hit:** The requested data is found in the cache. (Fast)
*   **Cache Miss:** The requested data is not found in the cache. The CPU must fetch it from main memory. (Slow)

**3. Cache Mapping Techniques**
*   **Fully-Associative:**
    *   Any memory block can be placed in any cache line.
    *   **Advantage:** Best flexibility and performance.
    *   **Disadvantage:** Complex and expensive to implement (requires many comparators).
*   **Direct-Mapped:**
    *   Each memory block maps to exactly one cache line.
    *   **Advantage:** Simple and cheap to implement.
    *   **Disadvantage:** Can cause conflicts, leading to poor performance.
*   **Set-Associative:**
    *   A compromise between the above two. Cache is divided into 'n' sets (ways).
    *   A memory block can be placed in any line within a specific set.
    *   **Advantage:** Good performance with reasonable complexity.

**4. Cache Coherence**
*   **Problem:** In a multiprocessor system, multiple caches may have different copies of the same memory block. If one processor updates its copy, the others become inconsistent.
*   **Solution:** Cache Coherence Protocols ensure all caches have a consistent view of memory.
*   **Common Protocols:** MSI, MESI, MOSI, MOESI.
*   **MESI States:**
    *   **Modified (M):** Cache data is different from main memory (dirty).
    *   **Exclusive (E):** Cache has the only copy, and it matches main memory (clean).
    *   **Shared (S):** Multiple caches may have the same read-only copy.
    *   **Invalid (I):** The cache line data is invalid and cannot be used.

**5. Cache Write Policies**
*   **Write-Through:**
    *   Data is written to both the cache and main memory simultaneously.
    *   **Advantage:** Ensures data consistency.
    *   **Disadvantage:** Slower write performance.
*   **Write-Back:**
    *   Data is written only to the cache initially. The main memory is updated later when the cache line is evicted.
    *   **Advantage:** Faster write performance.
    *   **Disadvantage:** Risk of data inconsistency; more complex.
*   **Write-Allocate vs. No-Write-Allocate:**
    *   **Write-Allocate:** On a write miss, the block is loaded into the cache before the write.
    *   **No-Write-Allocate:** On a write miss, the write goes directly to memory, bypassing the cache.

---

#### **5.5 I/O Interface and Modes of Transfer**

**1. Modes of Data Transfer**
*   **Programmed I/O:**
    *   The CPU directly controls the entire I/O operation.
    *   CPU repeatedly checks (polls) the I/O device status, leading to low efficiency as the CPU waits idly.
*   **Interrupt-Driven I/O:**
    *   The CPU issues an I/O command and continues other work.
    *   The I/O device interrupts the CPU when it is ready.
    *   More efficient than Programmed I/O, but the CPU still handles the data transfer word-by-word.
*   **Direct Memory Access (DMA):**
    *   A dedicated **DMA Controller (DMAC)** manages data transfer between I/O device and memory.
    *   The CPU is only involved at the start and end (interrupted when the entire block is transferred).
    *   This is the most efficient method for large data transfers.

**2. I/O Mapping**
*   **Memory-Mapped I/O (MMIO):**
    *   I/O devices and memory share the same address space.
    *   CPU uses the same instructions (e.g., LOAD, STORE) to access both memory and I/O devices.
    *   **Advantage:** Simpler programming, can use all memory instructions.
    *   **Disadvantage:** Reduces the available address space for memory.
*   **I/O-Mapped I/O (Isolated I/O):**
    *   I/O devices have a separate, dedicated address space.
    *   CPU uses special I/O instructions (e.g., IN, OUT) to access devices.
    *   **Advantage:** Does not reduce memory address space.
    *   **Disadvantage:** Requires special instructions.










