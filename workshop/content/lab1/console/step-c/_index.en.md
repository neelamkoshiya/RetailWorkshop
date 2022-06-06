+++
title = "Step C - Create Analytics App"
weight = 30
+++

We will now create an Amazon Kinesis Data Analytics App (SQL-based) that we will connect to the above Kinesis Data Stream to allow us to *process* the data we are ingesting.

1. Click on 'Data Analytics' in the left hand tab. 
   
   ![Kinesis Analytics](/images/lab1/kinesis_analytics_tab.png)   

2. You may see either the screen above or the one below, depending on whether or not you have already created an analytics app in the past.

   Click on 'Create Kinesis stream' or 'Create application' depending on the screen.

   ![Kinesis Analytics Splash](/images/lab1/kinesis_analytics_get_started.png)
   
   
   
2. For 'Application name', enter something descriptive. The 'Description' is optional. Leave the rest of the options as-is.

3. Then click on 'Create application'

   ![Create Kinesis Analytics App](/images/lab1/create_analytics_app.png)    
   
3. Click on 'Connect streaming data' to connect the Kinesis Data Stream we created in Step A with the Kinesis Data Analytics application.

   ![Connect Data Stream to Analytics App](/images/lab1/connect_streaming_data.png)
   
4. For the 'Kinesis data stream' drop-down, choose the Kinesis Data Stream name that we just created 

   ![Choose data stream page1](/images/lab1/connect_streaming_data_page1.png)   
   
5. Scroll down until you see this and click on 'Discover schema'

   ![Choose data stream page2](/images/lab1/connect_streaming_data_page2.png)   
   
6. Now look at the discovered schema, the column names, and associated data types. You'll notice that Kinesis Data Analytics has automatically discovered most of the schema types correctly. *Except* one. The very first column, ```COL_timestamp``` has been classified as ```VARCHAR``` instead of ```TIMESTAMP```. We deliberately introduced an uncommon ```TIMESTAMP``` format to trip it. However, this is easy to fix.
   
7. To fix the schema, click on the 'Edit schema' button. 

   ![Discover Schema](/images/lab1/connect_streaming_data_schema.png)

7. Update ```COL_timestamp```'s 'Column type' value to ```TIMESTAMP``` from the drop-down options.
   
   ![Edit Schema](/images/lab1/edit_schema.png)
   
8. Click on 'Save schema and update stream samples'. This will take around 10 - 15 seconds, but once complete, and the stream samples are updated, scroll down and you will notice the corrected schema as shown:

   ![Edited Schema](/images/lab1/edited_schema.png)   
   
9. Click on 'Exit (done)' to exit the screen

   ![Exit Schema Edit](/images/lab1/exit_schema_update.png)
