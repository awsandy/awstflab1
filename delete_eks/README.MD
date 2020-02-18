## Delete the EKS cluster

### Now we have soem Terraform available to re-create the cluster use the eksctl command to delete the cluster



1. Delete the EKS cluster
   
**Note this operation can take 15-20 minutes**

```console
time eksctl delete cluster --name [yourclustername] --region eu-west-1
```

```
[ℹ]  eksctl version 0.11.1
[ℹ]  using region eu-west-1
[ℹ]  deleting EKS cluster "ateksf"
[ℹ]  deleting Fargate profile "fp-default"
[ℹ]  deleted Fargate profile "fp-default"
[ℹ]  deleted 1 Fargate profile(s)
[✔]  kubeconfig has been updated
[ℹ]  cleaning up LoadBalancer services
[ℹ]  2 sequential tasks: { delete nodegroup "ng-96e8ad24", delete cluster control plane "ateksf" [async] }
[ℹ]  will delete stack "eksctl-ateksf-nodegroup-ng-96e8ad24"
[ℹ]  waiting for stack "eksctl-ateksf-nodegroup-ng-96e8ad24" to get deleted
[ℹ]  will delete stack "eksctl-ateksf-cluster"
[✔]  all cluster resources were deleted

```



### :star: Tips

:bulb: Keep an open scratch pad in Cloud9 or a text editor on your local computer
for notes.  When the step-by-step directions tell you to note something such as
an ID or Amazon Resource Name (ARN), copy and paste that into the scratch pad.

### :star: Recap

:key: Use a unique personal or development [AWS account](#aws-account)

:key: Keep your [AWS Cloud9 IDE](#aws-cloud9-ide) opened in a tab

### Next

:white_check_mark: Proceed to the next module, [Re-create the EKS cluster from Terraform](../terraform_eks).


