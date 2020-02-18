## Lab 3 Add resources

### In this lab we will take timeout form Terraform to create a Kubernetes Cluster



1. Install the eksctl & kubectl command line tools

A setup script has been provided to install the necessaru tools - jq and eksctl 

```
cd ~/environment/awstflab1-code/scripts
./02-install-eksctl.sh
```

```
sudo yum install jq -y
Loaded plugins: priorities, update-motd, upgrade-helper
amzn-main                                                                                                                                                                                 | 2.1 kB  00:00:00     
amzn-updates                                                                                                                                                                              | 2.5 kB  00:00:00     
1073 packages excluded due to repository priority protections
Package jq-1.5-1.2.amzn1.x86_64 already installed and latest version
Nothing to do
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 41.4M  100 41.4M    0     0   105M      0 --:--:-- --:--:-- --:--:--  105M
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
curl --silent --location "https://github.com/weaveworks/eksctl/releases/download/latest_release/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
jq --version
jq-1.5
eksctl version
[ℹ]  version.Info{BuiltAt:"", GitCommit:"", GitTag:"0.13.0"}
kubectl version --client
Client Version: version.Info{Major:"1", Minor:"17", GitVersion:"v1.17.3", GitCommit:"06ad960bfd03b39c8310aaf92d1e7c12ce618213", GitTreeState:"clean", BuildDate:"2020-02-11T18:14:22Z", GoVersion:"go1.13.6", Compiler:"gc", Platform:"linux/amd64"}
```

2. Create a Kubernetes (EKS) cluster

```
$ export AWS_REGION=eu-west-1
$ time eksctl create cluster --name=ateksf --nodes=2 --node-type="t3.large" --managed --fargate --alb-ingress-access --region=${AWS_REGION} --ssh-public-key "~/.ssh/id_rsa.pub"
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

:white_check_mark: Proceed to the next module, [Autmatically create the Terraform for the EKS cluster](../pull_terraform), 


[region-table]: https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/
[Create a Kubernetes Cluster]: ../4_create_eks/

