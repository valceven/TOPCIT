# Computer Architecture & File Systems: Simplified Notes

## File Systems Overview

### What is a File System?
**Purpose**: Organize and store data on storage devices so the OS can find and access files quickly.

### File Components
- **Name**: Human-readable identifier
- **Location**: Where it's stored (path)
- **Size**: How much space it uses
- **Permissions**: Who can read/write/execute
- **Timestamps**: When created, modified, accessed

### File Allocation Methods

| **Method** | **How It Works** | **Pros** | **Cons** |
|------------|------------------|----------|----------|
| **Contiguous** | Files stored in consecutive blocks | Fast reading | Fragmentation, hard to expand |
| **Linked** | Files scattered, blocks linked with pointers | No fragmentation | Slow access, pointer overhead |
| **Indexed** | Central index block points to all file blocks | Fast direct access | Index overhead |

### Common File Systems

| **OS** | **File System** | **Notes** |
|--------|-----------------|-----------|
| **Windows** | NTFS, FAT | NTFS for modern systems |
| **Linux** | ext4, XFS | ext4 most common |
| **macOS** | HFS+, APFS | APFS for newer systems |
| **Unix** | UFS, ZFS | i-node based |

---

## Computer Architecture Basics

### Core Components

```
┌─────────────────┐
│      CPU        │ ← Brain: processes instructions
├─────────────────┤
│     Memory      │ ← Temporary storage (RAM)
├─────────────────┤
│    Storage      │ ← Permanent storage (disk)
├─────────────────┤
│   I/O Devices   │ ← Input/output (keyboard, screen)
└─────────────────┘
```

### Two Main Architectures

#### Von Neumann Architecture
- **Structure**: Instructions and data share same memory and bus
- **Advantage**: Simpler design
- **Disadvantage**: Bottleneck (can't fetch instruction and data simultaneously)
- **Used in**: Most modern computers

#### Harvard Architecture  
- **Structure**: Separate memory and buses for instructions and data
- **Advantage**: Can access instructions and data in parallel
- **Disadvantage**: More complex design
- **Used in**: Embedded systems, CPU cache design

**Modern Reality**: Most CPUs use hybrid approach - Harvard inside CPU (cache), Von Neumann outside CPU (main memory).

---

## CPU (Central Processing Unit)

### Main Components

| **Component** | **Function** | **Example** |
|---------------|--------------|-------------|
| **Control Unit** | Directs operations, fetches instructions | Traffic controller |
| **ALU** | Arithmetic and logic operations | Calculator |
| **Registers** | Fast temporary storage | Notepad |
| **Buses** | Data pathways | Roads |

### CPU Operation Cycle

```
1. FETCH → Get instruction from memory
2. DECODE → Figure out what instruction means  
3. EXECUTE → Perform the operation
4. STORE → Save results if needed
```

### CISC vs RISC

| **Aspect** | **CISC** | **RISC** |
|------------|----------|----------|
| **Philosophy** | Complex instructions do more | Simple instructions, do them fast |
| **Instruction Size** | Variable length | Fixed length (32-bit) |
| **Examples** | Intel x86 | ARM, MIPS |
| **Best For** | Desktop/server applications | Mobile devices, embedded systems |

---

## Memory Hierarchy

### Speed vs Cost Trade-off

```
FAST & EXPENSIVE ↑
├─ CPU Registers    ← Fastest, smallest
├─ Cache Memory     ← Very fast, small  
├─ Main Memory (RAM) ← Fast, medium size
├─ SSD Storage      ← Medium speed, large
└─ Hard Drive       ← Slow, largest
SLOW & CHEAP ↓
```

### Memory Types

| **Type** | **Speed** | **Volatility** | **Use** |
|----------|-----------|----------------|---------|
| **Registers** | Fastest | Volatile | CPU workspace |
| **Cache** | Very fast | Volatile | Recently used data |
| **RAM** | Fast | Volatile | Active programs |
| **SSD/HDD** | Slow | Non-volatile | Long-term storage |

### Memory Access Patterns

- **Temporal Locality**: Recently used data likely to be used again
- **Spatial Locality**: Nearby data likely to be used next
- **Sequential Locality**: Instructions usually executed in order

*These patterns help optimize cache performance*

---

## Input/Output (I/O) Systems

### I/O Controller Functions
- Control timing between CPU and devices
- Handle communication protocols
- Buffer data between fast CPU and slow devices
- Detect and report errors

### Memory-Mapped vs I/O-Mapped

| **Type** | **How It Works** | **Advantage** | **Disadvantage** |
|----------|------------------|---------------|------------------|
| **Memory-Mapped** | I/O devices use memory addresses | Easier programming | Reduces available memory |
| **I/O-Mapped** | Separate address space for I/O | Full memory available | More complex programming |

### DMA (Direct Memory Access)
**Purpose**: Allow devices to transfer data directly to/from memory without CPU involvement

**Benefits**: 
- Frees up CPU for other tasks
- Faster data transfer for high-speed devices
- Reduces system overhead

---

## Emerging Technologies

### Neuromorphic Chips

#### Traditional vs Neuromorphic

| **Aspect** | **Traditional Chip** | **Neuromorphic Chip** |
|------------|---------------------|----------------------|
| **Design** | Separate processing and memory | Combined processing and memory |
| **Operation** | Sequential (one at a time) | Parallel (many simultaneous) |
| **Learning** | Pre-programmed | Can learn and adapt |
| **Power** | Higher consumption | Very low power |
| **Best For** | General computing | AI, pattern recognition |

**Key Innovation**: Mimics brain structure where processing and memory are integrated, like neurons and synapses.

### Quantum Computers

#### Traditional vs Quantum Bits

| **Aspect** | **Traditional Bit** | **Quantum Bit (Qubit)** |
|------------|-------------------|-------------------------|
| **States** | 0 OR 1 | 0 AND 1 simultaneously |
| **Processing** | Sequential | Massive parallel processing |
| **Capability** | 8 bits = 256 possible calculations | 8 qubits = 256 simultaneous calculations |

#### Types of Quantum Computers

| **Type** | **Purpose** | **Status** |
|----------|-------------|-----------|
| **Quantum Annealing** | Optimization problems | Commercial (D-Wave) |
| **Quantum Gate** | General purpose computing | Research phase |
| **Quantum Neural Network** | AI applications | Early research |

**Current Reality**: Quantum computers exist but are experimental, requiring extreme conditions (near absolute zero temperature) and are limited to specific problem types.

---

## Key Takeaways

### File Systems
1. **Different allocation methods** trade speed for storage efficiency
2. **File system choice** depends on OS and use case
3. **Fragmentation** is ongoing challenge requiring management

### Computer Architecture  
1. **Memory hierarchy** balances speed, cost, and capacity
2. **CPU design** involves trade-offs between complexity and performance
3. **I/O systems** need optimization to avoid bottlenecks

### Future Technologies
1. **Neuromorphic chips** could revolutionize AI and IoT devices
2. **Quantum computers** may solve specific problems much faster
3. **Both technologies** are still in early stages but show promise

### Practical Impact
- **Neuromorphic**: Better AI in phones, cars, robots
- **Quantum**: Breaking encryption, drug discovery, financial modeling
- **Timeline**: Neuromorphic closer to market, quantum still years away for practical use

*Understanding these fundamentals helps in making informed decisions about technology choices and anticipating future developments.*

# Data Processing Technology: Essential Notes

## Parallel Processing Systems

### Why Parallel Processing Matters
**Current trend**: AI, cloud computing, and big data require massive computational power that single processors can't provide.

**Key drivers**: Intel vs NVIDIA vs Google competition for AI market dominance through parallel processing capabilities.

### Flynn's Taxonomy (4 Types of Computing)

| **Type** | **Instructions** | **Data** | **Description** | **Examples** |
|----------|------------------|----------|-----------------|--------------|
| **SISD** | Single | Single | Traditional sequential processing | Classic CPUs |
| **SIMD** | Single | Multiple | Same operation on multiple data | GPU graphics, Intel MMX |
| **MISD** | Multiple | Single | Different operations on same data | Pipeline processors (rare) |
| **MIMD** | Multiple | Multiple | Different operations on different data | Modern multi-core systems |

### Memory Architecture Types

#### Symmetric Multiprocessor (SMP)
- **Structure**: All CPUs share same memory
- **Pros**: Easy programming, shared memory
- **Cons**: Memory bottleneck, poor scalability
- **Use**: Desktop/server systems

#### Massive Parallel Processor (MPP)  
- **Structure**: Each CPU has own memory
- **Pros**: Excellent scalability
- **Cons**: Complex programming, network dependency
- **Use**: Supercomputers, clusters

#### Non-Uniform Memory Access (NUMA)
- **Structure**: Hybrid - local + shared global memory
- **Pros**: Best of both SMP and MPP
- **Cons**: Complex memory management
- **Use**: High-end servers

---

## CPU vs GPU Processing

### Architecture Differences

```
CPU (Few Powerful Cores)        GPU (Many Simple Cores)
┌─────────────────────────┐     ┌─────────────────────────┐
│  ALU  │  ALU  │  ALU   │     │ ALU ALU ALU ALU ALU ALU │
│       │       │        │     │ ALU ALU ALU ALU ALU ALU │
│  CACHE │ CACHE │ CACHE  │     │ ALU ALU ALU ALU ALU ALU │
│       │       │        │     │ ALU ALU ALU ALU ALU ALU │
└─────────────────────────┘     └─────────────────────────┘
```

### When to Use What

| **Task Type** | **Best Choice** | **Why** |
|---------------|-----------------|---------|
| **Complex logic, branching** | CPU | Smart cores handle complexity well |
| **Simple repetitive tasks** | GPU | Many cores work in parallel |
| **AI/Machine Learning** | GPU | Matrix operations benefit from parallelism |
| **Video rendering** | GPU | Originally designed for graphics |
| **Database queries** | CPU | Complex decision making required |

### GPU Programming Platforms

| **Platform** | **Developer** | **Best For** | **Language** |
|--------------|---------------|--------------|--------------|
| **CUDA** | NVIDIA | NVIDIA GPUs only | C-based |
| **OpenCL** | Khronos Group | Cross-platform | C-based |
| **C++ AMP** | Microsoft | Windows/Visual Studio | C++ |
| **OpenACC** | Multiple vendors | Easy programming | Directive-based |

---

## Storage Technology

### Storage Connection Types

#### Direct Attached Storage (DAS)
- **Connection**: Direct cable (SCSI, fiber)
- **Pros**: Simple, fast, low cost
- **Cons**: Limited scalability, no sharing
- **Use**: Single server storage

#### Network Attached Storage (NAS)
- **Connection**: Network (Ethernet)
- **Pros**: Easy sharing, centralized management
- **Cons**: Network speed limitations
- **Use**: File sharing, home/office storage

#### Storage Area Network (SAN)
- **Connection**: Dedicated fiber channel network
- **Pros**: High speed (8-16 Gbps), scalable
- **Cons**: Expensive, complex setup
- **Use**: Enterprise databases, high-performance applications

### Storage Comparison Table

| **Aspect** | **DAS** | **NAS** | **SAN** |
|------------|---------|---------|---------|
| **Speed** | High | Medium | Very High |
| **Cost** | Low | Medium | High |
| **Sharing** | No | Yes | Yes |
| **Scalability** | Limited | Good | Excellent |
| **Management** | Simple | Easy | Complex |

### IP-SAN Technologies

| **Technology** | **Purpose** | **Advantages** |
|----------------|-------------|----------------|
| **iSCSI** | SCSI over IP networks | Uses existing network, cost-effective |
| **FCIP** | Fiber Channel over IP | Connect remote SANs |
| **iFCP** | Internet Fiber Channel Protocol | Regional SAN connections |

---

## RAID Technology (Data Protection)

### RAID Levels Comparison

| **RAID Level** | **Min Disks** | **Fault Tolerance** | **Performance** | **Capacity** | **Use Case** |
|----------------|---------------|-------------------|-----------------|--------------|--------------|
| **RAID 0** | 2 | None | Excellent read/write | 100% | High performance (temp data) |
| **RAID 1** | 2 | 1 disk failure | Good read, slower write | 50% | Critical data (databases) |
| **RAID 5** | 3 | 1 disk failure | Good read, slower write | 67-90% | General business use |
| **RAID 6** | 4 | 2 disk failures | Good read, slow write | 50-88% | Large capacity, high reliability |
| **RAID 10** | 4 | 1 disk per mirror | Excellent | 50% | High performance + reliability |

### RAID Selection Guide

**Choose RAID 0**: Maximum speed, temporary data (video editing)
**Choose RAID 1**: Maximum reliability, critical data (databases)
**Choose RAID 5**: Balanced performance/cost (file servers)
**Choose RAID 6**: Large capacity with extra protection (backup systems)
**Choose RAID 10**: Best performance + reliability (enterprise databases)

---

## Disk Scheduling Algorithms

### How Disk Access Works
```
Seek Time + Rotational Delay + Transfer Time = Total Access Time
```

### Scheduling Algorithms

| **Algorithm** | **Method** | **Pros** | **Cons** | **Best For** |
|---------------|------------|----------|----------|--------------|
| **FCFS** | First come, first served | Simple, fair | Inefficient movement | Light loads |
| **SSTF** | Shortest seek time first | Fast average | Can cause starvation | General use |
| **SCAN** | Elevator algorithm | Fair, efficient | Varies by position | Heavy loads |
| **LOOK** | SCAN without end travel | More efficient than SCAN | Complex | Modern systems |
| **C-SCAN** | Circular scan | Uniform response time | More seek time | Real-time systems |

---

## Backup Technologies

### Linear Tape-Open (LTO)

| **Generation** | **Capacity** | **Speed** | **Year** |
|----------------|--------------|-----------|----------|
| **LTO-1** | 100 GB | 20 MB/s | 2000 |
| **LTO-8** | 12.8 TB | 427 MB/s | Current |
| **LTO-10** | 48 TB | 1,100 MB/s | Future |

### Virtual Tape Library (VTL)
- **Purpose**: Emulate tape devices using disk storage
- **Benefits**: Fast backup speed, easy management
- **Use**: Bridge between disk and tape backup strategies

---

## Graphics & Video Compression

### Compression Types

#### Lossless Compression
- **Principle**: Perfect reconstruction possible
- **Methods**: Run-length encoding, Huffman coding, dictionary coding
- **Use**: Text, medical images, archival storage
- **Trade-off**: Lower compression ratios

#### Lossy Compression  
- **Principle**: Some data lost, smaller files
- **Methods**: Transform coding, prediction coding
- **Use**: Photos, videos, audio
- **Trade-off**: Higher compression ratios

### Video Compression Standards

| **Standard** | **Year** | **Compression vs Previous** | **Applications** |
|--------------|----------|----------------------------|------------------|
| **MPEG-1** | 1993 | Baseline | MP3, Video CD |
| **MPEG-2** | 1995 | Better quality | DVD, Digital TV |
| **MPEG-4** | 1999 | Mobile optimized | Internet video, mobile |
| **H.264/AVC** | 2003 | 2x better than MPEG-2 | HDTV, Blu-ray, YouTube |
| **H.265/HEVC** | 2013 | 2x better than H.264 | 4K/8K TV, streaming |

### JPEG Image Compression Process
```
Original → Transform (DCT) → Quantize → Encode → Compressed
Image                                              Data

Compressed → Decode → Dequantize → Inverse → Reconstructed  
Data                                Transform    Image
```

---

## Parallel Programming Models

### Programming Approaches

| **Model** | **Type** | **Best For** | **Example** |
|-----------|----------|--------------|-------------|
| **OpenMP** | Shared memory | Multi-core CPUs | `#pragma omp parallel` |
| **MPI** | Message passing | Distributed systems | Supercomputer clusters |
| **CUDA** | GPU programming | NVIDIA graphics cards | Deep learning |
| **OpenCL** | Cross-platform GPU | Any GPU/CPU | Image processing |

### Load Balancing Types

- **AMP**: Each core runs separate OS (Asymmetric)
- **SMP**: Single OS manages all cores (Symmetric)  
- **BMP**: Apps bound to specific cores (Bound)

---

## Storage Optimization Techniques

### Thin Provisioning
- **Purpose**: Allocate storage space only when actually used
- **Benefit**: Higher utilization, flexible expansion
- **Use**: Cloud computing, virtualization

### Data Deduplication
- **Purpose**: Remove duplicate data to save space
- **Methods**: 
  - **Inline**: Remove duplicates as data arrives
  - **Offline**: Remove duplicates after storage
- **Benefit**: Significant space savings for backups

---

## Key Takeaways

### Parallel Processing
1. **GPU computing** is essential for AI and machine learning
2. **Memory architecture** affects scalability and performance
3. **Programming models** vary by hardware and application type

### Storage Systems
1. **Connection type** determines performance and cost
2. **RAID levels** balance performance, capacity, and reliability
3. **Backup strategies** should include both disk and tape

### Graphics/Video
1. **Compression standards** evolve for better efficiency
2. **Lossy vs lossless** depends on use case requirements
3. **Hardware acceleration** improves real-time processing

### Modern Trends
- **AI workloads** driving GPU adoption
- **Cloud storage** replacing traditional SAN/NAS
- **Video streaming** demanding better compression
- **Edge computing** requiring efficient local processing

*Understanding these technologies helps choose the right solution for specific performance, reliability, and cost requirements.*

# System Architecture Study Notes

## VIII. Fault Response Technology

### High Availability (HA)

**Definition**: Uninterrupted service with 99.999% availability (5 nines) = less than 5 minutes 15 seconds downtime/year

**Availability Formula**: 
```
A = MTBF / (MTBF + MTTR)
```
- MTBF: Mean Time Between Failures
- MTTR: Mean Time To Repair

### HA Configuration Types

#### 1. Hot Standby (Active-Standby)
- Simple HA clustering
- Active server + standby server (powered on, OS running)
- Automatic failover via heartbeat network
- Standby can be used as development system

#### 2. Mutual Takeover (Active-Active)
- Multiple systems with separate servers
- Services switch to designated server on failure
- Each server needs capacity for both services
- Requires sufficient system resources

#### 3. Concurrent Access
- Multiple systems process tasks in parallel
- All servers active
- No failover needed - service continues if server fails
- Uses L4 switch for load balancing

### Fault-Tolerant Systems

**Definition**: Systems that continue functioning even when components fail

#### Troubleshooting Steps
1. **Fault Detection**: Analyze which module caused fault
2. **Fault Diagnosis**: Determine if fault is temporary or permanent
3. **Fault Isolation**: Block error spread
4. **Fault Recovery**: Eliminate faulty module and reconfigure

#### Fault-Tolerant Techniques

**General Techniques**:
- Checkpoint technique
- Protocol monitoring

**Hardware Techniques**:
- Triple Modular Redundancy
- RAID (disk mirroring, parity bits)
- Duplication with Comparison
- Stand by Sparing
- Watchdog Timer

**Software Techniques**:
- Checkpointer
- Recover block
- Conversation
- Distributed rollback

### Disaster Recovery System (DRS)

**Purpose**: Minimize disaster impact by locating infrastructure in different location

#### DR Center Types

| Type | Description | RTO |
|------|-------------|-----|
| **Mirror Site** | Same facility/IT devices as main center, real-time active-active | Immediate |
| **Hot Site** | Same facility but standby state (active-standby) | Within 4 hours |
| **Warm Site** | Only crucial IT resources, transfer components during disaster | Days-weeks |
| **Cold Site** | Only data in remote location, minimal resources | Weeks-months |

#### Key Metrics
- **RTO** (Recovery Time Objective): Maximum allowable downtime
- **RPO** (Recovery Point Objective): Tolerable data loss amount

---

## IX. Cloud Computing Technology

### Definition
Computing environment that leases IT resources through Internet, based on virtualization and distributed processing, with usage-based payment.

### Benefits
- **Costs**: CAPEX reduction, OPEX increase, TCO reduction
- **Period**: Reduced development time and cycles
- **Operation**: Reduced personnel, improved efficiency
- **Product**: Improved integration

### Cloud vs Other Technologies

#### Grid Computing vs Cloud Computing
| Aspect | Grid Computing | Cloud Computing |
|--------|---------------|-----------------|
| Computer Location | Geographically scattered, different orgs | Scattered but centrally managed |
| Configuration | Heterogeneous mixture | Mostly same model |
| Usage | Scientific/technical calculations | General-purpose applications |

### Cloud Service Types

#### By Service Type
1. **IaaS** (Infrastructure as a Service)
   - Provides infrastructure resources (server, storage, network)
   - User manages OS and above
   - Can be virtualized or bare-metal

2. **PaaS** (Platform as a Service)
   - Development and operating environment as service
   - Provides network infrastructure to application runtime
   - User manages applications and data

3. **SaaS** (Software as a Service)
   - Software delivered through web browser
   - Usage-based cost, on-demand, no IT management needed
   - Examples: Google Docs, Salesforce.com

#### By Operation Form
- **Public Cloud**: Services open to general public via Internet
- **Private Cloud**: Services on closed network for authorized users only
- **Hybrid Cloud**: Combination of public and private clouds

### Server Virtualization Technology

#### Hypervisor Types

**Native Type (Type 1)**:
- Installed directly on hardware
- No host OS required
- Examples: Xen, ESX Server, Hyper-V, KVM

**Hosted Type (Type 2)**:
- Software installed on existing OS
- Examples: VirtualPC, VMware Workstation, VirtualBox

#### Virtualization Methods

1. **Full Virtualization**
   - Complete hardware virtualization
   - No guest OS modification needed
   - Requires CPU virtualization support (Intel VT, AMD-V)

2. **Para-virtualization**
   - Hardware not completely virtualized
   - Guest OS uses hypervisor API
   - Requires guest OS kernel modification
   - Higher performance, only open-source OS

3. **OS-Level Virtualization (Containers)**
   - Uses OS container technology instead of hypervisor
   - Guest OS must match host OS
   - Examples: Docker, LXC, Solaris Containers

#### Container Advantages
- Quick start/finish
- High density (multiple containers per OS)
- Low overhead
- Application-specific container support

### Cloud Platforms

#### OpenStack
Open-source cloud computing platform with components:
- **Nova**: Virtual machine management
- **Swift**: Object storage
- **Glance**: Virtual disk image management
- **Keystone**: Authentication system
- **Cinder**: Block storage
- **Neutron**: Network service

#### Kubernetes
Container orchestration platform for management and operation

#### Mesos
Resource management for integrated cloud infrastructure and computing resources

---

## X. Big Data System

### Hadoop Ecosystem

**Hadoop**: High-availability distributed object-oriented platform for distributed processing of large data volumes

#### Core Components

**HDFS** (Hadoop Distributed File System):
- Distributed file system
- Prevents data loss through replication
- Stream access required
- Read-only data integrity
- NameNode (master) + DataNodes (slaves)

**MapReduce**:
- Distributed programming model
- **Map**: Classify scattered data into key-value pairs
- **Reduce**: Remove duplicates and extract desired data

#### Hadoop Support Programs

| Type | Technology | Function |
|------|------------|----------|
| **Data Collection** | Flume, Scribe, Chuckwa, Sqoop | Unstructured/structured data collection |
| **Storage** | HBase, Cassandra | Distributed NoSQL databases |
| **Processing** | Hive, Pig, Spark | Data analysis and processing |
| **Real-time** | Impala | Real-time SQL queries |
| **Management** | Oozie, Zookeeper, YARN | Workflow and resource management |

#### Commercial Solutions
- **Cloudera**: CDH + Cloudera Manager
- **Hortonworks**: HDP (all free, revenue from support)
- **MapR**: M3 (free), M5/M7 (paid versions)

### Big Data Trends
- Ecosystem formation based on enterprise strengths
- Differentiation of service delivery domains
- Still low versatility for non-engineers
- Growth of open-source systems
- Strengthened AI linkage

---

## XI. Network and Datalink Layer

### Datalink Layer Concept

**Purpose**: Transmit data between network devices using physical layer, responsible for:
- Address allocation
- Error detection

**Importance**: Critical for embedded software, network debugging, short-range wireless (Bluetooth, ZigBee)

### Datalink Layer Structure

#### Sub-layers
1. **LLC** (Logical Link Control)
   - Connection between MAC and network layer
   - Types: Type 1 (unconfirmed datagram), Type 2 (virtual circuit), Type 3 (confirmed datagram)

2. **MAC** (Media Access Control)
   - Controls data transfer through physical media
   - Contains MAC addresses (48-bit)
   - First 24 bits: OUI (manufacturer), Last 24 bits: serial number

### Address Resolution

#### ARP (Address Resolution Protocol)
- Converts IP addresses to MAC addresses
- Uses broadcast to find MAC address
- Stores results in cache memory

#### RARP (Reverse Address Resolution Protocol)
- Converts MAC addresses to IP addresses

### Error Control

#### Error Types
- **Single-bit errors**: One bit changed
- **Multi-bit errors**: Multiple non-contiguous bits changed
- **Burst errors**: Multiple consecutive bits changed

#### Error Control Methods

**Forward Error Correction (FEC)**:
- Receiving device detects and corrects errors
- Transmits spare bits for error recovery

**Backward Error Correction (BEC)**:
- Notifies transmitting device of errors
- Requests retransmission

#### Error Detection Methods
- **VRC** (Vertical Redundancy Check): Parity check
- **LRC** (Longitudinal Redundancy Check): Byte parity collection
- **CRC** (Cyclic Redundancy Check): Binary division method
- **Checksum**: Higher-level protocol method

#### ARQ (Automatic Repeat Request) Types
1. **Stop-and-wait ARQ**: Send one frame, wait for ACK/NAK
2. **Go-back-N ARQ**: Continuous transmission with sequence numbers
3. **Selective-repeat ARQ**: Retransmit only error frames
4. **Adaptive ARQ**: Dynamic frame length based on error rate
5. **Hybrid-ARQ**: Combines FEC and BEC

### IEEE 802 Standards

#### IEEE 802.11 (Wi-Fi)
| Protocol | Frequency | Speed | Modulation | Features |
|----------|-----------|-------|------------|----------|
| 802.11b | 2.4 GHz | 11 Mbps | DSSS | Basic wireless |
| 802.11a | 5 GHz | 54 Mbps | OFDM | Higher frequency |
| 802.11g | 2.4 GHz | 54 Mbps | OFDM | Backward compatible |
| 802.11n | 2.4/5 GHz | 600 Mbps | OFDM | MIMO support |
| 802.11ac | 5 GHz | 6.93 Gbps | OFDM | 256-QAM, beamforming |

#### IEEE 802.15 (WPAN)
| Standard | Technology | Frequency | Speed | Distance | Use Case |
|----------|------------|-----------|-------|----------|----------|
| 802.15.1 | Bluetooth | 2.4 GHz | Variable | 10-100m | Voice/file transfer |
| 802.15.3 | UWB | 3.1-10.6 GHz | 480 Mbps | 10m | Multimedia |
| 802.15.4 | ZigBee | 868 MHz/2.4 GHz | 20-250 Kbps | 10-75m | Sensor networks |

---

## Key Concepts Summary

- **High Availability**: 99.999% uptime through redundancy and failover
- **Disaster Recovery**: Geographically distributed backup systems with defined RTO/RPO
- **Cloud Computing**: Virtualized, on-demand IT resources with service models (IaaS/PaaS/SaaS)
- **Big Data**: Hadoop ecosystem for distributed storage and processing of large datasets
- **Networking**: Datalink layer protocols for reliable data transmission and error control

# System Architecture Study Notes

## VIII. Fault Response Technology

### High Availability (HA)

**Definition**: Uninterrupted service with 99.999% availability (5 nines) = less than 5 minutes 15 seconds downtime/year

**Availability Formula**: 
```
A = MTBF / (MTBF + MTTR)
```
- MTBF: Mean Time Between Failures
- MTTR: Mean Time To Repair

### HA Configuration Types

#### 1. Hot Standby (Active-Standby)
- Simple HA clustering
- Active server + standby server (powered on, OS running)
- Automatic failover via heartbeat network
- Standby can be used as development system

#### 2. Mutual Takeover (Active-Active)
- Multiple systems with separate servers
- Services switch to designated server on failure
- Each server needs capacity for both services
- Requires sufficient system resources

#### 3. Concurrent Access
- Multiple systems process tasks in parallel
- All servers active
- No failover needed - service continues if server fails
- Uses L4 switch for load balancing

### Fault-Tolerant Systems

**Definition**: Systems that continue functioning even when components fail

#### Troubleshooting Steps
1. **Fault Detection**: Analyze which module caused fault
2. **Fault Diagnosis**: Determine if fault is temporary or permanent
3. **Fault Isolation**: Block error spread
4. **Fault Recovery**: Eliminate faulty module and reconfigure

#### Fault-Tolerant Techniques

**General Techniques**:
- Checkpoint technique
- Protocol monitoring

**Hardware Techniques**:
- Triple Modular Redundancy
- RAID (disk mirroring, parity bits)
- Duplication with Comparison
- Stand by Sparing
- Watchdog Timer

**Software Techniques**:
- Checkpointer
- Recover block
- Conversation
- Distributed rollback

### Disaster Recovery System (DRS)

**Purpose**: Minimize disaster impact by locating infrastructure in different location

#### DR Center Types

| Type | Description | RTO |
|------|-------------|-----|
| **Mirror Site** | Same facility/IT devices as main center, real-time active-active | Immediate |
| **Hot Site** | Same facility but standby state (active-standby) | Within 4 hours |
| **Warm Site** | Only crucial IT resources, transfer components during disaster | Days-weeks |
| **Cold Site** | Only data in remote location, minimal resources | Weeks-months |

#### Key Metrics
- **RTO** (Recovery Time Objective): Maximum allowable downtime
- **RPO** (Recovery Point Objective): Tolerable data loss amount

---

## IX. Cloud Computing Technology

### Definition
Computing environment that leases IT resources through Internet, based on virtualization and distributed processing, with usage-based payment.

### Benefits
- **Costs**: CAPEX reduction, OPEX increase, TCO reduction
- **Period**: Reduced development time and cycles
- **Operation**: Reduced personnel, improved efficiency
- **Product**: Improved integration

### Cloud vs Other Technologies

#### Grid Computing vs Cloud Computing
| Aspect | Grid Computing | Cloud Computing |
|--------|---------------|-----------------|
| Computer Location | Geographically scattered, different orgs | Scattered but centrally managed |
| Configuration | Heterogeneous mixture | Mostly same model |
| Usage | Scientific/technical calculations | General-purpose applications |

### Cloud Service Types

#### By Service Type
1. **IaaS** (Infrastructure as a Service)
   - Provides infrastructure resources (server, storage, network)
   - User manages OS and above
   - Can be virtualized or bare-metal

2. **PaaS** (Platform as a Service)
   - Development and operating environment as service
   - Provides network infrastructure to application runtime
   - User manages applications and data

3. **SaaS** (Software as a Service)
   - Software delivered through web browser
   - Usage-based cost, on-demand, no IT management needed
   - Examples: Google Docs, Salesforce.com

#### By Operation Form
- **Public Cloud**: Services open to general public via Internet
- **Private Cloud**: Services on closed network for authorized users only
- **Hybrid Cloud**: Combination of public and private clouds

### Server Virtualization Technology

#### Hypervisor Types

**Native Type (Type 1)**:
- Installed directly on hardware
- No host OS required
- Examples: Xen, ESX Server, Hyper-V, KVM

**Hosted Type (Type 2)**:
- Software installed on existing OS
- Examples: VirtualPC, VMware Workstation, VirtualBox

#### Virtualization Methods

1. **Full Virtualization**
   - Complete hardware virtualization
   - No guest OS modification needed
   - Requires CPU virtualization support (Intel VT, AMD-V)

2. **Para-virtualization**
   - Hardware not completely virtualized
   - Guest OS uses hypervisor API
   - Requires guest OS kernel modification
   - Higher performance, only open-source OS

3. **OS-Level Virtualization (Containers)**
   - Uses OS container technology instead of hypervisor
   - Guest OS must match host OS
   - Examples: Docker, LXC, Solaris Containers

#### Container Advantages
- Quick start/finish
- High density (multiple containers per OS)
- Low overhead
- Application-specific container support

### Cloud Platforms

#### OpenStack
Open-source cloud computing platform with components:
- **Nova**: Virtual machine management
- **Swift**: Object storage
- **Glance**: Virtual disk image management
- **Keystone**: Authentication system
- **Cinder**: Block storage
- **Neutron**: Network service

#### Kubernetes
Container orchestration platform for management and operation

#### Mesos
Resource management for integrated cloud infrastructure and computing resources

---

## X. Big Data System

### Hadoop Ecosystem

**Hadoop**: High-availability distributed object-oriented platform for distributed processing of large data volumes

#### Core Components

**HDFS** (Hadoop Distributed File System):
- Distributed file system
- Prevents data loss through replication
- Stream access required
- Read-only data integrity
- NameNode (master) + DataNodes (slaves)

**MapReduce**:
- Distributed programming model
- **Map**: Classify scattered data into key-value pairs
- **Reduce**: Remove duplicates and extract desired data

#### Hadoop Support Programs

| Type | Technology | Function |
|------|------------|----------|
| **Data Collection** | Flume, Scribe, Chuckwa, Sqoop | Unstructured/structured data collection |
| **Storage** | HBase, Cassandra | Distributed NoSQL databases |
| **Processing** | Hive, Pig, Spark | Data analysis and processing |
| **Real-time** | Impala | Real-time SQL queries |
| **Management** | Oozie, Zookeeper, YARN | Workflow and resource management |

#### Commercial Solutions
- **Cloudera**: CDH + Cloudera Manager
- **Hortonworks**: HDP (all free, revenue from support)
- **MapR**: M3 (free), M5/M7 (paid versions)

### Big Data Trends
- Ecosystem formation based on enterprise strengths
- Differentiation of service delivery domains
- Still low versatility for non-engineers
- Growth of open-source systems
- Strengthened AI linkage

---

## XI. Network and Datalink Layer

### Datalink Layer Concept

**Purpose**: Transmit data between network devices using physical layer, responsible for:
- Address allocation
- Error detection

**Importance**: Critical for embedded software, network debugging, short-range wireless (Bluetooth, ZigBee)

### Datalink Layer Structure

#### Sub-layers
1. **LLC** (Logical Link Control)
   - Connection between MAC and network layer
   - Types: Type 1 (unconfirmed datagram), Type 2 (virtual circuit), Type 3 (confirmed datagram)

2. **MAC** (Media Access Control)
   - Controls data transfer through physical media
   - Contains MAC addresses (48-bit)
   - First 24 bits: OUI (manufacturer), Last 24 bits: serial number

### Address Resolution

#### ARP (Address Resolution Protocol)
- Converts IP addresses to MAC addresses
- Uses broadcast to find MAC address
- Stores results in cache memory

#### RARP (Reverse Address Resolution Protocol)
- Converts MAC addresses to IP addresses

### Error Control

#### Error Types
- **Single-bit errors**: One bit changed
- **Multi-bit errors**: Multiple non-contiguous bits changed
- **Burst errors**: Multiple consecutive bits changed

#### Error Control Methods

**Forward Error Correction (FEC)**:
- Receiving device detects and corrects errors
- Transmits spare bits for error recovery

**Backward Error Correction (BEC)**:
- Notifies transmitting device of errors
- Requests retransmission

#### Error Detection Methods
- **VRC** (Vertical Redundancy Check): Parity check
- **LRC** (Longitudinal Redundancy Check): Byte parity collection
- **CRC** (Cyclic Redundancy Check): Binary division method
- **Checksum**: Higher-level protocol method

#### ARQ (Automatic Repeat Request) Types
1. **Stop-and-wait ARQ**: Send one frame, wait for ACK/NAK
2. **Go-back-N ARQ**: Continuous transmission with sequence numbers
3. **Selective-repeat ARQ**: Retransmit only error frames
4. **Adaptive ARQ**: Dynamic frame length based on error rate
5. **Hybrid-ARQ**: Combines FEC and BEC

### IEEE 802 Standards

#### IEEE 802.11 (Wi-Fi)
| Protocol | Frequency | Speed | Modulation | Features |
|----------|-----------|-------|------------|----------|
| 802.11b | 2.4 GHz | 11 Mbps | DSSS | Basic wireless |
| 802.11a | 5 GHz | 54 Mbps | OFDM | Higher frequency |
| 802.11g | 2.4 GHz | 54 Mbps | OFDM | Backward compatible |
| 802.11n | 2.4/5 GHz | 600 Mbps | OFDM | MIMO support |
| 802.11ac | 5 GHz | 6.93 Gbps | OFDM | 256-QAM, beamforming |

#### IEEE 802.15 (WPAN)
| Standard | Technology | Frequency | Speed | Distance | Use Case |
|----------|------------|-----------|-------|----------|----------|
| 802.15.1 | Bluetooth | 2.4 GHz | Variable | 10-100m | Voice/file transfer |
| 802.15.3 | UWB | 3.1-10.6 GHz | 480 Mbps | 10m | Multimedia |
| 802.15.4 | ZigBee | 868 MHz/2.4 GHz | 20-250 Kbps | 10-75m | Sensor networks |

---

## XII. Network Layer Protocol and Equipment

### Network Layer Overview

**Purpose**: Third layer of OSI/TCP-IP model responsible for sending packets from transmitting to receiving side

**Key Functions**:
- **Packetizing**: Encapsulation/decapsulation of payload without changes
- **Routing**: Finding path to transfer payload from source to destination  
- **Forwarding**: Router creates decision/routing table when packet arrives

### Internetworking Equipment

| Equipment | Description | OSI Layer |
|-----------|-------------|-----------|
| **Repeater** | Amplifies/reproduces signals between connection points | Physical |
| **Bridge** | Connects two LANs, interpretation and format conversion | Data Link |
| **Switch** | Multi-port bridge, separates network by MAC address | Data Link |
| **Router** | Finds optimal path when connecting heterogeneous networks | Network |

### Router Structure

**Components**:
- **Control Plane**: Software-implemented, determines packet destination using tables
- **Forwarding Plane**: Actually sends packets according to control plane requirements

**Router Metrics**:
- **Number of hops**: Router count to destination (fewer = faster)
- **MTU**: Maximum Transmission Unit data size
- **Cost**: Based on transfer time, reliability, bandwidth
- **Latency**: Packet delay and bottlenecks during transfer

### Packet Switching Methods

#### Datagram Approach
- Non-connected service
- Packets processed independently
- Different paths possible
- Destination address determines forwarding

#### Virtual Circuit Approach  
- Connection-oriented service
- Virtual path established before transfer
- All packets use same path
- Packet label determines forwarding

### Network Layer Protocols

| Protocol | Purpose |
|----------|---------|
| **ARP** | Convert IP address to MAC address |
| **RARP** | Convert MAC address to IP address |
| **ICMP** | Transfer network error information |
| **IGMP** | IP multicast transfer |

### Network Commands

| Command | Function |
|---------|----------|
| **ping** | Test network connectivity using ICMP |
| **tracert/traceroute** | Find path to destination |
| **route** | Manual routing table modification |
| **ipconfig/ifconfig** | Check TCP/IP network settings |
| **netstat** | Check network connections and status |
| **arp** | Show/change local ARP cache |

### Quality of Service (QoS)

**QoS Attributes**:
- **Confidence**: Ability to deliver packets safely
- **Delay**: Transmission time from source to destination
- **Jitter**: Delay variation for same flow packets
- **Bandwidth**: Maximum communication rate available

**QoS Implementation Techniques**:

#### Packet Scheduling
- **FIFO queuing**: First-in-first-out delivery
- **Priority queuing**: Higher priority packets first
- **Weighted fair queuing**: Round-robin with weighted delivery

#### Traffic Control
- **Traffic Shaping**: Control speed/volume when leaving network
- **Traffic Policing**: Control speed/volume when entering network
- **Leaky Bucket**: Store burst packets, output at average speed
- **Token Bucket**: Basic algorithm for traffic shaping/policing

#### Service Quality Models
- **IntServ**: Flow-based, explicit resource reservation
- **DiffServ**: Class-based, packet priority operation
- **RSVP**: Resource reservation protocol for bandwidth

### Routing Algorithms and Protocols

#### Algorithm Types

**Link State Algorithm**:
- Each router calculates low-cost path to all destinations
- Uses complete network topology information
- Example: **Dijkstra Algorithm**

**Distance Vector Algorithm**:
- Maintains low-cost path table to destination routers
- Notifies path cost data to neighboring routers
- Example: **Bellman-Ford Algorithm**

#### Routing Protocol Classification

**By Autonomous System (AS)**:
- **IGP** (Interior Gateway Protocol): Within AS
  - RIP, OSPF, IGRP
- **EGP** (Exterior Gateway Protocol): Between AS
  - BGP

**Protocol Details**:

| Protocol | Type | Features |
|----------|------|----------|
| **RIP** | Distance Vector | 30-second updates, 16-hop limit, no VLSM |
| **IGRP** | Distance Vector | Reflects network state, 255-hop limit, load balance |
| **OSPF** | Link State | Fast updates, VLSM support, load balancing |
| **BGP** | Path Vector | AS interconnection, TCP-based |

### IPv4 Overview

**IPv4 Address Structure**: 32-bit address in dotted decimal notation

#### Address Classes

| Class | Range | Network/Host Bits | Default Mask |
|-------|-------|------------------|--------------|
| **A** | 1.0.0.0 - 126.255.255.255 | 8/24 | 255.0.0.0 |
| **B** | 128.0.0.0 - 191.255.255.255 | 16/16 | 255.255.0.0 |
| **C** | 192.0.0.0 - 223.255.255.255 | 24/8 | 255.255.255.0 |
| **D** | 224.0.0.0 - 239.255.255.255 | Multicast | - |
| **E** | 240.0.0.0 - 255.255.255.255 | Reserved | - |

#### Special IPv4 Addresses

- **127.x.x.x**: Loopback address
- **255.255.255.255**: Limited broadcast
- **0.0.0.0**: This host on this network
- **169.254.x.x**: APIPA (Automatic Private IP Addressing)

**Private Address Ranges**:
- Class A: 10.0.0.0 - 10.255.255.255
- Class B: 172.16.0.0 - 172.31.255.255  
- Class C: 192.168.0.0 - 192.168.255.255

#### Subnetting and CIDR

**Subnetting**: Dividing network into smaller subnets
**Supernetting**: Combining multiple networks into one large network
**CIDR**: Classless Inter-Domain Routing with flexible network/host boundaries

#### DHCP Process
1. **DHCPDISCOVER**: Client broadcasts IP request
2. **DHCPOFFER**: Server offers IP configuration
3. **DHCPREQUEST**: Client requests specific lease
4. **DHCPACK**: Server acknowledges IP assignment

#### NAT (Network Address Translation)
- **Basic NAT**: One-to-one private-to-public IP mapping
- **NAPT**: Multiple private IPs share one public IP using port numbers

### IPv6 Overview

**Features**:
- 128-bit addressing (3.4 x 10³⁸ addresses)
- Simplified header format
- Built-in security (IPsec)
- Better QoS support

**Address Types**:
- **Link-local**: FE80::/10 - internal network only
- **Global unicast**: 2001::/3 - internet routable
- **Multicast**: FF00::/8 - group delivery
- **Anycast**: Delivery to nearest interface

---

## XIV. Transport Layer Protocol

### Transport Layer Overview

**Purpose**: End-to-end communication between application processes

**Key Protocols**:
- **TCP**: Connection-oriented, reliable
- **UDP**: Connectionless, unreliable  
- **SCTP**: Combines TCP and UDP advantages

### TCP (Transmission Control Protocol)

#### TCP Characteristics

**Connection-oriented**: Requires three-way handshake
**Reliable**: Uses acknowledgments and sequence numbers
**Stream-based**: Continuous data flow with buffers
**Full-duplex**: Bidirectional communication

#### TCP Control Mechanisms

**Flow Control**:
- **Sliding Window Protocol**: Controls data flow rate
- **Window Size**: Receiver advertises available buffer space
- **RWND**: Receiver window size
- **CWND**: Congestion window size

**Error Control**:
- **Checksum**: Error detection in segments
- **Acknowledgment**: Confirms data receipt
- **Retransmission**: Resends lost/damaged segments

**Congestion Control**:
- **Slow Start**: Exponential window increase until threshold
- **Congestion Avoidance**: Linear window increase after threshold

#### TCP Connection Management

**Three-Way Handshake** (Connection Establishment):
1. Client → Server: SYN (seq=x)
2. Server → Client: SYN+ACK (seq=y, ack=x+1)
3. Client → Server: ACK (seq=x+1, ack=y+1)

**Connection Termination**:
1. Client → Server: FIN
2. Server → Client: ACK
3. Server → Client: FIN  
4. Client → Server: ACK

#### TCP Header Fields

| Field | Size | Purpose |
|-------|------|---------|
| Source Port | 16 bits | Sending application port |
| Destination Port | 16 bits | Receiving application port |
| Sequence Number | 32 bits | First byte number in segment |
| Acknowledgment | 32 bits | Next expected byte number |
| Window Size | 16 bits | Available buffer space |
| Checksum | 16 bits | Error detection |

#### TCP Timers

- **Retransmission Timer**: Wait for ACK before retransmission
- **Persistence Timer**: Resolve deadlock situations
- **Keepalive Timer**: Prevent idle connections
- **Time-wait Timer**: Used during connection termination

#### Well-known TCP Ports

| Service | Port | Service | Port |
|---------|------|---------|------|
| FTP | 21 (control), 20 (data) | DNS | 53 |
| SSH | 22 | HTTP | 80 |
| Telnet | 23 | POP3 | 110 |
| SMTP | 25 | IMAP4 | 143 |

### UDP (User Datagram Protocol)

#### UDP Characteristics

**Connectionless**: No connection establishment
**Unreliable**: No acknowledgments or retransmissions
**Simple**: Minimal overhead
**Fast**: No flow/congestion control
**Best-effort**: Application handles reliability if needed

#### UDP Applications

- Simple request-response communication
- Processes with internal flow/error control
- Multicasting transmission
- Management processes (SNMP)
- Routing protocols (RIP)
- Real-time applications (video streaming)

#### UDP Header

| Field | Size | Purpose |
|-------|------|---------|
| Source Port | 16 bits | Sending application port |
| Destination Port | 16 bits | Receiving application port |
| Length | 16 bits | UDP header + data length |
| Checksum | 16 bits | Error detection |

#### Well-known UDP Ports

| Service | Port | Service | Port |
|---------|------|---------|------|
| NTP | 123 | RIP | 520 |
| DHCP Server | 67 | RIPng | 521 |
| DHCP Client | 68 | OLSR | 698 |
| TFTP | 69 | Syslog | 514 |
| Kerberos | 88 | Timed | 525 |

### SCTP (Stream Control Transmission Protocol)

#### SCTP Features

**Multi-streaming**: Multiple data streams per association
**Multi-homing**: Multiple IP addresses per endpoint
**Connection-oriented**: Called "association"
**Reliable**: Uses acknowledgments and checksums
**Full-duplex**: Bidirectional communication

#### SCTP Advantages over TCP/UDP

- **Message-oriented**: Preserves message boundaries
- **Multi-stream**: Avoids head-of-line blocking
- **Multi-homing**: Network-level fault tolerance
- **Enhanced security**: Four-way handshake prevents SYN attacks

#### SCTP Numbering Systems

- **TSN** (Transmission Sequence Number): Numbers data chunks
- **SI** (Stream Identifier): Distinguishes streams (16-bit)
- **SSN** (Stream Sequence Number): Orders chunks within stream

#### SCTP Functions

1. **Association Management**: Start/end connections
2. **Sequenced Delivery**: Ordered data delivery per stream
3. **User Data Fragmentation**: Handle MTU limitations
4. **Acknowledgment**: Ensure reliable delivery
5. **Congestion Avoidance**: Similar to TCP mechanisms
6. **Chunk Bundling**: Multiple chunks per packet
7. **Packet Validation**: Verification tag and checksum
8. **Path Management**: Multi-homing support

---

## XV. Application Layer Technologies

### Application Layer Protocol Overview

**Purpose**: Exchange information between application programs

**Common Protocols**:
- **HTTP**: Web data transmission
- **FTP**: File transfer
- **SMTP/POP3/IMAP**: Email
- **DNS**: Hostname to IP mapping
- **SNMP**: Network management
- **Telnet**: Remote terminal access

### HTTP (Hypertext Transfer Protocol)

#### HTTP Characteristics

**Request/Response Protocol**: Client-server communication
**Text-based**: Human-readable message format
**Stateless**: Each request independent
**Current Version**: HTTP/1.1 (most common)

#### HTTP Methods

- **GET**: Retrieve content from server
- **POST**: Send data to server (forms, user input)
- **PUT**: Upload file to server
- **DELETE**: Remove resource from server
- **HEAD**: Get headers only (no body)

#### HTTP Status Codes

| Range | Type | Examples |
|-------|------|----------|
| **2xx** | Success | 200 OK, 206 Partial Content |
| **3xx** | Redirection | 301 Moved Permanently |
| **4xx** | Client Error | 404 Not Found, 403 Forbidden |
| **5xx** | Server Error | 500 Internal Server Error |

### FTP (File Transfer Protocol)

#### FTP Characteristics

**Dual Connection**:
- **Control Connection**: Port 21, maintained throughout session
- **Data Connection**: Port 20 (or other), established per transfer

#### FTP Transfer Modes

**Active Mode (General Transfer)**:
1. Client connects to server port 21
2. Client informs server of data port
3. Server port 20 connects to client data port
4. Data transfer occurs

**Passive Mode (PASV)**:
1. Client connects to server port 21
2. Server informs client of data port
3. Client connects to server data port
4. Data transfer occurs

**Benefits of Passive Mode**:
- Works through firewalls
- Supports proxy servers
- Client IP doesn't need external visibility

#### FTP Command Types

- **Access Commands**: USER, PASS, QUIT
- **File Management**: CWD, DELE, LIST, MKD, PWD
- **Data Formatting**: TYPE, STRU, MODE
- **Port Definition**: PORT, PASV
- **File Transfer**: GET, PUT, RETR, STOR

---

## XVI. Mobile Communication and Multimedia

### Multimedia Network

#### Data Compression Types

**Lossless Compression** (Reversible):
- No information loss during compression/decompression
- Lower compression rates
- Methods: Run-length encoding, Huffman coding, arithmetic coding

**Lossy Compression** (Irreversible):
- Some data lost to achieve higher compression
- Methods: Prediction coding, transform coding
- Used for multimedia where perfect reproduction not critical

#### Multimedia Data Types

**Text**: Plain text, hypertext using Unicode
**Image**: Still images using JPEG (DCT transformation)
**Video**: Multiple frames, spatial/temporal compression
**Audio**: Digitized using ADC (sampling + quantization)

#### QoS in Multimedia Networks

**QoS Techniques**:
- **RSVP**: Resource reservation with fixed bandwidth allocation
- **TOS Field**: Type of Service priority classification (8 levels: 0-7)

### Internet Telephony (VoIP)

#### VoIP Overview

**Definition**: Voice communication over IP packet networks
**Components**:
- **Media Gateway**: Multimedia data exchange and control
- **Signaling Gateway**: Call signaling and network conversion

#### VoIP Signaling Protocols

**SIP (Session Initiation Protocol)**:
- Application layer signaling protocol
- HTTP-like text-based format
- Scalable and extensible
- URL/email-style addressing

**H.323**:
- ITU-T standard for multimedia over LAN
- Widely used by early VoIP providers
- Complex but comprehensive protocol suite

#### SIP Components

| Component | Purpose |
|-----------|---------|
| **SIP** | Core signaling protocol (RFC 3261) |
| **SDP** | Session Description Protocol |
| **Audio Codec** | G.711A, G.723.1, G.729A |
| **Video Codec** | H.263, MPEG-4, H.264 |
| **RTP/RTCP** | Real-time transport protocols |

#### VoLTE (Voice over LTE)

**Implementation**: Voice services over LTE all-IP network
**Architecture**: Uses IMS (IP Multimedia Subsystem)
**Evolution**: Circuit-switched fallback → full VoLTE

### Media Transport Protocols

#### RTP (Real-Time Transport Protocol)

**Purpose**: Process real-time traffic over Internet
**Transport**: Operates over UDP
**Features**: Timestamp and sequence numbering for media synchronization

#### RTCP (Real-Time Control Protocol)

**Purpose**: Control protocol for RTP streams
**Functions**: Quality monitoring, sender/receiver reports
**Packet Types**: Sender report, receiver report, source description

#### RTSP (Real-Time Streaming Protocol)

**Purpose**: Control streaming media servers
**Commands**: PLAY, PAUSE, STOP (VCR-like operations)
**Standard**: IETF RFC 2326

#### IMS (IP Multimedia Subsystem)

**Definition**: 3GPP-defined platform for IP multimedia services
**Core Technology**: SIP-based call control
**Components**:
- **CSCF**: Call Session Control Function
- **HSS**: Home Subscriber Server

---

## XVII. Latest Technologies

### IoT (Internet of Things)

#### IoT Concept

**Definition**: Sensors and communication in objects connected to Internet
**Evolution**: From M2M and ubiquitous computing to IoT
**Goal**: Information exchange between all objects without human intervention

#### Core IoT Technologies

**Sensing Technology**:
- Various sensors (temperature, humidity, light, gas)
- Smart sensors with processing capability
- Virtual sensing functions

**Communication Technology**:
- **Wired**: Ethernet, PLC
- **Wireless**: WLAN, Bluetooth, ZigBee, 3G/LTE
- **New Technologies**: BLE, Z-Wave

**Services and Interface**:
- Ontology-based semantic web
- Cloud computing for distributed processing
- Open APIs for service access

#### IoT Protocols

**CoAP (Constrained Application Protocol)**:
- Lightweight application layer protocol
- UDP-based, binary encoding
- Designed for resource-constrained devices

**MQTT (Message Queue Telemetry Transport)**:
- Publish-subscribe messaging protocol
- Lightweight for low-speed, high-latency networks
- Broker-based architecture

| Aspect | MQTT | CoAP |
|--------|------|------|
| **Purpose** | M2M protocol | Message protocol |
| **Topology** | N:M type | 1:1 type |
| **Configuration** | Broker + clients | Server + client |
| **Operation** | Publish/subscribe | Request/response |
| **Transport** | TCP | UDP |
| **Standard** | OASIS | IETF CoRE |

### Software-Defined Networks

#### SDN (Software Defined Network)

**Concept**: Separate control plane from data plane for programmable networks
**Benefits**: 
- Network programmability
- Centralized control
- Hardware vendor independence

#### SDN Architecture

**Application Layer**: Network applications and services
**Control Layer**: SDN controller software
**Infrastructure Layer**: Network devices (switches, routers)
**Interface**: OpenFlow protocol between layers

#### OpenFlow Technology

**Components**:
- **Controller**: Issues commands to switches
- **Switch**: Performs data flow operations
- **Protocol**: OpenFlow communication standard

**Operation**: Controller programs flow tables in switches for packet handling

#### NFV (Network Function Virtualization)

**Purpose**: Implement network functions as software on standard hardware
**Benefits**: 
- Reduced CAPEX and OPEX
- Space and power savings
- Faster service deployment

#### NFV Architecture

**VNFs** (Virtual Network Functions): Software implementations of network services
**NFVI** (NFV Infrastructure): Computing, storage, and network resources
**Management & Orchestration**: Resource management and VNF lifecycle

#### SDN vs NFV Comparison

| Aspect | SDN | NFV |
|--------|-----|-----|
| **Objective** | Network programmability | Virtualized network functions |
| **Origin** | Academic/data centers | Telecommunications carriers |
| **Protocol** | OpenFlow-centered | None specific |
| **Organization** | ONF | ETSI NFV Working Group |

**Relationship**: Complementary technologies often used together

---

## Key Concepts Summary

- **Network Layer**: Packet routing, forwarding, and inter-network communication
- **Transport Layer**: End-to-end reliable (TCP) or unreliable (UDP) data delivery
- **Application Layer**: High-level protocols for specific services (HTTP, FTP, SMTP)
- **Quality of Service**: Techniques to guarantee network performance for multimedia
- **VoIP/Multimedia**: Real-time communication over IP networks using SIP/H.323
- **IoT**: Connected devices using lightweight protocols (MQTT, CoAP)
- **SDN/NFV**: Software-defined and virtualized networking technologies
- **IPv4/IPv6**: Internet addressing with transition to larger address space