# awstflab1 March 18th


### Modules

This workshop is divided into several modules. Each module describes a scenario of
what we're going to build and step-by-step directions to help you implement the
architecture and verify your work.

| Module | Description |
| ---------------- | -------------------------------------------------------- |
| [Initial setup guide](setup) | Login to your lab AWS account and create an AWS Cloud9 environment in region eu-west-1 (Ireland). |
| [Initialize Terraform](Init) | Configure user management for the website using Amazon Cognito. |
| [First steps with Terraform](first_steps) | Create an AWS Lambda function that will persist data to an Amazon DynamoDB table. |
| [Add Resources](add_resources) | Expose the Lambda function via an Amazon API Gateway as a RESTful API that the static site can call. |
| [Create an EKS Cluster with the command line](create_eks)] | Expose the Lambda function via an Amazon API Gateway as a RESTful API that the static site can call. |
| [Automatically generate Terraform code for EKS](pull_terraform) | Expose the Lambda function via an Amazon API Gateway as a RESTful API that the static site can call. |
| [Delete the EKS cluster !](delete-eks) | Expose the Lambda function via an Amazon API Gateway as a RESTful API that the static site can call. |
| [Re-create the EKS cluster from Terraform](terraform_eks) | Expose the Lambda function via an Amazon API Gateway as a RESTful API that the static site can call. |

After you have completed the workshop you can delete all of the resources that were created by following the [cleanup guide][cleanup].

### Next

:white_check_mark: Review and follow the directions in the [Initial setup guide][setup],
wherein you'll setup pre-requisites like an
AWS Account & configure your AWS Cloud9 IDE and 


### References

https://github.com/terraform-providers/terraform-provider-aws/tree/master/examples

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