# Chapter2 MapReduce and the New Software Stack
- Data-mining
    + often called "big-data" analysis
    + need manage immense amount of data quickly.
- The data
    + extremely regular
    + a ample opportunity to exploit **parallelism**.
- A new software stack has evolved.
- Programming systems for parallelism
    + Not from a "super-computer" but a "computing clusters"
        + commodity hardware, including conventional processors, connected by Ethernet cables or switches.
- Software stack
    - file system -- distributed file system
        + much larger than the disk blocks
        + provide data replication --> protect from failures.
    - programming system -- MapReduce
        - enable many most common calculations on large-scale data to be performed on computer clusters efficiently.
        - can tolerant of hardware failures during computations.
        - can be implementated by SQL
        - Greatest cost is communication.
## Distributed File Systems
- Advantages:
    - the power of the parallelism
    - avoid the realiability problems
### Physical Organization of Compute Nodes
- parallel-computing architecture -- **cluster computing**
- Store on racks
    - 8-64 each rack
- Connection:
    - same rack: gigabit Ethernet.
    - among racks: another level of network or **switch**
    - bandwith: interRack > intrarack
- Tree shaped
- Fail:
    - more components, higher frequency 
    - Solution:
        - **Duplicate**: Files must be store redundantly.
        - **Divide**: Computations must be divided into tasks
### Large-Scale FIle-System Organization
- Distributed file system (DFS)
    - Google File System (GFS)
    - Hadoop Distributed File System (HDFS)
        - Open source
        -





note of the class ppt 33/36 chapter2
- User program initiates process on Master and worker nodes
- worker node executes a Maptask or a Reduce Maptask
- Each chunck of input data is processed by Maptask
- Each Maptask creates intermediate files for Reduce task
- Master keeps track of Map & Reduce tasks
- Reduce task executes and writes output to a file.
Master fails ===> restart mapReduce job
Mapworker fails ====> maptask(in-progress, completed)
Reduce worker fails ===> reduce task (in-progress)
