2025-04-06 09:34

Tags: [[AWS EC2]]

---

>[!i] Idea: Fleets allow us to auto request for Spot Instance

- Spot Fleets = set of [[EC2 Spot Instances]] + On-demand instance
- Fleet will try to meet target capacity within price constrains:
	- Define possible launch pools (instance type, OS, AZ) (Can have multiple pool for Fleet to choose)
	- Fleet stop launch when cost > max cost you define
- Strategies to allocate:
	- lowestPrice: from the lowest price pool (cost optimized, short workload)
	- diversified: distributed to all pools (good availability, long workload)
	- capacityOptimized: pool with optimal capacity for number of instance
	- priceCapacityOptimized (recommended): highest capacity available, then lowest price

---
# References