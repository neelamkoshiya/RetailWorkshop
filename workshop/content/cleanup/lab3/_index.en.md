+++
title = "Lab 3 - Cleanup"
weight = 400
+++


### AWS Glue
1. Go to https://console.aws.amazon.com/glue
2. Click on "Tables" in the left hand pane
3. Select the "prod_retail_data" (or whatever you named it) table
4. Click on the "Action" drop-down and click on "Delete table"
   1. Follow the prompts to confirm and fully delete the table
5. Click on "Databases" in the left hand pane
6. Select "retail_analytics_db" (or whatever you named it) database 
7. Click on the "Action" drop-down and click on "Delete database"
   1. Follow the prompts to confirm and fully delete the database
8. Click on "Crawlers" in the left hand pane
9. Select "RetailAnalyticsCrawler" (or whatever you named it)
10. Click on the "Action" drop-down and click on "Delete crawler"
   1. Follow the prompts to confirm and fully delete the crawler

**AWS IAM**
1. Go to https://console.aws.amazon.com/iam
2. Click on "Roles" in the left hand pane
3. Select "AWSGlueServiceRole-SOME_UNIQUE_IDENTIFIER" (whatever you called this unique identifier)
4. Click on "Delete" and follow the prompts

----

### Amazon Forecast
1. Go to https://console.aws.amazon.com/forecast
2. Click on "View dataset groups"
3. Select "RetailForecast" 
4. Click on "Delete" 
   1. Follow the prompts to delete fully
