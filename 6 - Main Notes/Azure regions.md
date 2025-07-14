## Azure regions
- Azure consits of data centers
- Data centers are organized into regions
- Each region has at least 1 data center
- Data centers in same religion are networked together -> low latency

### Special regions
- Azure government: 
	- designed for US government agencies and their partners
	- Strict compliance regulation and residency requirements 
- Azure China cloud
	- Operated by Chinese consortium
	- Follow China sovereignty laws
- Azure German cloud
	- Operated by german subsidiary of Microsoft
	- Follow German data privacy regulation

> [!i] Key consideration
> - ==Data residency==: ensure data stay inside a specific geographic region
> - ==Compliance==: help comply with industry or regulatory requirements
> - ==Sovereignty== concern: Stick with data law in certain religion
> - ==Not all services are available== in special regions
> - Special regions may have ==higher latency==
> - More ==complexity management== 

### Regions pairs
- Offer robust mechanism to protect data and application agaisnt disaster
- In each region, there're regional pairs:
	- are 2 separated data center
	- at least 300 miles far -> avoid single disaster
- Benefit:
	- Increase resilience
	- Improve business continuty -> reduce downtime
	- Enhance data protection
- How it work:
	- Automatically failover
	- Automatically data replication

## Azure regions
- Azure consits of data centers
- Data centers are organized into regions
- Each region has at least 1 data center
- Data centers in same religion are networked together -> low latency

### Special regions
- Azure government: 
	- designed for US government agencies and their partners
	- Strict compliance regulation and residency requirements 
- Azure China cloud
	- Operated by Chinese consortium
	- Follow China sovereignty laws
- Azure German cloud
	- Operated by german subsidiary of Microsoft
	- Follow German data privacy regulation

> [!i] Key consideration
> - ==Data residency==: ensure data stay inside a specific geographic region
> - ==Compliance==: help comply with industry or regulatory requirements
> - ==Sovereignty== concern: Stick with data law in certain religion
> - ==Not all services are available== in special regions
> - Special regions may have ==higher latency==
> - More ==complexity management== 

### Regions pairs
- Offer robust mechanism to protect data and application agaisnt disaster
- In each region, there're regional pairs:
	- are 2 separated data center
	- at least 300 miles far -> avoid single disaster
- Benefit:
	- Increase resilience
	- Improve business continuty -> reduce downtime
	- Enhance data protection
- How it work:
	- Automatically failover
	- Automatically data replication

### Feature availability in region
- Finding information in Azure Portal -> Regional availability
- Search for "Azure products by regions"

> [!s] Best practices for choosing region
> - Latency: the nearer, the faster
> - Feature needs: is the service you need available in the region?
> - Compliance requirement: choose regions that aligns with regulation
