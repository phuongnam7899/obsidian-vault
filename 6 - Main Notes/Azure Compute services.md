2025-07-07 20:40

Tags: [[Azure Cloud]]

---

- It lies in the heart of a running application in Azure Cloud
	- Is comprehensive collection of on-demand resources
	- Scalable compute resources
	- Empower build, deploy and manage of **applications**
- Example:
	- Azure Virtual Machine
	- Azure App Service
	- Azure Functions
	- Azure Kubernetes Service
	- Azure Container Instance
- Choosing the right service:
	- Application types: web app, APIs, Microservices, Containerized application,
	- Management overhead: 
		- prefer full control of the machine/application? (VM)
		- or managed approach? (App service, function)
	- Scalability needs
- Real world use cases:
	- Scalable e-commerce app:
		- VM or App services for core functionality
		- Integrate Function for handling real-time event like order process
	- Data analytic pipeline
		- VM with GPU support for machine learning tasks
		- Azure HDInsight for big data processing
	- Serverless microservice architecture:
		- Build function for microservices
			- Add product t shopping cart
			- Process payment
			- Send order confirmation
	- Social Media:
		- Functions to process user uploaded file
		- Functions for send notification
		- Perform realtime analytics of user activity


---
# References