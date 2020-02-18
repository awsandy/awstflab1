## Re-create the EKS cluster using Terraform

### In this lab we will

1. Generate a terraform plan - and save the plan in a file
   
```console
$ terraform plan -out tfplan
```
```
Refreshing Terraform state in-memory prior to plan...
The refreshed state will be used to calculate this plan, but will not be
persisted to local or remote state storage.


------------------------------------------------------------------------

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_eip.eipalloc-03a57b18a7526b3fe will be created
  + resource "aws_eip" "eipalloc-03a57b18a7526b3fe" {
      + allocation_id     = (known after apply)
      + association_id    = (known after apply)
      + domain            = (known after apply)
      + id                = (known after apply)
      + instance          = (known after apply)
      + network_interface = (known after apply)
      + private_dns       = (known after apply)

```
**..... output lines removed for brevity .....**
```
      + owner_id                         = (known after apply)
      + tags                             = {
          + "Name"                                        = "eksctl-ateks1-cluster/VPC"
          + "alpha.eksctl.io/cluster-name"                = "ateks1"
          + "eksctl.cluster.k8s.io/v1alpha1/cluster-name" = "ateks1"
          + "kubernetes.io/cluster/ateks1"                = "shared"
        }
    }

Plan: 55 to add, 0 to change, 0 to destroy.

------------------------------------------------------------------------

This plan was saved to: tfplan

To perform exactly these actions, run the following command to apply:
    terraform apply "tfplan"
```

2. "apply" the plan - which creates the resources in your AWS account
```console
$ terraform apply tfplan
```

```
aws_eip.eipalloc-03a57b18a7526b3fe: Creating...
aws_iam_role.eksctl-ateks1-cluster-ServiceRole-M9Q1LA7D9GKP: Creating...
aws_iam_role_policy.eksctl-ateks1-cluster-ServiceRole-M9Q1LA7D9GKP__eksctl-ateks1-cluster-PolicyNLB: Creating...
aws_iam_role_policy.eksctl-ateks1-nodegroup-ng-1bc714-NodeInstanceRole-L71RPARV2XTY__eksctl-ateks1-nodegroup-ng-1bc7141a-PolicyALBIngress: Creating...
aws_iam_role_policy_attachment.eksctl-ateks1-nodegroup-ng-1bc714-NodeInstanceRole-L71RPARV2XTY__AmazonEKS_CNI_Policy: Creating...
aws_iam_role_policy_attachment.eksctl-ateks1-nodegroup-ng-1bc714-NodeInstanceRole-L71RPARV2XTY__AmazonEKSWorkerNodePolicy: Creating...
aws_iam_role_policy_attachment.eksctl-ateks1-cluster-ServiceRole-M9Q1LA7D9GKP__AmazonEKSServicePolicy: Creating...
aws_iam_role_policy_attachment.eksctl-ateks1-cluster-ServiceRole-M9Q1LA7D9GKP__AmazonEKSClusterPolicy: Creating...
```
**..... output lines removed for brevity .....**
**Note this operation can take 15-20 minutes**

```
output
```

### :star: Tips

:bulb: <span style="color:red"> *If you see an error (red text) during this operation - Just repeat the terraform  pland and terraform apply commands one more time.*</span>

The is caused by some dependacies and race conditions between the Cluster's Roles/Policies and the Cluster creation. Running the plan/apply a seond time will resolve this.


3. Using the AWS command line retreive the credentials for you new cluster

```console
$ aws eks update-cluster-config --name [yourclustername]
```
4. Check the cluster is operational

```console
kubectl get pods --all-namespaces
```

```
output
```

```console
$kubectl get nodes
```
```
output
```

### :star: Tips

:bulb: Keep an open scratch pad in Cloud9 or a text editor on your local computer
for notes.  When the step-by-step directions tell you to note something such as
an ID or Amazon Resource Name (ARN), copy and paste that into the scratch pad.

### :star: Recap

:key: Use a unique personal or development [AWS account](#aws-account)

:key: Keep your [AWS Cloud9 IDE](#aws-cloud9-ide) opened in a tab

### Next

:white_check_mark: Proceed to the next module, [cleanup guide](cleanup).


