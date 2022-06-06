+++
title = "Lab 2 - Cleanup"
weight = 300
+++

### Amazon Kinesis Data Firehose
1. Go to https://console.aws.amazon.com/kinesis
2. Click on "Delivery streams" on the left hand panel
3. Select 'RetailAnalyticsDeliveryStream' (or the name you chose) that you crated for this workshop
4. Click on "Delete" (in the top right corner)

**AWS IAM**
1. Go to https://console.aws.amazon.com/iam
2. Click on "Roles" on the left hand pane
3. Select the "firehose_delivery_role" (or whatever you named it) IAM role (use the "Search" option to narrow it down)
4. Click on "Delete" and follow the prompts

----

### Amazon S3
1. Go to https://console.aws.amazon.com/s3
2. Select the bucket that you created for this workshop (<SOMETHING>-retail-analytics)
3. Click on the "Empty" button (top right corner)
   1. Follow the prompts to empty this bucket fully
   2. Click the "Exit" button (top right corner)
4. Now click on the "Delete" button (top right corner)
   1. Follow the prompts to delete this bucket fully

----

### Amazon Lambda
1. Go to https://console.aws.amazon.com/lambda
2. Click on "Functions" in the left hand pane (unless it is already selected)
3. Select the "AnnotateRetailAnalyticsData" (or whatever you named it) function
4. Click on the "Actions" drop-down menu and click "Delete"
   1. Follow the prompts to confirm and fully delete the Lambda function.

**AWS IAM**
1. Go to https://console.aws.amazon.com/iam
2. Click on "Roles" on the left hand pane
3. Select the "AnnotateRetailAnalyticsData-role-XXXXXXXX" (or whatever you named the AnnotateRetailAnalyticsData Lambda function above)
4. Click on "Delete" and follow the prompts


