+++
title = "Step C - Setup Glue Crawler"
weight = 120
+++

Open a new tab in your browser and point it to https://console.aws.amazon.com/glue

1. If you see a "Splash Screen", just click 'Get Started'

   ![Get Started with Glue](/images/lab2/glue_get_started.png)

2. Click on 'Add tables using a crawler'.

   ![Add database](/images/lab2/glue_0_add_table.png)
   
3. Give this crawler a descriptive name and click 'Next'.

   ![Name the Crawler](/images/lab2/glue_1_add_crawler_info.png)
   
4. For crawler source, choose 'Data stores' (selected by default) and click 'Next'.

   ![Choose Crawler Source](/images/lab2/glue_2_specify_crawler_source.png)
   
5. Add a data store by specifying the S3 bucket name into which data is being ingested and click 'Next'.

   ![Add Data Store](/images/lab2/glue_3_add_data_store.png)  
   
6. For 'Add another data store' screen, leave the default values as-is and click 'Next'.

   ![Add Another Data Store](/images/lab2/glue_3.5_choose_another_datastore.png)   
   
7. For 'IAM role' enter a unique name and click 'Next'. 

   ![Choose IAM Role](/images/lab2/glue_4_choose_iam.png)

{{% notice note %}}   

If you're using your own AWS account, make a note of what you called this IAM role above. You'll need it when it is time to clean up.

{{% /notice %}}
   
8. For 'Frequency', leave the choice as 'Run on demand' and click on 'Next'.

   ![Schedule Crawl Frequency](/images/lab2/glue_5_crawl_scheduler.png)   
   
9. Under 'Configure the crawler's output', click on 'Add Databse'

   ![Configure Crawler Output](/images/lab2/glue_6_configure_crawl_output.png)    
   
10. In the 'Add database' dialog box, for 'Database name' enter 'retail_analytics_db' (or any name you like, but just remember to use this value when querying) and click on 'Create'

   ![Add Database](/images/lab2/glue_7_database_name.png)
   
11. Click on 'Next'

12. Click 'Finish'

    ![Finish](/images/lab2/glue_8_finish.png)    
    
13. You will see a success flash message with an option to run the newly created crawler right away. DO NOT RUN IT YET! (but, if you already clicked on it, well, no harm)
