2025-07-28 13:57

Tags: 

---

# Pre-built image
- Create container

```sh
az container create --name [container_name] --image microsoft/aci-helloworld --ip-address public -g [resource_group_name]
```

- List down all containers:
```sh
az container list -g [resource_group_name]
```

> [!i] Can change the output format to table by adding `-o table` at the end


# Custom image
- 

- az ad signed-in-user show
- az login
- az storage blob list --account-name fleetprodseadiagstrg --container-name code --auth-mode login --output table
- az storage blob list --account-name fleetprodseadiagstrg --container-name code --output table
- az storage account keys list --account-name fleetprodseadiagstrg --query "[0].value" -o tsv


---
# References