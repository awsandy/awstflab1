## Re-create the EKS cluster using Terraform

### Re-create the EKS cluster using terraform

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
aws_eks_cluster.ateksf: Still creating... [11m0s elapsed]
aws_eks_cluster.ateksf: Still creating... [11m10s elapsed]
aws_eks_cluster.ateksf: Still creating... [11m20s elapsed]
aws_eks_cluster.ateksf: Creation complete after 11m22s [id=ateksf]
aws_eks_node_group.ateksf_ng-96e8ad24: Creating...
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [10s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [20s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [30s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [40s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [50s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [1m0s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [1m10s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [1m20s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [1m30s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [1m40s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Still creating... [1m50s elapsed]
aws_eks_node_group.ateksf_ng-96e8ad24: Creation complete after 1m59s [id=ateksf:ng-96e8ad24]

Apply complete! Resources: 9 added, 0 changed, 0 destroyed.

The state of your infrastructure has been saved to the path
below. This state is required to modify and destroy your
infrastructure, so keep it safe. To inspect the complete state
use the `terraform show` command.

State path: terraform.tfstate
```

### :star: Tips

:bulb: 
```diff
- *If you see errors (red text) during this operation 
- Just repeat the terraform plan and terraform apply commands one more time.* 
```
The is caused by some dependacies and race conditions between the Cluster's Roles/Policies and the Cluster creation. Running the plan/apply a second time will resolve this.


### Once the Cluster has been created

3. Using the AWS command line retreive the credentials for you new cluster

```console
$ aws eks update-kubeconfig --name [yourclustername]
```

```
Added new context arn:aws:eks:eu-west-1:111122223333:cluster/[yourclustername] to /Users/youruser/.kube/config
```

4. Check the cluster is operational

```console
$ kubectl get pods --all-namespaces
```

```
NAMESPACE     NAME                       READY   STATUS    RESTARTS   AGE
kube-system   aws-node-gzqdf             1/1     Running   0          5m10s
kube-system   aws-node-qw7tp             1/1     Running   0          5m24s
kube-system   coredns-5fd8748bdd-5d7pz   1/1     Running   0          9m5s
kube-system   coredns-5fd8748bdd-ns7qz   1/1     Running   0          9m4s
kube-system   kube-proxy-fhvpm           1/1     Running   0          5m24s
kube-system   kube-proxy-sdb2n           1/1     Running   0          5m10s
```

```console
$ kubectl get nodes
```
```
NAME                                           STATUS   ROLES    AGE     VERSION
ip-192-168-58-200.eu-west-1.compute.internal   Ready    <none>   5m57s   v1.14.7-eks-1861c5
ip-192-168-81-4.eu-west-1.compute.internal     Ready    <none>   5m43s   v1.14.7-eks-1861c5
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


