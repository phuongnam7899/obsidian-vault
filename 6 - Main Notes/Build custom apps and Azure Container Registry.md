2025-08-05 20:31

Tags: [[Azure Containers (ACI)]] [[Azure Container Registry (ACR)]]

---

- Clone a repository
- Edit the code as needed
- Create container storage (see [[Azure Container Registry (ACR)]])
- Build the image of project -> push to the ACR
```
az acr build --image [image_name] --registry [registry_name] --file Dockerfile [file_path]
```
- Pull the created image to ACI ()


---
# References