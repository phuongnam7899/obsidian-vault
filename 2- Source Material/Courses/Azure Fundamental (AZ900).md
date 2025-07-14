# Module 1: Cloud Concepts

## The need of cloud computing
- For an application to run, we need:
	- ==Compute==: Things that do the calculation (CPU, RAM)
	- ==Storage==: Place to store file / raw data
	- ==Database==: A place to save structured data
	- ==Network==: To connect difference devices
	- ==Server Sprawl==: Manage/Maintain the multi servers when application scale (Heat, depreciation,...)
- Cloud computing give unlimited compute, storage and resources without pre-buy anything
- -> Give business agility, scalability and adaptability
- -> Startup could compete with giants

[[Definition of cloud computing]]

## Evolution of cloud model 

### History
- 1960 - Time Sharing: Enable multiple users to access a central computer -> maximize efficiency
- 1990 - Data Exchange: Internet is the main vehicle of data exchange
- 2000's - Internet bandwidth improved: companies see the potential of online services
- 2006: AWS launch - Introduced storage via S3

### Models
- Level 1: Infrastructure as a Service (IaaS)
	- Offer ==foundation element of computing== on demand: Server, Storage & Networking
	- Power to scale/shrink resources
	- Example: 
		- AWS EC2 (nothing but a VM)
		- Google Compute Engine (GCE) - provide computing solution
> [!s] IaaS is like renting the IT infras, not buying them

- Level 2: Platform as a Service (PaaS)
	- Provide ==development environment== to create, run and manage -> Accelerate app development
		- It include ways to build, deploy and manage the application
		- Example:
			- Microsoft Azure App Service: provide tools to create web/mobile application
			- Heroku
- Level 3: Software as a Service (SaaS)
	- ==Deliver the whole app== over internet (without caring about the development and infras) like Google Workspace, Saleforce,...

- The higher level is to doing Hybrid and Multi-cloud: combine on-premise and cloud services from different providers

- Future: 
	- Serverless computing
	- Edge computing
	- Integration of AI and ML

## Who is responsible for the data in the cloud
### IaaS
- Cloud Providers are responsible for protection the infrastructure that run the services
	- Hardware
	- Software
	- Networking
	- Facilities
- Cloud users are responsible for:
	- Guest operating system
	- Any application
	- Data stored in the cloud
	- Patch the OS
	- Encryption and security
	- Network traffic protect

### PaaS
- Cloud provider extends the responsibility to complete platform and solution stack
	- Example: Azure SQL Database: Microsoft manage: physical servers, network, the data storage, OS
- Cloud user:
	- Application security
	- Data management and security (data access control)
	- User access management

### SaaS
- More responsibility shifted to provider
	- Infras
	- Middware
	- Application
	- Update
- Cloud user:
	- Define roles and permissions
	- Data encrypt and privacy
	- Compliance management

[[Key characteristic of Cloud computing]]

[[Benefits of Cloud Computing]]

[[CapEx vs OpEx]]

## The global network powering the cloud
- ==Data centers are the pillars== of cloud
- The data centers are ==distributed around the world==
- Data centers ==should approximate users== -> low latency
- They should ==access to renewable energy==

[[Public, Private and Hybrid Cloud]]

[[Infras as a Code (IaC)]]

## Serverless
- When open a lemonade stand:
	- Buy/rent a stand -> pay event when it closed
	- Stock-up supply
	- Be there all the time to sell

 - Serverless approach:
	 - ==Pay only when someone buy== (code execution), not the idle time
	 - ==Someone else setup the stand== for you -> you focus on make better lemonade (application code)

## Microservice
- Analogy: a food court -> you can choose each dish in different stalls
- In technology: break large application into smaller services, each do a specific things -> all work together to do the job
- Challenges:
	- Managing a team of specialist and microservices is hard
	- Communication is key -> microservices must communicate seamlessly for application to work well
	- Require a solid foundation of infra and tools to manage
- Microservice tech explain:
	- Each stall in food court = 1 ==microservice==
	- The first stall will be ==authentication== -> to prove who you are in the system
	- Each stall should have its own storage to store ingregients -> ==database==
	- ==API==: allow microservices to commnicate with each other#
# Module 2: Core Azure Services

[[Azure regions]]

[[Azure Availability Zones]]

[[Resources Group]]

[[Azure Resource Manager (ARM)]]

## Azure core services and products
### [[Azure Compute services]]
- Azure Virtual Machine
- VM Scale set
- Azure App Services
- Azure Functions
- Azure Container Services

### Network connectivity
- Virtual Networks
- Load Balancer
- VPN Gateway
- Application Gateway
- Content Delivery Network

### Others
- Azure Storage
- Database services
	- NoSQL
	- Relational DB
- Azure Marketplace
- IoT
- Data mining technologies
	- Azure SQL Data Warehouse
	- Azure HD Insight
	- Azure Data lake analysis
- AI:
	- Machine learning services
	- Machine learning studio
- Serverless Computing
- DevOps
- Command Cloud Resource
- 
# Module 3: Security, Privacy, Compliance & Trust
# Module 4: Azure pricing and support
