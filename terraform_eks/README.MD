## Re-create the EKS cluster using Terraform

### In this lab we will

1. Generate a terraform plan - and save the plan in a file
   
```console
$ terraform plan -out tfplan
```
```

```
**..... output lines removed for brevity .....**
```

```

2. "apply" the plan - which creates the resources in your AWS account
```console
$ terraform apply tfplan
```

```
output
```

```
**..... output lines removed for brevity .....**
```
more output
```

3. Using the AWS command line retreive the credentials for you new cluster

```console
$ aws eks 
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


