# Overview of steps

* Create a directory for our Terraform project & create a Terraform configuration file (usually named `main.tf`) in that directory. In this file, we define the AWS provider & resources we want to create. Here's a basic example:

```hcl
   provider "aws" {
     region = "us-east-1"  # Set our desired AWS region
   }

   resource "aws_instance" "example" {
     ami           = "ami-0c55b159cbfafe1f0"  # Specify an appropriate AMI ID
     instance_type = "t2.micro"
   }
```

## Initialize Terraform**

* In our terminal, navigate to the directory containing our Terraform configuration files & run:

```
terraform init
```

- This command initializes the Terraform working directory, downloading any necessary provider plugins.


## Apply the Configuration

* Run the following command to create the AWS resources defined in our Terraform configuration:

```
terraform apply
```

- Terraform Apply will display a plan of the changes it's going to make. Review the plan & type "yes" when prompted to apply it.

## Verify Resources

> After Terraform completes the provisioning process, we can verify the resources created in the AWS Management Console or by using AWS CLI commands.

## Destroy Resources

If we want to remove the resources created by Terraform, we can use the following command:

```
terraform destroy
```

# Note:- 

* Be cautious when using `terraform destroy` as it will delete resources as specified in our Terraform configuration.