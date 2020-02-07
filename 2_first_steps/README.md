
### Initialize the terraform resource provider

In this section we will initiaize terraform and build a basic VPC using terraform infrastructire as code


![Terraform stages](../images/terraform.png)


**:white_check_mark: Step-by-step Instructions**

1. Within your Cloud9 IDE bash window run the following :


    ```console

    andyt530:~/environment/awstflab-code/2_first_steps (master) $ terraform init                        ```                                                                                        

    ```
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



### Next

:white_check_mark: Proceed to the first module, [Add additional resources](../3), 


[region-table]: https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/
[static-web-hosting]: ../1_StaticWebHosting/

