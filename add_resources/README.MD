## Lab 3 Add resources

### In this lab we will add some basic resources to the VPC using terraform

1. Add a subnet

Add a subnet named "subnet1" to your configuration with a CIDR of 10.0.1.0/24

### :star: TIP

:key: Create a new file subnet.tf

:key: Use the terraform documentation for guidance https://www.terraform.io/docs/providers/aws/r/subnet.html
   
<details>
<summary>Solution - click me</summary>
<p>
subnet.tf

```
resource "aws_subnet" "main" {
  vpc_id     = "${aws_vpc.main.id}"
  cidr_block = "10.0.1.0/24"

  tags = {
    Name = "Main"
  }
}

```
<p>
</details>


Peform a terraform plan and terraform apply
check the subnet has been created in the AWS console

Use the **terraform state list** and **terraform state show xxx.yyy**  commands to look at the local version of the configuration

2. Now add another tag to the subnet.tf file 
```
Environment = "Development"
```

Rerun **terraform plan** and **terraform apply**

#### :question: What happens & why?


3.  Next - delete the subnet.tf file

Rerun **terraform plan** and **terraform apply**

#### :question: What happens & why?



---

## Layering Terraform )divided responsibilities & multiple teams

In this next section we are going to imagine:

*A central team is responsible to creating and deploying VPC's. Your job is to consume the VPC's provided.
*Within these pre-created VPC's you are responsible for creating subnets - but must not create or detroy and existing VPC's








### :star: Recap

:key: Use a unique personal or development [AWS account](#aws-account)

:key: Keep your [AWS Cloud9 IDE](#aws-cloud9-ide) opened in a tab

### Next

:white_check_mark: Proceed to the next module, [Create an EKS Cluster](../create_eks).



