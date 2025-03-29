{{date}} {{time}}

Tags: #AWS #Cloud #Compute #Serverless

---

- Serverless computing is a cloud computing model where the cloud provider manages the infrastructure
- Developers focus only on code, not server management or capacity planning
- Applications scale automatically and you pay only for the resources consumed

## AWS Serverless Services

### AWS Lambda

- Run code without provisioning or managing servers
- Key features:
  - Pay only for compute time consumed when code is running
  - Automatically scales from a few requests per day to thousands per second
  - Supports multiple programming languages (Node.js, Python, Java, Go, etc.)
  - Can trigger code execution using other AWS services

### Container Orchestration Services

- **AWS Elastic Container Service (ECS)**:

  - Run and scale containerized applications
  - Use simple API calls to control Docker-enabled applications
  - Integrates with other AWS services

- **AWS Elastic Kubernetes Service (EKS)**:
  - Run and scale Kubernetes applications
  - Fully managed Kubernetes control plane
  - Certified Kubernetes conformant

### AWS Fargate

- Serverless compute engine for containers
- Works with both ECS and EKS
- Key features:
  - Pay only for resources used by containers
  - No need to provision or manage servers
  - Each workload runs in its own isolated environment

## Benefits of Serverless Computing

- No server management needed
- Flexible scaling
- Pay for value
- Increased development speed
- Reduced operational complexity

---

# References

- [[Amazon EC2]]
- [[AWS Messaging Services]]
