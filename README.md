# awstflab1 March 18th


### Modules

This workshop is divided into several modules. Each module describes a scenario of
what we're going to build and step-by-step directions to help you implement the
architecture and verify your work.

| Module | Description |
| ---------------- | -------------------------------------------------------- |
| [Initial Setup][0_setup] | Login to your lab AWS account and create an AWS Cloud9 environment in region eu-west-1 (Ireland). |
| [Initialize Terraform][1_Init] | Configure user management for the website using Amazon Cognito. |
| [Serverless Backend][serverless-backend] | Create an AWS Lambda function that will persist data to an Amazon DynamoDB table. |
| [RESTful APIs][restful-apis] | Expose the Lambda function via an Amazon API Gateway as a RESTful API that the static site can call. |



## Intro
## [Lab0 - Setup Lab](0_Setup)
## [Lab1 - Initialize Terraform](1_Init)
## [Lab2 - First steps](2_first_steps)
## [Lab3 -](3_add_resources)

## [Lab4 - Create EKS Cluster](4_create_eks)
## [Lab5 - Reverse the Cluster](5_pull_terraform)
## [Lab6 - Delete The Cluster](6_delete-eks)
## [Lab7 - Recreate with Terraform](7_terraform_eks)

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