+++
title = "Step C - Import Data"
weight = "40"
+++

We will now import data target timeseries dataset that we just defined

1. Before we import the target timeseries dataset, we'll need to upload the ```retail_analytics.csv``` to an Amazon S3 bucket that Amazon Forecast can access and get the dataset from.

2. Switch your browser tab back to the one where you have Cloud9 open.


3. All S3 bucket names, regardless who created them, need to be globally unique. So choose something *unique to you* and append or prepend it to ```retail-forecast``` such as ```sudoamit-retail-forecast```.

   From the Cloud9 terminal window run the below after replacing BUCKET_NAME with some unique name that you came up with for your S3 bucket. 
   
   
   ```shell
   cd lab3/src
   ```
      
   ```shell
   aws s3 mb s3://[SOME_UNIQUE_NAME]-retail-forecast
   ```
   
   ```shell
   aws s3 cp retail_analytics.csv s3://[SOME_UNIQUE_NAME]-retail-forecast/
   ```
   
   <br/> 
    
2. Switch back to the browser tab where you have Amazon Forecast open to pick up where we left off. The console should now be in the 'Import target time series dataset' screen.     

3. Enter a descriptive name for 'Dataset import name'.

4. Leave the 'Timestamp format' as-is.
 
   ![Import Target Timeseries Dataset](/images/lab3/import_target_timeseries_dataset.png)


5. For 'IAM Role', click on drop-down and choose

   ![Choose Create IAM Role](/images/lab3/forecast_choose_create_role.png)
   
6. Click on 'Create role'

   ![Create IAM Role](/images/lab3/forecast_create_role.png)   


6. For 'Data location' copy and paste the S3 bucket name that you created earlier like so: ```s3://[SOME_UNIQUE_NAME]-retail-forecast/retail_analytics.csv```

   ![S3 Data](/images/lab3/forecast_s3_data.png)


7. Click on 'Start Import'. If all is successful, you should see a flash message like so:

   ![Import Target Timeseries Success](/images/lab3/import_target_timeseries_success.png)

   This should take around 2 mins. Refresh the browser a few times to see if it is complete.
