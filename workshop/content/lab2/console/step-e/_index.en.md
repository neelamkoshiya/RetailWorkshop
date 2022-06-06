+++
title = "Step E - Query/Explore Data"
weight = 140
+++

We will now query this table from Athena to verify.

1. Open Amazon Athena by pointing your browser tab at https://console.aws.amazon.com/athena

1. If you see a splash screen, click 'Get started' 

   ![Athena Splash Screen](/images/lab2/athena_splash_screen.png)

2. Click on the 'Databases' drop-down and choose 'retail\_analytics\_db'

3. In it, you should see the table 'prod\_retail\_data'. Click on the dotted link beside it to open up multiple options.

4. Click on 'Preview table' to query it's contents.

   ![](/images/lab2/athena.png)
   
5. If this is a new AWS Account or if you've never used Amazon Athena before, this will result in an error like so:

   Click on 'set up a query result location in Amazon S3'

   ![](/images/lab2/athena_query_result_location_error.png)   
   
6. For 'Query result location' enter a unique S3 bucket.

7. Click 'Save'.

   ![](/images/lab2/athena_query_results_config.png)   
   
8. Now run the query again and it should succeed.   
   
5. Feel free to experiment by writing any Hive compatible query.   
    
   ![](/images/lab2/athena_experiment.png)
