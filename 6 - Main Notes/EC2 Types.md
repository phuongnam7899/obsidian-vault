2025-04-16 20:31

Tags: [[AWS EC2]]

---

- (https://aws.amazon.com/ec2/instance-types/)
- Naming convention: m5.2xlarge
  - m: instance class
  - 5: generation (AWS improve the hardware over time)
  - 2xlarge: size (the more, the more CPU and storage)

|                       | Feature                                                                                  | Ideal for                                                                                                                                                                                          |
| --------------------- | ---------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| General purpose ()    | ==balance== compute, memory and networking                                               | ==Broad range== of workload (web server, code repo)                                                                                                                                                |
| Compute optimized (c) | Higher performance ==processor==                                                         | ==High computing application== , ==batch processing== workload, media transcoding, high-performance web server, high perform computing - HPC, scientific modeling, machine learning, gaming server |
| Memory Optimized      | Fast ==performance for memory== intensive work                                           | ==High performance DB==, Distributed we scale cache stores, [[In-memory databases]] optimized for BI, Application perform real-time processing of unstructured data                                |
| Accelerated computing | Use ==hardware accelerator== to expedite data processing                                 | Application ==streaming & graphic work==                                                                                                                                                           |
| Storage Optimized     | ==Low latency== and ==high I/O operation== per second (IOPS) for storage-intensive tasks | ==Distributed file system== and ==data warehouse== application, high frequency of [[online transaction processing (OLTP)]] system, databases, cache for in-mem database (like Redis)               |


---
# References