# Variables:

* Input & output variables in Terraform are essential for parameterizing and sharing values within our Terraform configurations and modules. They allow us to make our configurations more dynamic, reusable, and flexible.

## Input Variables:

* Input variables are used to parameterize our Terraform configurations. They allow us to pass values into our modules or configurations from the outside. Input variables can be defined within a module or at the root level of our configuration. Here's how we define an input variable:

```hcl
variable "name" {
  description = "Name of an EC2 Instnace"
  type        = string
  default     = "webserver"
}
```

In this example:

- `variable` is used to declare an input variable named `name`.
- `description` provides a human-readable description of the variable.
- `type` specifies the data type of the variable (e.g., `string`, `number`, `list`, `map`, etc.).
- `default` provides a default value for the variable, which is optional.

We can then use the input variable within our module or configuration like this:

```hcl
resource "aws_instance" "abc" {
  name = var.name
  # other resource configurations
}
```

* We reference the input variable using `var.example_var`.

## Output Variables

* Output variables allows us to expose values from our module or configuration, making them available for use in other parts of our Terraform setup. Here's how we define an output variable:

```hcl
output "instance_id" {
  description = "Output the Instance ID of EC2 Instance"
  value       = resource.aws_instance.instance_id
}
```

* In this example:

- `output` is used to declare an output variable named `instance_id`.
- `description` provides a description of the output variable.
- `value` specifies the value that we want to expose as an output variable. This value can be a resource attribute, a computed value, or any other expression.

* We can reference output variables in the root module or in other modules by using the syntax `module.module_name.output_name`, where `module_name` is the name of the module containing the output variable.

* For example, if we have an output variable named `example_output` in a module called `example_module`, we can access it in the root module like this:

```hcl
output "root_output" {
  value = module.example_module.example_output
}
```

* This allows us to share data and values between different parts of our Terraform configuration and create more modular and maintainable infrastructure-as-code setups.