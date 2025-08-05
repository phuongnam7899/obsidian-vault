### Availability Sets
- Avail Set functions as logical grouping of VM within a single datacenter
- How it enhances uptime:
	- Physical separation: VMs are distributed across multiple fault domain (separated physical rack that with different power source and network switch) and update domain (logica group that get updated/rebooted separatedly during maintenance)
	- Reundant infras
	- Automatic VM placement