## Delete the EKS cluster

### Now we have soem Terraform available to re-create the cluster use the eksctl command to delete the cluster



1. Delete the EKS cluster
   
```console
time eksctl delete cluster --name ateks1 --region eu-west-1
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

:white_check_mark: Proceed to the next module, [Re-create the EKS cluster from Terraform](../terraform_eks).


