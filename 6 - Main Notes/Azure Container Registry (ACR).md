2025-07-27 20:59

Tags: [[Azure Cloud]] 

---

- Is a service of Azure to manage the image that could be used for the [[Azure Containers (ACI)]]

# Fields when create
- Project details
	- Subscription
	- [[Resources Group]]
- Instance details
	- Name
	- Location
	- Admin User
	- [[SKU]]
- Encryption (Only available in premium SKU)
- Tags

# CLI Commands
- Build the image of project -> push to the ACR
```
az acr build --image [image_name] --registry [registry_name] --file Dockerfile [file_path]
```


---
# References