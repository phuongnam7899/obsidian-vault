{{date}} {{time}}

Tags: [[AWS]] [[Cloud]] [[Serverless]] [[Compute]]

---

# AWS Serverless Computing

Serverless computing allows you to build and run applications without managing servers, focusing solely on your code.

## Key AWS Serverless Services

### AWS Lambda

- Run code without provisioning or managing servers
- Pay only for compute time consumed
- Code executes in response to events
- Scales automatically based on workload
- Supports multiple programming languages

### Container Orchestration Services

- **Amazon Elastic Container Service (ECS)**:

  - Run and scale containerized applications
  - Control Docker-enabled applications via simple API calls
  - Integrates with AWS tools and services

- **Amazon Elastic Kubernetes Service (EKS)**:
  - Run and scale Kubernetes applications
  - Managed Kubernetes control plane
  - Compatible with standard Kubernetes tools

### AWS Fargate

- Serverless compute engine for containers
- Works with both ECS and EKS
- No server management required
- Pay only for resources required by your containers
- Allocates compute resources on-demand

Serverless computing eliminates infrastructure management while allowing developers to focus on code and business logic.

---

# References

[[Amazon EC2]]
[[AWS Core Service Categories]]
