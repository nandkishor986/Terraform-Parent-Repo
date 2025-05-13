# Providers 

* A provider in Terraform is a plugin that enables interaction with an API. This includes cloud providers, SaaS providers, and other APIs. The providers are specified in the Terraform configuration code. They tell Terraform which services it needs to interact with. For example, if we want to use Terraform to create a virtual machine on AWS, we would need to use the AWS provider. The AWS provider provides a set of resources that Terraform can use to create, manage, and destroy virtual machines on AWS.

> Here is an example of how to use the AWS provider in a Terraform configuration:

provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "web-server" {
  ami = "ami-0123456789abcdef0" # Change the AMI 
  instance_type = "t2.micro"
}


* In this example, we are first defining the AWS provider. Then we are specifying the region as ``us-east-1``. Then, we are defining the `aws_instance` resource and at last we are specifying the `AMI ID` and the `instance type`.

> When Terraform runs, it will first install the AWS provider. Then, it will use the AWS provider to create the virtual machine.

Here are some other examples of providers:

- `azurerm` - for Azure
- `google` - for Google Cloud Platform
- `kubernetes` - for Kubernetes
- `openstack` - for OpenStack
- `vsphere` - for VMware vSphere

> There are many other providers available & new ones are being added all the time. Providers are an essential part of Terraform. They allow Terraform to interact with a wide variety of cloud providers & other APIs. This makes Terraform a very versatile tool that can be used to manage a wide variety of infrastructure.


## Different ways to configure providers in Terraform:

> There are three main ways to configure providers in Terraform:

1. In the root module 

* This is the most common way to configure providers. The provider configuration block is placed in the root module of the Terraform configuration. This makes the provider configuration available to all the resources in the configuration.

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami = "ami-0123456789abcdef0"
  instance_type = "t2.micro"
}
```

2. In a child module

* We can also configure providers in a child module. This is useful if we want to reuse the same provider configuration in multiple resources.

```hcl
module "aws_vpc" {
  source = "./aws_vpc"
  providers = {
    aws = aws.us-west-2
  }
}

resource "aws_instance" "webserver" {
  ami = "ami-0123456789abcdef0"
  instance_type = "t2.micro"
  depends_on = [module.aws_vpc]
}
```

### In the required_providers block

* We can also configure providers in the ``required_providers`` block. This is useful if we want to make sure that a specific provider version is used.

```hcl
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "~> 3.79"
    }
  }
}

resource "aws_instance" "webserver" {
  ami = "ami-0123456789abcdef0"
  instance_type = "t2.micro"
}
```

* The best way to configure providers depends on our specific needs. If we are only using a single provider, then configuring it in the root module is the simplest option. If we are using multiple providers, or if we want to reuse the same provider configuration in multiple resources, then configuring it in a child module is a good option. And if we want to make sure that a specific provider version is used, then configuring it in the ``required_providers`` block is the best option.
