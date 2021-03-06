## Lab 3 Add resources

### In this lab we will take timeout form Terraform to create a Kubernetes Cluster



1. Install the eksctl & kubectl command line tools

A setup script has been provided to install the necessaru tools - jq and eksctl 

```console
$ cd ~/environment/awstflab1-code/scripts
$ ./02-install-eksctl.sh
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

```console
$ export AWS_REGION=eu-west-1
$ time eksctl create cluster --name=[yourinitials+eks] --fargate --alb-ingress-access --region=${AWS_REGION} --ssh-public-key "~/.ssh/id_rsa.pub"
```
**Note a create operatiobn will take about 15 minues to complete**
```
[ℹ]  eksctl version 0.11.1
[ℹ]  using region eu-west-1
[ℹ]  setting availability zones to [eu-west-1b eu-west-1c eu-west-1a]
[ℹ]  subnets for eu-west-1b - public:192.168.0.0/19 private:192.168.96.0/19
```


**Make a note of the stack name**
```
[ℹ]  building cluster stack "eksctl-[yourclustername]-cluster"
[ℹ]  deploying stack "eksctl-[yourclustername]-cluster"
```
**..... output lines removed for brevity .....**

```
[ℹ]  "coredns" is now scheduled onto Fargate
[ℹ]  "coredns" pods are now scheduled onto Fargate
[ℹ]  kubectl command should work with "/Users/awsandy/.kube/config", try 'kubectl get nodes'
[✔]  EKS cluster "[yourclustername]" in "eu-west-1" region is ready


```

Next check the cluster has created ok
```console
$ kubectl get nodes
```
```
NAME                                                    STATUS   ROLES    AGE   VERSION
fargate-ip-192-168-140-21.eu-west-1.compute.internal    Ready    <none>   18m   v1.14.8-eks
fargate-ip-192-168-152-202.eu-west-1.compute.internal   Ready    <none>   18m   v1.14.8-eks
```

And that basic services are running

```console
$ kubectl get pods --all-namespaces
```
```
NAMESPACE     NAME                       READY   STATUS    RESTARTS   AGE
kube-system   aws-node-4gzb9             1/1     Running   0          23m
kube-system   aws-node-ffrxf             1/1     Running   0          23m
kube-system   coredns-56f75d76cb-gxm9r   1/1     Running   0          20m
kube-system   coredns-56f75d76cb-vxv4g   1/1     Running   0          20m
kube-system   kube-proxy-49fnc           1/1     Running   0          23m
kube-system   kube-proxy-nkx9l           1/1     Running   0          23m

```


3. Examine all the resources that have been created
   
Using the AWS console find the VPC that EKS created - what other resources have been created ? 

Can you find the stack set that was run by eksctl - what resources did it create ?

<details>
<summary>See how - click me</summary>
<p><ul>
<li>Using the AWS Console navigate to CloudFormation.</li>
<li>Look for a stack name eksctl-[yourname]-cluster and click it's link.</li>
<li>Look in the Events and Resources tabs to see what has been created.</li>
</ul><p>
</details>




### :star: Recap

:key: In this section we have created a new EKS (fareate cluster) using the eksctl command line tool

### Next

:white_check_mark: Proceed to the next module, [Autmatically create the Terraform for the EKS cluster](../pull_terraform).



