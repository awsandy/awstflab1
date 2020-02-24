# AWS Terraform Lab



### Modules

This workshop is divided into several modules. Each module describes a scenario of
what we're going to build and step-by-step directions to help you implement the
architecture and verify your work.

| Module | Description |
| ---------------- | -------------------------------------------------------- |
| [Initial setup guide](setup) | Login to your lab AWS account and create an AWS Cloud9 environment in region eu-west-1 (Ireland). |
| [Initialize Terraform](Init) | Download and install terraform |
| [First steps with Terraform](first_steps) | Create a VPC using Terraform |
| [Add Resources](add_resources) | Add some additional resources to your VPC and examine Terraforn state |
| [Create an EKS Cluster with the command line](create_eks)] | Create an EKS cluster on AWS using the eksctl command line |
| [Automatically generate Terraform code for EKS](pull_terraform) | Use the provided tool to import the EKS cluster into Terraform and automaticvally generate terraform files. |
| [Delete the EKS cluster !](delete-eks) | Delete the EKS cluster using the eksctl command and delete the residual VPC. |
| [Re-create the EKS cluster from Terraform](terraform_eks) | Using the previously automatically generated Terraform re-create the EKS cluster on AWS. |

After you have completed the workshop you can delete all of the resources that were created by following the [cleanup guide](cleanup).

### Next

:white_check_mark: Review and follow the directions in the [Initial setup guide](setup),
wherein you'll setup pre-requisites like an
AWS Account & configure your AWS Cloud9 IDE and 


### References

https://github.com/terraform-providers/terraform-provider-aws/tree/master/examples


![Static website architecture](../images/spinning-gears.gif)

### collapsible markdown?
<details>
<summary>CLICK ME</summary>
<p>
#### yes, even hidden code blocks!

```python
print("hello world!")
```
</p>
</details>