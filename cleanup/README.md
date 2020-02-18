## Cleanup resources

### In this lab 

1. Destroy the cluster with Terraform

**Note a destroy operation will take about 15-20 minutes to complete**

```console
$ terraform destroy
```
**..... output lines removed for brevity .....**
```
          - "eksctl.cluster.k8s.io/v1alpha1/cluster-name" = "[yourclustername]"
          - "kubernetes.io/cluster/[yourclustername]"                = "shared"
        } -> null
    }

Plan: 0 to add, 0 to change, 55 to destroy.

Do you really want to destroy all resources?
  Terraform will destroy all your managed infrastructure, as shown above.
  There is no undo. Only 'yes' will be accepted to confirm.
```
  Enter a value: **yes**
```
aws_route_table_association.rtbassoc-0115c7b18869a02f3: Destroying... [id=rtbassoc-0115c7b18869a02f3]
aws_route_table.rtb-0ea284cd4547961cd: Destroying... [id=rtb-0ea284cd4547961cd]
aws_route_table_association.rtbassoc-0f4e141aaf15a074a: Destroying... [id=rtbassoc-0f4e141aaf15a074a]
aws_route_table.rtb-033220495352e8a9f: Destroying... [id=rtb-033220495352e8a9f]
aws_security_group_rule.sg-02984c8f9c87633cf: Destroying... [id=sgrule-2008478280]
```
   
**..... output lines removed for brevity .....**


```
aws_eks_cluster.[yourclustername]: Still destroying... [id=[yourclustername], 9m10s elapsed]
aws_eks_cluster.[yourclustername]: Still destroying... [id=[yourclustername], 9m20s elapsed]
aws_subnet.subnet-03a107ac996fab132: Destruction complete after 0s
aws_subnet.subnet-01d9337798ba5b52b: Destruction complete after 0s
aws_subnet.subnet-029909c92d8b8920d: Destruction complete after 0s
aws_iam_role.eksctl-[yourclustername]-cluster-ServiceRole-M9Q1LA7D9GKP: Destruction complete after 1s
```

**Note you may see an error at the end like this - it can be ignored**

```
Error: InvalidParameterValue: cannot disassociate the main route table association rtbassoc-082561b86b786dab6
	status code: 400, request id: a5dfc518-83bd-4345-bd5a-4bec9f81be3e
```


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

