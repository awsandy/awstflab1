## Lab 3 Add resources

### In this lab we will take timeout form Terraform to create a Kubernetes Cluster



1. Install the eksctl & kubectl command line tools

A setup script has been provided to install the necessaru tools - jq and eksctl 

```
cd ~/environment/awstflab1-code/scripts
./02-install-eksctl.sh
```

```
output here
```

2. Createan EKS cluster

```
$ export AWS_REGION=eu-west-1
time eksctl create cluster --name=ateksf --nodes=2 --node-type="t3.large" --managed --fargate --alb-ingress-access --region=${AWS_REGION} --ssh-public-key "~/.ssh/id_rsa.pub"
```

```
output here
```

Next check the cluster has created ok
```
$ kubectl get nodes
```

3. Examine all the resources that have been created
   
Using the AWS console find the VPC that EKS created - what other resources have been created ? 

Can you find the stack set that was run by eksctl - what resources did it create ?
   



### :star: Tips

:bulb: Keep an open scratch pad in Cloud9 or a text editor on your local computer
for notes.  When the step-by-step directions tell you to note something such as
an ID or Amazon Resource Name (ARN), copy and paste that into the scratch pad.

### :star: Recap

:key: Use a unique personal or development [AWS account](#aws-account)

:key: Keep your [AWS Cloud9 IDE](#aws-cloud9-ide) opened in a tab

### Next

:white_check_mark: Proceed to the next module, [Tools initialization](../1_Init), 


[region-table]: https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/
[Create a Kubernetes Cluster]: ../4_create_eks/

