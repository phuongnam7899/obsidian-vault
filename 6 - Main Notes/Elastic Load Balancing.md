{{date}} {{time}}

Tags: [[AWS]] [[Cloud]] [[Networking]] [[Compute]]

---

# Elastic Load Balancing

- Automatically distributes incoming application traffic across multiple targets
- Provides a single point of contact for applications
- Helps ensure high availability and fault tolerance

## Key Features

- Automatically scales as traffic to your application changes over time
- Can distribute traffic across multiple Availability Zones
- Performs health checks on targets and only routes traffic to healthy instances
- Integrates seamlessly with EC2 Auto Scaling

## How It Works

- Sits between client devices and backend servers (EC2 instances, containers, etc.)
- Receives requests from clients and distributes them across targets
- Can be public-facing for client traffic or internal for backend communication

## Benefits

- Improves application availability and fault tolerance
- Prevents overloading of individual resources
- Provides high throughput and low latency
- Adapts to changes in traffic patterns
- Allows resources to be added or removed without disrupting application flow

## Integration with Auto Scaling

When used with EC2 Auto Scaling:

- New instances are automatically registered with the load balancer
- Instances are evenly distributed across Availability Zones
- Traffic is only sent to healthy instances

---

# References

- [[Amazon EC2]]
- [[EC2 Auto Scaling]]
- [[AWS Core Service Categories]]
