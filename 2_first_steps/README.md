
### Initialize the terraform resource provider

In this section we will initiaize terraform and build a basic VPC using terraform infrastructire as code


![Terraform stages](../images/terraform.png)


**:white_check_mark: Step-by-step Instructions**

1. Within your Cloud9 IDE bash window run the following :


    ```console

    andyt530:~/environment/awstflab-code/2_first_steps (master) $ terraform init                                                                                                                 

    Initializing the backend...

    Initializing provider plugins...
    - Checking for available provider plugins...
    - Downloading plugin for provider "aws" (hashicorp/aws) 2.48.0...

    Terraform has been successfully initialized!

    You may now begin working with Terraform. Try running "terraform plan" to see
    any changes that are required for your infrastructure. All Terraform commands
    should now work.

    If you ever set or change modules or backend configuration for Terraform,
    rerun this command to reinitialize your working directory. If you forget, other
    commands will detect it and remind you to do so if necessary.
    andyt530:~/environment/awstflab-code/2_first_steps (master) $ 

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

:white_check_mark: Proceed to the first module, [Static Web Hosting][static-web-hosting], 
wherein you'll deploy a static web site via AWS Amplify Console.

[region-table]: https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/
[static-web-hosting]: ../1_StaticWebHosting/

