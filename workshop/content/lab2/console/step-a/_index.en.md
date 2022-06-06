+++
title = "Step A - Firehose Destination"
weight = 100
+++

1. Click on the 'Destination' tab, and then click on 'Connect to a destination'. We will create a 'Firehose' destination.

   ![Analytics Destination](/images/lab2/analytics_destination.png)
   
2. For 'Destination', choose 'Kinesis Firehose delivery stream'

3. And for 'Kinesis Firehose delivery stream', click on 'Create new'. This will open up a new tab in which we will create and configure a new Kinesis Firehose delivery stream.

   ![Connect to Destination](/images/lab2/analytics_connect_destination.png)   
   
4. Create a Kinesis Firehose stream. Enter a descriptive name for 'Delivery stream name' and click 'Create'

5. In the 'New delivery stream' page, leave the rest of the options as-is. Click on 'Next'

   ![Create Firehose](/images/lab2/create_firehose.png)

5. In the subsequent 'Process records' page, scroll down to the 'Transform source records with AWS Lambda' section.

   For 'Data transformation' choose 'Enabled'.
   
6. Click on 'Create new'   

   ![Create Firehose Page 2](/images/lab2/create_firehose_2.png)
   
7. Click on 'General Firehose Processing' (the first link) 

   ![Choose a Lambda Blueprint](/images/lab2/choose_lambda_blueprint.png)   

8. This should open up a new tab to create a Lambda function to process records

   * For 'Function name' enter 'AnnotateRetailAnalyticsData'
   * For 'Exectuion role' choose 'Create new role with basic Lambda permissions'
   
   ![Configure Lambda Firehose Processor - Part 1](/images/lab2/configure_lambda_firehose_processor_page1.png)
   
9. Scroll down further to where you see the Lambda source code. Leave it as-is (**the source code is NOT editable in this screen**) and click on 'Create function'

   ![Configure Lambda Firehose Processor - Part 2](/images/lab2/configure_lambda_firehose_processor_page2.png)  
   
10. In this next screen, you can edit the Lambda source code. 
    * For 'Runtime' select 'Node.js 8.10'.
    * And for source code, copy paste the file ```AnnotateRetailDataAnalytics.js```.
    * Take a look at the comments in the source code to clarify (just conceptually) what we're doing with this Lambda function.

    ![Configure Lambda Firehose Processor - Source Code](/images/lab2/configure_lambda_firehose_processor_source.png)        

11. Scroll down further until you reach the 'Basic Settings' section. Increase the Lambda function's 'Timeout' value to '1 min' 

    ![Increase Lambda Timeout](/images/lab2/lambda_increase_timeout.png)

    
12. Scroll back up to the very top of the page and Click on 'Save'. This button is on the top right-hand corner (again, you'll have to scroll all the way up to see it).

    ![Save Lambda](/images/lab2/lambda_save.png)


12. **OPTIONAL**: You can also test out this Lambda function by sending it a mock Firehose record to see if it processes it successfully. You can do this by clicking on the 'Test' button and configuring a test event like below:

    ```json
    {
      "invocationId": "invocationIdExample",
      "deliveryStreamArn": "arn:aws:kinesis:EXAMPLE",
      "region": "us-west-2",
      "records": [
        {
          "recordId": "49546986683135544286507457936321625675700192471156785154",
          "approximateArrivalTimestamp": 1495072949453,
          "data": "eyJDT0xfdGltZXN0YW1wIjoiMjAxOS0wOS0xOCAxMTo0OTozNi4wMDAiLCJzdG9yZV9pZCI6InN0b3JlXzQ5Iiwid29ya3N0YXRpb25faWQiOiJwb3NfMiIsIm9wZXJhdG9yX2lkIjoiY2FzaGllcl8xNDkiLCJpdGVtX2lkIjoiaXRlbV84NzU4IiwicXVhbnRpdHkiOjQsInJlZ3VsYXJfc2FsZXNfdW5pdF9wcmljZSI6MzcuMzQsInJldGFpbF9wcmljZV9tb2RpZmllciI6Mi4yMSwicmV0YWlsX2twaV9tZXRyaWMiOjc5LCJBTk9NQUxZX1NDT1JFIjowLjcyODk2NzM5NDUxNzg5MDV9Cg=="
        }
      ]
    }
    ```

13. You can now either close this browser tab where you configured the Lambda function to annotate Firehose records, or keep it open and switch back to the previous tab. 

14. In the 'Choose a Lambda blueprint', click 'close' 

    ![](/images/lab2/close_lambda_blueprint_dialog.png)
    
15. Now, in the 'Transform source records with AWS Lambda' section, click on the 'Lambda function' drop-down and choose the Lambda function that we just crreated to annotate Firehose records.

    Just in case, you don't see the function, click on the 'Refresh' button next to it to reload available Lambda functions.

    ![](/images/lab2/choose_created_lambda_firehose_processor.png)    
       
16. Click on 'Next' (scroll down a bit, if you have to)
   
17. In the 'Select a destination' page, the 'Amazon S3' option should already be selected by default. If not, choose that as the option.

   Scroll down to the 'S3 destination' section. And click on the 'Create new' button to create a new S3 bucket to store analytics data.

   ![Create S3 Destination](/images/lab2/create_s3_destination.png)


18. All S3 bucket names, regardless who or which accounts created them, need to be globally unique. Some string that is *unique to you* appended or prepended to ```retail_analytics``` should help. For example ```[COMPANY-NAME]-[SOME-UNIQUE-IDENTIFIER]-retail-analytics``` has a higher likelihood of being unique. 

   ![Create S3 Bucket](/images/lab2/create_s3_bucket_dialog.png)

19. Click on 'Create S3 Bucket'. 

20. Configure the S3 destination.

   * For the 'S3 bucket' field, the bucket that you just created should have been pre-selected.
   
   * For 'S3 prefix', enter 
   
     ```
     prod-retail-data/year=!{timestamp:yyyy}/month=!{timestamp:MM}/day=!{timestamp:dd}/hour=!{timestamp:HH}/
     ```
   
   * For 'S3 error prefix', enter
   
     ```
     prod-retail-data-errors/year=!{timestamp:yyyy}/month=!{timestamp:MM}/day=!{timestamp:dd}/hour=!{timestamp:HH}/!{firehose:error-output-type}
     ```
     
   * The above two prefix configurations allow customizing the prefixes (or the paths at which incoming data will be stored) using both static and dynamic (such as date) information. With the above configuration, we're choosing to store it using the Hive compatible partitioning format, which works well for efficient querying with Amazon Athena and Amazon EMR.  

   ![Configure S3 Destination](/images/lab2/configure_s3_destination.png)


21. Click on 'Next'. This should auto-close the tab you're on and lead you right back to the 'Kinesis Firehose - Create delivery stream' page.

22. Under 'S3 buffer conditions' section, for 'Buffer size' enter 1 and for 'Buffer interval' enter 60.

    ![S3 Buffer Configuration](/images/lab2/configure_s3_buffer.png)
    
23. Scroll down to the 'Permissions' section and for 'IAM role' click 'Create new or choose' 

    ![Create Firehose IAM Role](/images/lab2/firehose_iam_role.png)        

24. This will open up a new tab with a pre-created IAM Role and policy which you can just authorize by clicking on 'Allow'.

    ![Authorize Firehose IAM Role Creation](/images/lab2/firehose_iam_role_allow.png)

    Clicking on 'Allow' will automatically close the IAM tab and take you right back to your original tab, but now with the 'IAM role' pre-selected with the role that we just created.
    
25. Now click on 'Next'. You may need to scroll down a bit.    
    
    ![Click Next](/images/lab2/create_delivery_stream_click_next.png)
    
26. This is the final screen. Leave everything as-is, scroll down, and click on 'Create delivery stream'.

    ![Create Delivery Stream](/images/lab2/firehose_click_create_delivery_stream.png)    

28. You will first see an in-progress flash message...

    ![Firehose Create InProgress](/images/lab2/firehose_create_in_progress.png)

27. Followed by a success flash message, if all is successful.

    ![Firehose Create Success](/images/lab2/firehose_create_success.png)
    
You can now close this browser tab, or switch to the previous one (where you have the Kinesis Analytics Data application configuration open -- the browser tab that looks like the screenshot below in Step B #1)
