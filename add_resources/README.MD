## Lab 3 Add resources

### In this lab we will add some basic resources to the VPC using terraform

:white_check_mark: 1. Add a subnet

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


Peform a `$ terraform plan .` and `$ terraform apply .`
check the subnet has been created in the AWS console

Use the `$ terraform state list` and `$ terraform state show xxx.yyy`  commands to look at the local version of the configuration

:white_check_mark: 2. Now add another tag to the subnet.tf file 
```
Environment = "Development"
```

<details>
<summary>Solution - click me</summary>
<p>
subnet.tf

```
resource "aws_subnet" "subnet1" {
  vpc_id     = aws_vpc.main.id
  cidr_block = "10.0.1.0/24"

  tags = {
    Name = "subnet1"
    Environment = "Development"
  }
}

```
<p>
</details>

Rerun `$ terraform plan .` and `$ terraform apply .`

#### :question: What happens & why?


:white_check_mark: 3.  Next - delete the subnet.tf file

Rerun `$ terraform plan .` and `$ terraform apply .`

#### :question: What happens & why?


### :star: Things to note
Open the two solutions above if you haven't already - notice the two different ways to deference (refer to) the VPC id - the later is Terraform v12 style `aws_vpc.main.id` and much cleaner than the former Terraform v11 `"${aws_vpc.main.id}"` style.

In the `$ terraform plan .` commands note that some were adding resources, others changing existing resources and some deleteing resources. Very useful to understand before using apply.

----

## Layering Terraform 
### Divided responsibilities & multiple teams

In this next section we are going to imagine:

* You firstly belong to Team 1: A central team your responsible for creating and deploying VPC's tahgt others consume but should not change / add or delete. 

* Secondly you belong to Team 2: Your job is to consume the VPC's provided by Team 1. Within these pre-created VPC's your team are responsible for creating subnets.

To achive this Terrafor provides "Data Sources". These allow you to safely refer to existing infrastructure that typically someone else has created.


:white_check_mark: 4. Use a data source for the VPC

**Pay close attention to the instructions here**

* Delete the file vpc.tf
  ```console
  $ rm vpc.tf
  ```
* Delete it's state using:
```console
$ terraform state rm aws_vpc.main
Removed aws_vpc.main
Successfully removed 1 resource instance(s).  
```
  
At this point a terraform plan should return nothing:
```console
$ terraform plan .
```
```
The refreshed state will be used to calculate this plan, but will not bepersisted to local or remote state storage.

------------------------------------------------------------------------

No changes. Infrastructure is up-to-date.

This means that Terraform did not detect any differences between your
configuration and real physical resources that exist. As a result, no
actions need to be performed.

```

:white_check_mark: 4. Create a data source for the VPC
**This woould normally be provided to you from another team via source control**

**So pretending your in Team 1**

edit a new file called data_vpc.tf - be sure to set the vpc-xxxxxxxxxxxxx to match your own
```
# set with something like export TF_VAR_vpc_id=vpc-xxxxxxxxxxxxxxxx
variable "vpc_id" {
default="vpc-xxxxxxxxxxxxxxxx" 
}     

data "aws_vpc" "main" {
  id = "${var.vpc_id}"   
}

output "myvpc_id" {
  description = "The ID of the VPC"
  value       = data.aws_vpc.main.id 
}

output "mycidr_block" {
  description = "The ID of the VPC"
  value       = data.aws_vpc.main.cidr_block
}

```

```
$ terraform refresh
```
```
$ terraform state show data.aws_vpc.main
```
```
$ terraform output
```
**Note the output variables are shown**
```
mycidr_block = 10.0.0.0/16
myvpc_id = vpc-02ea7979d995d486f
```


**Now pretending your in Team 2 - use the data file to add your subnet**

Edit a new file subnet.tf

```
resource "aws_subnet" "subnet2" {
  vpc_id     = data.aws_vpc.main.id

  tags = {
    Name = "Main"
    Environment = "Development"
  }
}

```
Note the reference for the vpid_id begins **data**.aws_vpc.main.id


```console
$ terraform plan .
```

```
.....
Plan: 1 to add, 0 to change, 0 to destroy.
```
## :bulb: Note how the plan is just adding the subnet - we no longer are creating/destroying the VPC just referring to it via the data source


### :star: Recap

:key: In this section we have seen how to add/modify and delete terraform resources. 

We have also looked at layering resources using data statements


### Next

:white_check_mark: Proceed to the next module, [Create an EKS Cluster](../create_eks).

