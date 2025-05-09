# Providers, Multi-Region, Multi-Cloud, Variables & Conditions:

> If we remember when we have created an EC2 Instance the other day, what was the first thing that we wrote in the ``main.tf`` file - is the provider like below 

<<
EOF

provider "aws" {
    # Our Configuration
    region = "" etc
}

EOF>>

* But what if I don't mention the provider block and proceed with creating the EC2 Instance logic & executed "terraform init" & let's say it got success & then I executed "terraform apply" so what will happen now?

> If we do like this - How will Terraform understand where it has to create this resource & how to authenticate with that particular cloud provider - all of that information is available through this provider block. 

# Provider:-

> Provider is nothing but a plugin that helps Terraform to understand where it has to create the infrastructure, so it act's as a medium for Terraform to understand where these resources has to be created. Without provider it is not possible.

> Now what if instead of AWS we need to create infrastructure on Azure, GCP etc, where I will understand how to configure this provider - for that we can use the Terraform Registry of different providers. 


# What if we want to setup a Infrastructure in Multi-Region using Terraform:
# How do we setup Terraform to create infrastructure on Multiple Cloud: This is if our Organization using Hybrid Cloud then how will you setup it. 

* Refer to the Terraform-Code Repository:


# Variables:

> Variables are used to parameterize the things, means they can be used as parameters to pass values to our project. In Terraform there are typically 2 Types of variables:-

1. Input Variables: Let's say we want to pass some information to terraform, then it is called as input variables. If we want to parameterize any output in our terraform configuration then we can pass the values using variables. Input variables in Terraform are used to parameterize configurations, making modules reusable and configurable.


2. Output Variables: If we want Terraform to print any value in the output. Output variables in Terraform are used to display resource attributes (values) for e.g Public IP of Server after execution & to pass data between modules.