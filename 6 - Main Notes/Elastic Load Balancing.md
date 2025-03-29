{{date}} {{time}}

Tags: #AWS #Cloud #Compute

---

- Elastic Load Balancing (ELB) automatically distributes incoming traffic across multiple resources
- Key features:
  - Automatically scales to handle varying levels of traffic
  - Provides a single point of contact for auto-scale groups
  - Detects unhealthy instances and reroutes traffic to healthy instances

## Types of Load Balancers

- **Application Load Balancer**: Routes traffic based on application-level content (HTTP/HTTPS)
- **Network Load Balancer**: Routes traffic based on network/transport protocols (TCP/UDP/TLS)
- **Gateway Load Balancer**: Routes traffic for virtual appliances like firewalls and intrusion detection systems
- **Classic Load Balancer**: Legacy load balancer for basic load balancing across EC2 instances

## Benefits

- Increases application availability and fault tolerance
- Provides seamless scaling of resources
- Enhances security with integrated certificate management
- Improves user experience by ensuring consistent performance

---

# References

- [[Amazon EC2]]
- [[EC2 Auto Scaling]]
