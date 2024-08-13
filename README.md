# Custom MapReduce Reports
Reports describing custom implementation of distributed grep, gossip membership protocol, HDFS, and MapReduce in Go. The fi

## Disclaimer and Context
This project was done as part of CS 425 (Distributed Systems) at UIUC in Fall 2023. As such, I cannot make the code public, but I have attached the reports from each stage of the project process (distributed grep, gossip membership protocol, HDFS, and MapReduce). This project was done in collaboration with Vraj Patel, another student.

## Overview
The entire project was written in Go, and the functionality was tested using a distributed network of 10 VMs. The four main parts of the project were:
 1. Create a distributed grep program that could grep files across all VMs in a network
 2. Implement the gossip protocol (with and without suspicion) to be used as a live membership protocol for the network of VMs
     - This would be used in later stages for all machines to detect who was present in the network, who had failed, and who had left/rejoined
 3. Implement a distributed file system (much like HDFS) to service reads and writes. The system had to:
     - Use our gossip membership protocol implementation from the previous part
     - Have fault tolerance via data replication
     - Implement read/write locks while avoiding starvation
     - Implement leader election in case the current leader machine failed, and support joining back into the network
 5. Implement MapReduce (named MapleJuice in the report) to perform user-specified computations in parallel on data in the DFS. The system had to:
     - Use our HDFS implementation from the previous part
     - Support any user-defined Map or Reduce jobs via an executable
     - Support user-specified filenames, hash partitioning, and range partitioning for job allocation
     - Implement SQL filter and join using only our implementation of Map and Reduce
