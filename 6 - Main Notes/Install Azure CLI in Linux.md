2025-05-28 17:43

Tags: [[Azure]] [[Linux]]

---

# Redhat Linux 

```
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
```

```
# Create the repository file
sudo tee /etc/yum.repos.d/azure-cli.repo > /dev/null <<EOF
[azure-cli]
name=Azure CLI
baseurl=https://packages.microsoft.com/yumrepos/azure-cli
enabled=1
gpgcheck=1
gpgkey=https://packages.microsoft.com/keys/microsoft.asc
EOF
```

```
sudo dnf install azure-cli
```

---
# References