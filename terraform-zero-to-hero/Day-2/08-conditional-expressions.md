# Conditional Expressions:

> Conditional expressions in Terraform are used to define conditional logic within configurations. They allow us to make decisions or set values based on conditions. Conditional expressions are typically used to control whether resources are created or configured based on the evaluation of a condition.

* The syntax for a conditional expression in Terraform is:

-> ``condition ? true_val : false_val``


* condition is an expression that evaluates to either true or false.

* true_val is the value that is returned if the condition is true.

* false_val is the value that is returned if the condition is false.


* Here are some common use cases and examples of how we can use conditional expressions in Terraform:

1. Conditional Resource Creation Example

resource "aws_instance" "example" {
  count = var.create_instance ? 1 : 0

  ami           = "ami-XXXXXXXXXXXXXXXXX"
  instance_type = "t2.micro"
}

* In this example, the count attribute of the aws_instance resource uses a conditional expression. If the create_instance variable is true, we create one EC2 instance. If create_instance is false, we create zero instances, effectively skipping resource creation.


2. Conditional Variable Assignment Example

variable "environment" {
  description = "Environment type"
  type        = string
  default     = "development"
}

variable "production_subnet_cidr" {
  description = "CIDR block for production subnet"
  type        = string
  default     = "10.0.1.0/24"
}

variable "development_subnet_cidr" {
  description = "CIDR block for development subnet"
  type        = string
  default     = "10.0.2.0/24"
}

resource "aws_security_group" "example" {
  name        = "example-sg"
  description = "Example security group"

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = var.environment == "production" ? [var.production_subnet_cidr] : [var.development_subnet_cidr]
  }
}

* In this example, the cidr_blocks value in the aws_security_group resource uses a conditional expression to choose between the production and development subnet CIDRs based on the environment variable. If the environment is set to "production", we use the production_subnet_cidr variable; otherwise, we use the development_subnet_cidr variable.


3. Conditional Resource Configuration

resource "aws_security_group" "example" {
  name = "example-sg"
  description = "Example security group"

  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = var.enable_ssh ? ["0.0.0.0/0"] : []
  }
}

* In this example, the ingress block within the aws_security_group resource uses a conditional expression to control whether SSH access is allowed. If enable_ssh is true, we allow SSH traffic from any source ("0.0.0.0/0"); otherwise, we allow no inbound traffic.

* Conditional expressions in Terraform provide a powerful way for us to make decisions and customize our infrastructure deployments based on various conditions and variables. They enhance the flexibility and reusability of our Terraform configurations.