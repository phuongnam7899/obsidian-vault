## Availability Zones
- What are AZs: 
	- geographically separated datacenters in a single region
	- built with independent power,  cooling and network infra
- Benefits:
	- Enhanced availability: when an AZ got problem (hardware problem, power loss,...), the others are not affected and  can be used right away
- Use cases:
	- Mission-critical application: you want to make sure the application always on
	- State-sensitive data: you don't want the data is missed
	- Geo-redundancy within region

### Availability Sets
- Avail Set functions as logical grouping of VM within a single datacenter
- How it enhances uptime:
	- Physical separation: VMs are distributed across multiple fault domain (separated physical rack that with different power source and network switch) and update domain (logica group that get updated/rebooted separatedly during maintenance)
	- Reundant infras
	- Automatic VM placement


[[Resources Group]]

[[Azure Resource Manager (ARM)]]

## Availability Zones
- What are AZs: 
	- geographically separated datacenters in a single region
	- built with independent power,  cooling and network infra
- Benefits:
	- Enhanced availability: when an AZ got problem (hardware problem, power loss,...), the others are not affected and  can be used right away
- Use cases:
	- Mission-critical application: you want to make sure the application always on
	- State-sensitive data: you don't want the data is missed
	- Geo-redundancy within region

### Availability Sets
- Avail Set functions as logical grouping of VM within a single datacenter
- How it enhances uptime:
	- Physical separation: VMs are distributed across multiple fault domain (separated physical rack that with different power source and network switch) and update domain (logica group that get updated/rebooted separatedly during maintenance)
	- Reundant infras
	- Automatic VM placement