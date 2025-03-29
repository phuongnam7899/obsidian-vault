{{date}} {{time}}

Tags: [[AWS]] [[Cloud]] [[Compute]]

---

# EC2 Auto Scaling

- Automatically adjusts the number of EC2 instances in response to changing demand
- Helps maintain application availability and allows scaling up or down as computing requirements change
- Eliminates need to manually provision capacity based on predicted traffic

## Auto Scaling Methods

### Dynamic Scaling

- Responds to changing demand
- Adds or removes EC2 instances based on real-time metrics like CPU utilization
- Useful for workloads with unpredictable patterns

### Predictive Scaling

- Automatically schedules the right number of EC2 instances based on predicted demand
- Uses machine learning to analyze historical workload patterns
- Best for workloads with regular, predictable traffic patterns (daily, weekly)

## Benefits

- Improved fault tolerance - automatically replaces unhealthy instances
- Better application availability - ensures you have the right capacity to meet demand
- Cost optimization - only run the instances you need, when you need them
- Automatic resource management - reduces manual monitoring and scaling actions

## How It Works

1. Define minimum, maximum, and desired capacity for your Auto Scaling group
2. Set up scaling policies based on metrics (like CPU usage)
3. Auto Scaling monitors your applications and automatically adjusts capacity

---

# References

- [[Amazon EC2]]
- [[Elastic Load Balancing]]
- [[AWS Core Service Categories]]
