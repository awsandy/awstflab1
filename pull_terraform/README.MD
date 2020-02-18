## Lab 3 Add resources

### In this lab we will add soem basic resources to the VPC using terraform

1. Run the tool to create the Terraform for EKS

```console
$ ./eks2th.sh
```

```
Account ID = 566972129213
Terraform Resource Type Filter = 
 
terraform init

Initializing the backend...

Initializing provider plugins...
- Checking for available provider plugins...
- Downloading plugin for provider "aws" (hashicorp/aws) 2.49.0...

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
Tue 18 Feb 2020 12:13:54 GMT
loop through providers
/Users/awsandy/odp/aws/sw/aws2tf/generated/tf.566972129213-eks
300-get-eks-cluster.sh
all
cluster name ateks1
get other stuff
vpc-0913cefa99679c043
aws_vpc.vpc-0913cefa99679c043: Importing from ID "vpc-0913cefa99679c043"...
aws_vpc.vpc-0913cefa99679c043: Import prepared!
  Prepared aws_vpc for import
aws_vpc.vpc-0913cefa99679c043: Refreshing state... [id=vpc-0913cefa99679c043]
```
**..... output lines removed for brevity .....**

```
aws_route_table_association.rtbassoc-0fd049ea1bb5fcb05: Refreshing state... [id=rtbassoc-0fd049ea1bb5fcb05]
aws_route_table_association.rtbassoc-054bdca72f36ed291: Refreshing state... [id=rtbassoc-054bdca72f36ed291]
aws_route_table.rtb-0520c23f71ba9173e: Refreshing state... [id=rtb-0520c23f71ba9173e]
aws_route_table.rtb-072106e2ccff8dfd7: Refreshing state... [id=rtb-072106e2ccff8dfd7]
aws_route_table.rtb-04168a54979d23519: Refreshing state... [id=rtb-04168a54979d23519]
aws_route_table_association.rtbassoc-0f4e141aaf15a074a: Refreshing state... [id=rtbassoc-0f4e141aaf15a074a]
aws_route_table_association.rtbassoc-0115c7b18869a02f3: Refreshing state... [id=rtbassoc-0115c7b18869a02f3]
aws_eks_node_group.ateks1_ng-1bc7141a: Refreshing state... [id=ateks1:ng-1bc7141a]
aws_route_table_association.rtbassoc-0e4c4bd87f99580f5: Refreshing state... [id=rtbassoc-0e4c4bd87f99580f5]

------------------------------------------------------------------------

No changes. Infrastructure is up-to-date.

This means that Terraform did not detect any differences between your
configuration and real physical resources that exist. As a result, no
actions need to be performed.
---------------------------------------------------------------------------
aws2tf output files are in generated/tf.566972129213-eks
---------------------------------------------------------------------------
f8ffc212119c:aws2tf awsandy$ 

```
   

2. Examine the terraform files that have been created

```console
$ cd generated/tf.566972129213-eks
$ ls *.tf
```

### :star: Tips

:bulb: Keep an open scratch pad in Cloud9 or a text editor on your local computer
for notes.  When the step-by-step directions tell you to note something such as
an ID or Amazon Resource Name (ARN), copy and paste that into the scratch pad.

### :star: Recap

:key: Use a unique personal or development [AWS account](#aws-account)

:key: Keep your [AWS Cloud9 IDE](#aws-cloud9-ide) opened in a tab

### Next

:white_check_mark: Proceed to the next module, [Delete the EKS cluster !](../delete_eks). 



