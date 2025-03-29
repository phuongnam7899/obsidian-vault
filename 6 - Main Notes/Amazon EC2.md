{{date}} {{time}}

Tags: #AWS #Cloud #Compute

---

- EC2 (Elastic Cloud Compute) is a core AWS service that provides virtual machines
- Key features:
  - Secure and sizable compute capacity
  - Boot server instances in minutes
  - Pay-for-use pricing model

## EC2 Instance Types

- **General purpose**: Balance of compute, memory, and networking (ideal for broad range of workloads)
- **Compute optimized**: Higher performance processors (ideal for high computing applications and batch processing)
- **Memory optimized**: Fast performance for memory-intensive workloads (ideal for high-performance databases)
- **Accelerated computing**: Uses hardware accelerators to expedite data processing (ideal for streaming and graphic work)
- **Storage optimized**: Low latency and high I/O operations per second (ideal for distributed file systems and data warehouses)

## EC2 Pricing Models

- **On-demand**:
  - No upfront cost or minimum contract
  - Ideal for short-term, irregular workloads
- **Spot**:
  - Uses spare AWS capacity that can be reclaimed
  - Up to 90% cheaper than on-demand
  - Ideal for flexible start/end times and workloads that can withstand interruption
- **Reserved**:
  - Requires 1-year or 3-year commitment
  - Cheaper than on-demand
- **Compute Savings Plans**:
  - 1 or 3 year commitment
  - Cheaper than on-demand for consistent computing needs

## Dedicated Computing Options

- **Dedicated Instances**:
  - Non-shared infrastructure but AWS manages placement
  - Higher price than standard instances
- **Dedicated Hosts**:
  - Complete physical server isolation
  - Full control over server
  - Most expensive option

---

# References

- [[AWS Core Service Categories]]
- [[EC2 Auto Scaling]]
- [[Elastic Load Balancing]]
- [[Server-less Computing]]
