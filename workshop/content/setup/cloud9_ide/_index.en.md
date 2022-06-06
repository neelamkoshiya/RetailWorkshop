+++
title = "Cloud9 IDE Setup"
weight = 20
pre = "2. "
+++

We will use a Cloud9 environment, which should have all of the most popular languages (Ruby, Python, NodeJS, Java, etc.) and many associated libraries already installed, to help save time and serve as a launch pad.


1. Point your browser to https://console.aws.amazon.com/cloud9

2. On the top right-hand corner, ensure that you're in the Oregon region if you're using the AWS account provided as part of this workshop. 

   If you're using your own account however, choose one of the 6 regions above (Oregon still recommended).

2. Click on 'Create environment'

   ![Cloud9 Create Environment](/images/cloud_9_create_environment.png)
   
3. For 'Name', enter a something descriptive like 'Retail_IDE' 

4. Click 'Next step'

   ![Cloud9 Name Environment](/images/cloud_9_name_environment.png)
   
5. Leave the 'Environment type' default option chosen as 'Create a new instance for environment (EC2)'

6. For 'Instance type' choose 't2.small (2 GiB RAM + 1 vCPU)

   ![Cloud9 Configure Environment 1](/images/cloud_9_configure_environment.png)
   
7. Leave the 'Platform' option (chosen by default) at 'Amazon Linux' 

8. For 'Cost-saving setting', choose 'After four hours'

9. Click 'Next Step'

   ![Cloud9 Configure Environment 2](/images/cloud_9_configure_environment_2.png)          

   
10. In the final configuration screen, scroll down and click 'Create environment'

    ![Create Environment](/images/cloud_9_create_environment_final.png)
    
11. It will take about a minute for the Cloud9 environment to be created.

### Customize Cloud9 IDE [OPTIONAL]

12. If you prefer dark themes, click on the settings gear icon in the top right hand corner to open up the preferences pane and choose one of the available dark themes.

    ![Choose Theme](/images/cloud_9_themes.png)
    

### Clone the Repo

1. In the Cloud9 IDE bash terminal run this to clone the src code

```shell
git clone https://github.com/amitnarayanan/retail-workshop-src.git
```
