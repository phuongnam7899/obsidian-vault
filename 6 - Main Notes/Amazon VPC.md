{{date}} {{time}}

Tags: #AWS #Cloud #Networking

---

- Amazon VPC (Virtual Private Cloud) enables you to launch AWS resources in a logically isolated virtual network
- Similar to running a traditional network in your own data center, but with the scalability of AWS

## Key Components

### Subnets

- Segments of IP address ranges within a VPC
- Allow you to group resources based on security or operational needs
- Can be public (accessible from the internet) or private (internal only)

### Internet Gateway

- Connects the VPC's public subnets to the internet
- Provides a target in VPC route tables for internet-routable traffic
- Performs network address translation (NAT) for instances with public IP addresses

### Virtual Private Gateway

- Connects VPC's private subnets to an on-premises network through VPN or Direct Connect
- Enables secure communication between AWS and on-premises networks
- Routes traffic between VPC and on-premises resources

### AWS Direct Connect

- Dedicated private connection from an on-premises network to AWS
- Provides more consistent network performance than internet-based connections
- Reduces bandwidth costs for high-volume workloads

## Security Controls

### Network Access Control Lists (ACLs)

- Acts as a firewall for controlling traffic at the subnet level
- Stateless packet filtering (return traffic must be explicitly allowed)
- Default network ACL allows all inbound and outbound traffic
- Custom network ACLs deny all inbound and outbound traffic by default

### Security Groups

- Acts as a virtual firewall for EC2 instances or other resources
- Controls inbound and outbound traffic at the instance level
- Stateful packet filtering (return traffic is automatically allowed)
- By default, denies all inbound traffic and allows all outbound traffic

---

# References

- [[AWS Regions and Availability Zones]]
- [[Amazon Route 53]]
