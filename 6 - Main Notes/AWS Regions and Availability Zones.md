{{date}} {{time}}

Tags: #AWS #Cloud #Infrastructure

---

- AWS divides its global infrastructure into Regions and Availability Zones
- This architecture ensures high availability, fault tolerance, and low latency

## AWS Regions

- Geographic areas that host AWS resources
- Each Region is completely isolated from other Regions
- Factors for selecting a Region:
  - Legal and compliance requirements (e.g., GDPR)
  - Proximity to customers (to reduce latency)
  - Available services (newer Regions may not support all services)
  - Pricing (varies by Region)

## Availability Zones (AZs)

- One or more discrete data centers with redundant power, networking, and connectivity
- Physically separated within a Region but connected via low-latency links
- Designed for fault isolation while enabling cross-zone redundancy
- Each Region has multiple AZs (typically 3+)
- AZs allow customers to operate highly available applications

## Edge Locations

- Content delivery network (CloudFront) endpoints
- Located in many more cities than Regions
- Cache copies of content for faster delivery to users worldwide
- Reduces latency by serving content from locations closer to users

## AWS Outposts

- Extends AWS infrastructure to on-premises data centers
- Provides consistent hybrid experience using the same APIs and tools
- Enables low-latency access to on-premises systems

---

# References

- [[What is cloud computing]]
- [[Amazon VPC]]
