2025-05-22 10:33

Tags: 

---

# Provider Config
```hcl
provider "azurerm" {
  features {}
  subscription_id = "your-subscription-id"
}
```
# Resource Declaration
```
resource "azurerm_resource_group" "example" {
  name     = "example-resources"
  location = "East US"
  tags = {
    environment = "Production"
  }
}
```
# Variables
```
variable "location" {
  type        = string
  default     = "East US"
  description = "Azure region to deploy resources"
}
```
# Data sources
```
data "azurerm_resource_group" "existing" {
  name = "existing-resource-group"
}
```
# Outputs
```
output "resource_group_id" {
  value = azurerm_resource_group.example.id
}
```
# Modules
```
module "network" {
  source              = "./modules/network"
  resource_group_name = azurerm_resource_group.example.name
  location            = var.location
  address_space       = ["10.0.0.0/16"]
}
```
# Conditional expressions
```
resource "azurerm_virtual_machine" "vm" {
  count = var.environment == "production" ? 2 : 1
  # other configuration
}
```

# Local values
```
locals {
  common_tags = {
    Project     = "MyProject"
    Environment = var.environment
  }
}
```

# Backend config
```
terraform {
  backend "azurerm" {
    resource_group_name  = "tfstate"
    storage_account_name = "tfstate1234"
    container_name       = "tfstate"
    key                  = "prod.terraform.tfstate"
  }
}
```


---
# References