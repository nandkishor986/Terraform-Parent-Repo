# Infrastructure as Code(IaC): 

* Before the adventages of Infrastructure as Code, infrastructure management was typically a manual & time-consuming process. System administrators & operations teams had to:

1. Manually Configure Servers: Servers & other infrastructure components were often set up & configured manually, which could lead to inconsistencies & errors.

2. Lack of Version Control: Infrastructure configurations were not typically version-controlled, making it difficult to track changes or revert to previous states.

3. Documentation Heavy: Organizations relied heavily on documentation to record the steps & configurations required for different infrastructure setups. This documentation could become outdated quickly.

4. Limited Automation: Automation was limited to basic scripting, often lacking the robustness & flexibility offered by modern IaC tools.

5. Slow Provisioning: Provisioning new resources or environments was a time-consuming process that involved multiple manual steps, leading to delays in project delivery.

* IaC addresses these challenges by providing a systematic, automated & code-driven approach to infrastructure management. Popular IaC tools include Terraform, AWS CloudFormation, Azure Resource Manager templates others. 

* These tools enable organizations to define, deploy & manage their infrastructure efficiently & consistently, making it easier to adapt to the dynamic needs of modern applications and services.


# Why to use Terraform ?

* There are multiple reasons why Terraform is used over the other IaC tools but below are the main reasons.

1. **Multi-Cloud Support**: Terraform is known for its multi-cloud support. It allows us to define infrastructure in a cloud-agnostic way, meaning we can use the same configuration code to provision resources on various cloud providers (AWS, Azure, Google Cloud, etc.) and even on-premises infrastructure. This flexibility can be beneficial if our organization uses multiple cloud providers or plans to migrate between them.

2. **Large Ecosystem**: Terraform has a vast ecosystem of providers & modules contributed by both HashiCorp (the company behind Terraform) and the community. This means we can find pre-built modules and configurations for a wide range of services & infrastructure components, saving our time and effort in writing custom configurations.

3. **Declarative Syntax**: Terraform uses a declarative syntax, allowing us to specify the desired end-state of our infrastructure. This makes it easier to understand & maintain our code compared to imperative scripting languages.

4. **State Management**: Terraform maintains a state file that tracks the current state of our infrastructure. This state file helps Terraform understand the differences between the desired & actual states of our infrastructure, enabling it to make informed decisions when we apply the changes.

5. **Plan and Apply**: Terraform's "plan" and "apply" workflow allows us to preview changes before applying them. This helps prevent unexpected modifications to our infrastructure & provides an opportunity to review & approve changes before they are implemented.

6. **Community Support**: Terraform has a large & active user community, which means we can find answers to common questions, troubleshooting tips, and a wealth of documentation & tutorials online.

7. **Integration with Other Tools**: Terraform can be integrated with other DevOps and automation tools, such as Docker, Kubernetes, Ansible, and Jenkins, allowing us to create comprehensive automation pipelines.

8. **HCL Language**: Terraform uses HashiCorp Configuration Language (HCL), which is designed specifically for defining infrastructure. It's human-readable & expressive, making it easier for both developers & operators to work with.



* Let’s imagine I’m working as a DevOps Engineer & I receive a very basic task: to create an S3 bucket on the AWS platform.

> The simplest way to do this would be to:

1. Log in to the AWS Console using my username and password.

2. Search for the S3 service.

3. Click on “Create Bucket” & provide several details like:

- The bucket name,

- Whether to enable or disable public access,

- Whether versioning should be turned on, etc.

> Once all details are filled in, I click “Create”, and the bucket is ready in just a couple of minutes.

~ Easy enough, right?

* But now, let’s say I receive the same kind of request from hundreds of different teams. Manually repeating this task each time would consume a lot of time & reduce my overall productivity. Clearly, we need a better way.


# The Need for Automation

> To avoid repetitive manual tasks, the ideal approach is to automate infrastructure provisioning. AWS offers ways to interact with its services programmatically, through tools like:

1. AWS CLI, and

2. AWS SDKs or APIs (using languages like Python or Shell).

* With a basic understanding of Python or Shell scripting, I can write a script that interacts with AWS APIs. Instead of logging in manually each time, I run this script once to create the S3 bucket — whether it's 1 or 1000 buckets, the effort remains the same. I can simply share the script with teams or run it on their behalf, saving time and effort.

* However, even simple tasks like this need some level of scripting knowledge. The complexity increases if the request involves something like:

> Creating a VPC,

> Configuring its subnets and routing,

> Launching an EC2 instance with high availability,

> Setting up an S3 endpoint for that VPC.

* All of this requires not only good scripting skills but also a deep understanding of networking and AWS resources.

# CloudFormation to the Rescue

> To bridge this skill gap, AWS introduced CloudFormation Templates (CFTs). These allow DevOps engineers to define infrastructure as code using a simple templating language — either JSON or YAML.

> These templates abstract away the scripting complexity and allow users to define resources like:

- VPCs,

- EC2 instances,

- S3 buckets,

- Load balancers, etc.

* Since JSON and YAML are standard formats widely known across the industry, CloudFormation becomes a more accessible way to manage infrastructure as code (IaC). Plus, AWS provides extensive documentation to help users write these templates effectively.


# The Rise of IaC Tools:-

* Now that we’ve embraced the concept of Infrastructure as Code, a number of tools have emerged in the industry:

1. CloudFormation for AWS,

2. Azure Resource Manager (ARM) for Microsoft Azure,

3. Heat Templates for OpenStack, etc.

> But there’s a challenge — each of these tools is specific to a cloud provider. This means if my organization uses multiple clouds (say AWS for one project & Azure for another), I would have to learn different tools for each.

* This is where Terraform changes the game.

# Why Terraform is Essential

* Terraform offers a universal, cloud-agnostic approach to infrastructure automation. Developed by HashiCorp, it uses its own language called HCL (HashiCorp Configuration Language) to describe infrastructure requirements.

* Instead of learning a different IaC tool for each provider, I can just learn Terraform, and specify the provider I want to use (AWS, Azure, GCP, etc.). Terraform handles the rest by converting the HCL code into API calls specific to the provider — this is why Terraform is also called API as Code.

# Terraform Benefits:

- Works with multiple providers.

- Uses a declarative language (HCL).

- Reduces manual effort.

- Has a strong community & ecosystem.

- Great for creating highly available & scalable infrastructure.

* In today’s DevOps landscape, where agility & speed are crucial, Terraform has become a mandatory skill.


# Competitors to Terraform

* While Terraform is a pioneer, it does have competitors, such as:

1. Pulumi (uses familiar languages like Python, TypeScript),

2. Crossplane (Kubernetes-native),

3. OpenTofu (a community-driven Terraform fork),

4. Vagrant (for local VM provisioning).

* However, Terraform’s universal approach, community support, and maturity keep it ahead of the competition for now.


# Setting Up a Terraform Environment with GitHub Codespaces

* GitHub Codespaces provides a free development environment (60 hours/month) with:

> 2 vCPUs

> 4 GB RAM

* To set up a Terraform environment:

* Open GitHub Codespaces.

* Search for “Add Dev Container Configuration Files”.

* Modify the active configuration to include:

- Terraform (verified version),

- AWS CLI.

- Apply default settings and click OK.

- Rebuild the container by searching “Rebuild Container” in the command palette.

* Now, We’ll get a new container with Terraform and AWS CLI pre-installed, ready for use.


# The Role of ``main.tf`` File in Terraform

> The main.tf file is the primary configuration file in Terraform. While we can name it anything, using `main.tf` is a best practice.

* In this file, we define:

1. The Terraform block – for required providers & versions.

2. The provider block – for example, specifying AWS as the cloud platform and the region.

3. The resource blocks – defining each AWS resource like S3 buckets, EC2 instances, etc.


* If we want to create 10 resources, we will include 10 such resource blocks. Terraform will understand what needs to be created and will handle the provisioning via the cloud provider's APIs.

# Conclusion

* As infrastructure scales & becomes more complex, manual provisioning is no longer feasible. Learning different IaC tools for each provider is inefficient. Terraform simplifies this with a universal, API-driven approach to infrastructure management. It is an essential skill for modern DevOps & Cloud Engineers, not just for saving time but also for ensuring consistency, scalability & repeatability of infrastructure.


# Most Important Terraform Commands:-

1. *terraform init* > "Terraform init will initialize the configuration, this command will read the terraform files & it will understand that - Ok I have to fetch the AWS Credentials, so let me initialize that configuration for you. As a part of ``terraform init`` when we run this particular command it will get initialize only in that particular folder where terraform configuration files will be present. 

> Initializes the Terraform working directory - It sets up the current directory for use with Terraform. This includes checking configuration files & preparing the workspace.

* Downloads required provider plugins:-

> Terraform scans the configuration to find used providers (e.g., AWS, GCP) & automatically downloads their binaries. This ensures compatibility with our infrastructure code.

* Sets up the backend configuration:

> If a backend (like S3, GCS, or local) is defined, it configures state management accordingly. This enables state sharing and locking when using remote backends.

* Creates the `.terraform` directory:

> This directory stores plugin binaries, module references & other setup files. It helps Terraform keep track of the environment & dependencies.


2. *terraform plan* > Plan command act's just like a dry run where before creating the infrastructure or before applyting the infrastructure we can use this `terraform plan` command to know what exactly it is going to create. By using this ``plan`` command we can cross verify the things before implementing. 

> Generates an execution plan without making changes: It shows what actions Terraform will take to match the current infrastructure with the desired configuration. No real changes are made at this stage.

> Helps us to review the changes before applying them: The plan output lists all resources to be added, modified, or destroyed. This ensures transparency & avoids unintended changes.

> Compares configuration with the current state: Terraform checks the current state file against the configuration files. It identifies differences to create an accurate change plan.

> Validates the syntax & logic of the configuration: It checks for errors like missing variables or misconfigured blocks. This step ensures that our code is ready for deployment.


3. *terraform apply* > 

> Executes the changes required to reach the desired state. Terraform reads the configuration & applies the necessary changes to match the defined infrastructure. It creates, updates, or deletes resources accordingly.

> Prompts for approval before applying changes - By default, it shows the execution plan and asks for user confirmation. This helps prevent accidental modifications.

> Uses the latest state to determine changes - Terraform compares the desired configuration with the current state file. Only the differences are applied to avoid redundant operations.

> Writes the new state to the backend or local file - After successful execution, it updates the state file to reflect the actual infrastructure. This state file is crucial for future plan & apply operations.


4. *terraform destroy* > 

> Destroys all resources defined in the Terraform configuration - It removes the infrastructure managed by Terraform, such as VMs, networks & databases.

> Prompts for confirmation before proceeding - By default, it asks for user approval to avoid accidental deletion of critical resources.

> Uses the state file to identify what to destroy - Terraform reads the current state file to know which resources it created & needs to remove.

> Updates the state after successful destruction - Once resources are deleted, the state file is updated to reflect an empty or changed infrastructure state.


* Terraform State File:- ``terraform state`` file is used to record whatever it is creating, so next time if we create a new file or just add some more configuration in current file this state file will be used as an reference to what we have created and what we are going to create now. 