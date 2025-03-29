{{date}} {{time}}

Tags: [[AWS]] [[Cloud]] [[Serverless]] [[Compute]]

---

# AWS Serverless Computing

Serverless computing is a cloud execution model where AWS manages the infrastructure, allowing developers to focus solely on code.

## Key Characteristics

- No server provisioning or management required
- Automatic scaling based on workload
- Pay-for-value billing (only pay for resources used during code execution)
- Built-in high availability and fault tolerance

## AWS Serverless Services

### AWS Lambda

- Run code without provisioning or managing servers
- Pay only for compute time consumed
- Automatically scales with usage
- Supports multiple programming languages

### Amazon API Gateway

- Create, publish, maintain, and secure APIs
- Connect applications to backend services
- Serverless integration with Lambda

### AWS Step Functions

- Coordinate multiple AWS services into serverless workflows
- Design and run workflows with visual interface
- Automatically trigger and track each step

## Container Services

### Amazon Elastic Container Service (ECS)

- Fully managed container orchestration service
- Run and scale containerized applications
- Uses Docker containers
- Deep integration with other AWS services

### Amazon Elastic Kubernetes Service (EKS)

- Managed Kubernetes service
- Run Kubernetes applications without installing and managing Kubernetes control plane
- Compatible with existing Kubernetes applications

### AWS Fargate

- Serverless compute engine for containers
- Works with both ECS and EKS
- No server provisioning or management
- Pay only for resources required to run containers

## Benefits of Serverless

- Focus on code, not infrastructure
- Reduced operational complexity
- Automatic scaling to match demand
- Optimized costs through pay-per-use model
- Faster time to market for applications

---

# References

- [[AWS Lambda]]
- [[AWS Core Service Categories]]
- [[AWS Container Services]]
