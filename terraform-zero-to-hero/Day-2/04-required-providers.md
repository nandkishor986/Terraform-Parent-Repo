# Provider Configuration

> The ``required_providers`` block in Terraform is used to declare & specify the required provider configurations for our Terraform module or configuration. It allows us to specify the provider name, source & version constraints.

```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 3.0"
    }
    azurerm = {
      source  = "hashicorp/azurerm"
      version = ">= 2.0, < 3.0"
    }
  }
}
```