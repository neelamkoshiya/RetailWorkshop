+++
title = "Step A - Create Stream"
weight = 10
+++

1. Point browser to https://console.aws.amazon.com/kinesis

   Note the region that you are defaulted to, which in the case of the screenshot below is 'Oregon'. Any of the regions that you prefer where Amazon Forecast is supported is fine, so long as you ensure that you remain within that region across all labs.
   
   ![Default Region](/images/lab1/kinesis_region.png)
   
1. Click on 'Get Started'

   ![Get Started with Kinesis](/images/lab1/kinesis_get_started.png)
   
1. Click on 'Create data stream'

   ![Create Data Stream](/images/lab1/kinesis_create_data_stream.png)   

2. For 'Kinesis stream name', give it a descriptive name such as 'RetailDataStream' for example. (note the restrictions in what characters can be used for the name right below the textbox).

   {{% notice note %}}

   You're free to name this stream anything you prefer, but if you change it, be sure to also change line no. 5 in the ```gen_pos_log_stream.rb``` script in the ```/src``` directory and use the same name for ```STREAM_NAME```
   
   {{% /notice %}}
   
   ```
   STREAM_NAME = 'RetailDataStream'
   ```

3. For 'Number of shards*' enter '2'

   ![Create Streams](/images/lab1/create_streams.png)
   
3. Click 'Create Kinesis Streams'. This will take around 10 to 15 seconds after which, the Kinesis Data Stream should have been created. You should see a success message like this:

   ![Stream Creation Success](/images/lab1/data_stream_created.png)
   
   We have successfully created a Amazon Kinesis Stream resource that can ingest our data.




