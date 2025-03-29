{{date}} {{time}}

Tags: [[AWS]] [[Cloud]] [[Serverless]] [[Compute]]

---

# AWS Lambda

- Serverless compute service that runs code without provisioning or managing servers
- Executes code only when needed and scales automatically
- Pay only for the compute time consumed (when code is running)

## Key Features

- No servers to manage or provision
- Continuous scaling based on the number of incoming requests
- Pay-per-use pricing model (only pay for the time your code runs)
- Supports multiple programming languages (Node.js, Python, Java, Go, Ruby, etc.)
- Built-in fault tolerance and high availability

## How Lambda Works

1. Upload your code to Lambda or write it in the console
2. Set up your code to trigger from events (S3 uploads, API calls, etc.)
3. Lambda runs your code only when triggered
4. AWS automatically scales your application by running code in parallel

## Common Use Cases

- Data processing
- Real-time file processing
- Real-time stream processing
- Building serverless backends for web, mobile, IoT, and 3rd party API integrations
- Creating RESTful APIs

## Event Sources

Lambda can be triggered by:

- AWS services (S3, DynamoDB, SNS, CloudWatch, etc.)
- API calls through Amazon API Gateway
- User-defined applications
- AWS SDK calls

## Limitations

- Maximum execution time per request (currently 15 minutes)
- Memory allocation limits
- Deployment package size limits
- Temporary storage constraints

---

# References

- [[AWS Core Service Categories]]
- [[AWS Serverless Computing]]
- [[AWS Container Services]]
