# Multiple Providers

* We can use multiple providers in one single terraform project. For example,


1. Create a ``providers.tf`` file in the root directory of our Terraform project.
2. In the ``providers.tf`` file, define the AWS & Google providers. For example:


```
provider "aws" {
  region = "us-east-1"
}

provider "google" {
  credentials = file()
  region = "asia-south1"
  project = "project_id"
}
```

3. In our other Terraform configuration files, we can then use the AWs & Google providers to create resources in AWS and Google, respectively,

```
resource "aws_instance" "webserver" {
  ami = "ami-0123456789abcdef0"
  instance_type = "t2.micro"
}

resource "google_compute_instance" "devserver" {
  name = "devserver"
  zone = "asia-south1-a"
  machine_type = "e2-micro"
}
```

