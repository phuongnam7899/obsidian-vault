2025-04-06 08:31

Tags: [[AWS EC2]] [[Finance]]

---

- On demand:
  - No upfront cost / minimum contract
  - Ideal for short term, irregular workload
- [[EC2 Spot Instances]]
- Reserved:
  - Require 1-year or 3-year term commitment
  - Cheaper than on-demand
  - Can buy/sell in Reserved Instance Marketplace
- Computed saving plan:
  - 1 or 3 year commitment
  - Cheaper than on-demand for consistent computing
  - Commit to a certain type of usage (X per hour for 1-3 years)
  - Locked into specify instance family and region
  - Flexible across:
	  - Instance Size
	  - OS
	  - Tenancy (Host, Dedicated, Default)
- [[Dedicated computing in AWS]] 

# Quick compare (Non-dedicated)

| Purchase Option | Relative Cost | Flexibility | Commitment Required |
| --------------- | ------------- | ----------- | ------------------- |
| On Demand       | 💰💰💰💰💰    | ⭐⭐⭐⭐⭐       | None                |
| Spot            | 💰            | ⭐⭐          | None                |
| Reserved        | 💰💰          | ⭐⭐⭐         | 1-3 years           |
| Compute Savings | 💰💰💰        | ⭐⭐⭐⭐        | 1-3 years           |
Example:
![[Pasted image 20250406090526.png]]
# How to choose
- On demand: Like you go traveling, then rent a homestay for any time you like, pay full price
- Reserved: Like you rent an apartment for long time -> got discount
- Saving Plan: Pay a certain amount per hour for certain period and stay in any room type and change the room type if want
- Spot: Rooms with very low price, but you can be kicked any time if someone pay more than you
- Dedicated host: you book an entire building
- Capacity reservation: you book a room for a period and pay even if you don't use it

---
# References
- [[Spot Fleets]]