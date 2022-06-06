+++
title = "Step B - Configure Analytics App"
weight = 110
+++

We have successfully configured a Kinesis Data Firehose Delivery Stream and we're now going to configure our Kinesis Data Analytics  to use this as its destination.

1. For 'Kinesis Firehose delivery stream', ensure that the 'Retail Analytics Delivery Stream' is selected.

   ![Choose Firehose Delivery Stream](/images/lab2/choose_firehose_delivery_stream.png)
   
2. Scroll down to the 'In-application Stream' section and for 'In-application stream name', choose 'DESTINATION_STREAM' (the stream we created via Streaming SQL in Step E #1 and Step F #1 of Lab 1)

   ![Choose In-Application Stream](/images/lab2/choose_in_application_stream.png)

3. Click on 'Save and continue'. This might take a few 10 seconds.

4. Click on 'Go to SQL results'

   ![Go to SQL Results](/images/lab2/go_to_sql_results_2.png)

5. **CONDITIONAL Step** Check that your script is still running in Cloud9. If not, run it now.

   ```shell
   cd ~/environment/retail/lab1/src
   ```
   
   ```shell
   ruby gen_pos_log_stream.rb
   ```   
   
   Wait for the script to start...
   
   
6. Open up another browser tab and point it to https://console.aws.amazon.com/s3 and navigate to the bucket that you created. Click into this bucket and wait at least a minute (since we configured Kinesis Firehose's buffer as 60 seconds or 1 MB -- whichever is hit first) and refresh again. You should now see this bucket start to fill up with data.

   ![Data in S3](/images/lab2/s3_data.png)
