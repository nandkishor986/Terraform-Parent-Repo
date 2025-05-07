# Setup Terraform for AWS

* To configure AWS credentials & set up Terraform to work with AWS, we'll need to follow these steps:

1. **Install AWS CLI (Command Line Interface)**:

> Make sure we have the AWS CLI installed on our machine. We can download & install it from the [AWS CLI download page](https://aws.amazon.com/cli/).

2. **Create an AWS IAM User**:

> To interact with AWS programmatically, we should create an IAM (Identity and Access Management) user with appropriate permissions. Here's how to create one:

a. Log in to the AWS Management Console with an account that has administrative privileges.

b. Navigate to the IAM service.

c. Click on "Users" in the left navigation pane & then click "Add user."

- Choose a username, select "Programmatic access" as the access type, and click "Next: Permissions."

- Attach policies to this user based on our requirements. At a minimum, we should attach the "AmazonEC2FullAccess" policy for basic EC2 operations. If we need access to other AWS services, attach the relevant policies accordingly.

- Review the user's configuration & create the user. Be sure to save the Access Key ID & Secret Access Key that are displayed after user creation; we'll need these for Terraform.

3. **Configure AWS CLI Credentials**:

* Use the AWS CLI to configure our credentials. Open a terminal and run:

```
aws configure
```

* It will prompt us to enter our AWS Access Key ID, Secret Access Key, default region, and default output format. Enter the credentials obtained in the previous step.