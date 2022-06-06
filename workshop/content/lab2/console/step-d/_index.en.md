+++
title = "Step D - Crawl Data"
weight = 130
+++

1. Open up a new browser tab and point it at https://console.aws.amazon.com/iam.

2. Click on 'Roles' in the left-hand pane (see screenshot below #3)

3. And then type 'Glue' in the Search box, which should bring up a role named 'AWSGlueServiceRole-[SOME\_UNIQUE\_IDENTIFIER]' that you configured in [Step C]({{% relref "lab2/console/step-c#glue-iam-role" %}}) (scroll down to #7). 

   Click on the role.

   ![Update Glue Service Linked Role](/images/lab2/iam_glue_role_1.png)   
   
4. In the subsequent screen, click again on the Glue service linked role named 'AWSGlueServiceRole-[SOME\_UNIQUE\_IDENTIFIER]'

   ![Click Glue Service Linked Role](/images/lab2/iam_glue_click_service_role_2.png)   
   
5. Click on 'Edit Policy'

   ![Edit Glue Service Linked Role Policy](/images/lab2/iam_glue_role_edit_policy_3.png)   
   
6. Click on 'JSON'.

   ![](/images/lab2/iam_glue_edited_role_4.png)   
   
7. Copy paste the below permissions policy. 

   **NOTE:** Replace YOUR\_S3\_BUCKET\_NAME with what you used so that Glue may access **YOUR** S3 bucket.

   ```json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "s3:GetObject",
                    "s3:PutObject"
                ],
                "Resource": [
                    "arn:aws:s3:::YOUR_S3_BUCKET_NAME/prod-retail-data/*"
                ]
            }
        ]
    }   
   ```   
   
8. Click on 'Review policy'

9. Click on 'Save changes'

   ![](/images/lab2/iam_glue_role_save_changes_5.png)   
   
10. Close this browser tab.   

12. You should have now returned to the previous tab you were on, when you had just finished creating a Glue crawler. Now Click on 'Run it now?' to crawl your S3 data.

   This will take at least 1-2 mins from start to finish. Wait for the crawler to complete running (click on the refresh icon in the top-right a few times).

   ![Run Crawler](/images/lab2/glue_9_run_it_now.png)    
   
13. To verify that the Glue crawler has crawled your S3 data, has automatically discovered the underlying schema, and has created a table on your behalf, click on 'Tables' on the left-hand pane.

14. Enter 'retail\_analytics\_db' in the 'Search' field to narrow results down (if necessary)

    ![](/images/lab2/glue_view_database_tables.png)
    
    You should see a new table created in ```retail_analytics_db```. 
