## Setup

### Download & run Helper scripts

In this section we will download a helper script that will install terraform into the Cloud9 IDE you have created



**:white_check_mark: Step-by-step Instructions**

1. Within your Cloud9 IDE bash window run the following to download the helper scripts:


    ```console
    andyt530:~/environment $ git clone https://github.com/andyt530/awstflab-code.git
    Cloning into 'awstflab-code'...
    remote: Enumerating objects: 8, done.
    remote: Counting objects: 100% (8/8), done.
    remote: Compressing objects: 100% (7/7), done.
    remote: Total 8 (delta 0), reused 4 (delta 0), pack-reused 0
    Unpacking objects: 100% (8/8), done.
    andyt530:~/environment $ ls
    awstflab-code  README.md
    andyt530:~/environment $ cd awstflab-code/scripts
    andyt530:~/environment/awstflab-code/scripts (master) $ 
    ```

    ![Cloud9](../images/IDE1.jpg)

2. Run the helper script to install terraform

    '''
    andyt530:~/environment/awstflab-code/scripts (master) $ sh -v 01-install-terraform.sh
    wget https://releases.hashicorp.com/terraform/0.12.18/terraform_0.12.18_linux_amd64.zip
    --2020-02-07 11:39:38--  https://releases.hashicorp.com/terraform/0.12.18/terraform_0.12.18_linux_amd64.zip
    Resolving releases.hashicorp.com (releases.hashicorp.com)... 199.232.57.183, 2a04:4e42:4b::439
    Connecting to releases.hashicorp.com (releases.hashicorp.com)|199.232.57.183|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 16519860 (16M) [application/zip]
    Saving to: ‘terraform_0.12.18_linux_amd64.zip’

    terraform_0.12.18_linux_amd64.zip                    100%[===================================================================================================================>]  15.75M  --.-KB/s    in 0.1s    

    2020-02-07 11:39:39 (137 MB/s) - ‘terraform_0.12.18_linux_amd64.zip’ saved [16519860/16519860]

    unzip terraform_0.12.18_linux_amd64.zip
    Archive:  terraform_0.12.18_linux_amd64.zip
    inflating: terraform               
    sudo mv terraform /usr/local/bin/
    andyt530:~/environment/awstflab-code/scripts (master) $ 
    '''

3. check terraform is installed correctly

    '''
    andyt530:~/environment/awstflab-code/scripts (master) $ terraform help
    Usage: terraform [-version] [-help] <command> [args]

    ..... serveral other lines not shown here .....

    andyt530:~/environment/awstflab-code/scripts (master) $ 
    '''

4. return to your working directory ready for the next part
   '''
    andyt530:~/environment/awstflab-code/scripts (master) $ cd ~/environment
    andyt530:~/environment $ 
   '''

### Next

:white_check_mark: Proceed to the first module, [Connecting terraform to AWS](2_first_steps), 


[region-table]: https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/
[static-web-hosting]: ../1_StaticWebHosting/

