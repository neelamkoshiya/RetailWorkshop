+++
title = "Step E - Process Data"
weight = 50
+++ 

Here, we'll add some streaming SQL to process ingested PoS data on the fly. We'll experiment with two different streaming SQL statements
  
 
1. For our first experiment, copy the streaming SQL from the file ```retail_pos_analytics_kpi_attribution.sql``` into the SQL editor window. The SQL is also provided here for convenience

   ```sql
    --
    -- Creates a stream with a subset of the data that we are ingesting,
    -- which is our way of ensuring that we only run anomaly detection on
    -- the numeric columns that we pick.
    --
    CREATE OR REPLACE STREAM "RETAIL_KPI_ANOMALY_DETECTION_STREAM" (
      "store_id"              varchar(8),
      "workstation_id"        varchar(8),
      "operator_id"           varchar(16),
      "item_id"               varchar(16),
      "retail_kpi_metric"     integer,
      "ANOMALY_SCORE"         double,
      "ANOMALY_EXPLANATION"   varchar(512)
    );
    
    --
    -- Compute an anomaly score for each record in the input stream. The
    -- anomaly detection algorithm considers ALL numeric columns and
    -- ignores the rest.
    --
    CREATE OR REPLACE PUMP "RETAIL_KPI_ANOMALY_DETECTION_STREAM_PUMP" AS
    INSERT INTO "RETAIL_KPI_ANOMALY_DETECTION_STREAM"
      SELECT STREAM "store_id",
                    "workstation_id",
                    "operator_id",
                    "item_id",
                    "retail_kpi_metric",
                    ANOMALY_SCORE,
                    ANOMALY_EXPLANATION
      FROM TABLE(RANDOM_CUT_FOREST_WITH_EXPLANATION (
                     CURSOR( SELECT STREAM "store_id",
                                            "workstation_id",
                                            "operator_id",
                                            "item_id",
                                            "retail_kpi_metric"
                             FROM "SOURCE_SQL_STREAM_001"), 100, 256, 100000, 1, false)
      );
    
    --
    -- Create a destination stream that combines (JOINs) all the values in
    -- the source stream along with the anomaly values in the anomaly stream
    -- which we will then store for historic records.
    --
    CREATE OR REPLACE STREAM "DESTINATION_STREAM" (
      "COL_timestamp"               timestamp,
      "store_id"                    varchar(8),
      "workstation_id"              varchar(8),
      "operator_id"                 varchar(16),
      "item_id"                     varchar(16),
      "quantity"                    integer,
      "regular_sales_unit_price"    real,
      "retail_price_modifier"       real,
      "retail_kpi_metric"           integer,
      "ANOMALY_SCORE"               double
      --"ANOMALY_EXPLANATION"         varchar(512)
    );
    
    CREATE OR REPLACE PUMP "DESTINATION_STREAM_PUMP" AS
    INSERT INTO "DESTINATION_STREAM"
      SELECT STREAM "SOURCE_STREAM"."COL_timestamp",
                    "SOURCE_STREAM"."store_id",
                    "SOURCE_STREAM"."workstation_id",
                    "SOURCE_STREAM"."operator_id",
                    "SOURCE_STREAM"."item_id",
                    "SOURCE_STREAM"."quantity",
                    "SOURCE_STREAM"."regular_sales_unit_price",
                    "SOURCE_STREAM"."retail_price_modifier",
                    "SOURCE_STREAM"."retail_kpi_metric",
                    "ANOMALY_STREAM"."ANOMALY_SCORE"
                    --"ANOMALY_STREAM"."ANOMALY_EXPLANATION"
      FROM "SOURCE_SQL_STREAM_001" AS "SOURCE_STREAM"
      JOIN "RETAIL_KPI_ANOMALY_DETECTION_STREAM" AS "ANOMALY_STREAM"
        ON  "SOURCE_STREAM"."store_id"       = "ANOMALY_STREAM"."store_id"
        AND "SOURCE_STREAM"."workstation_id" = "ANOMALY_STREAM"."workstation_id"
        AND "SOURCE_STREAM"."operator_id"    = "ANOMALY_STREAM"."operator_id"
        AND "SOURCE_STREAM"."item_id"        = "ANOMALY_STREAM"."item_id";

   ```

   Paste the above SQL into the SQL editor window.
   
   
2. Click on 'Save and run SQL' button. 

   ![Edited SQL](/images/lab1/sql_editor.png)
   
   You will need to wait for a few 10 seconds for the results to start streaming. While waiting for this to update...
   
   {{% notice note %}}
      
   **Useful Terms**: It might also be helpful to understand the simple concepts of a STREAM and a PUMP.<br/><br/>
   **STREAM**: An *in-application* stream works like a table that you can query using SQL statements, but it's called a stream because it represents continuous data flow.<br/><br/>
   **PUMP**: A pump is a continuously running insert query that inserts data from one *in-application* stream to another *in-application* stream.

   {{% /notice %}}
   
   See the docs here for a more detailed explanation of these concepts: https://docs.aws.amazon.com/kinesisanalytics/latest/dev/streaming-sql-concepts.html


3. Once the results start streaming in, under the 'Source' and 'Real-time analytics' tab, you will notice multiple streams. 
   
   1. ```SOURCE_SQL_STREAM_001``` - This is the raw source data. You will see this under the 'Source' tabs. 
   2. ```RETAIL_KPI_ANOMALY_DETECTION_STREAM``` - This is the stream with anomaly scores. You will see this under the 'Real-time analytics' tabs. 
   3. ```DESTINATION_STREAM``` - This is the raw source data ```JOIN```ed with anomaly scores to store in Amazon S3 for historical analysis. You will see this under the 'Real-time analytics' tabs. 
   
   
4. Under 'In-application streams' click on the ```RETAIL_KPI_ANOMALY_DETECTION_STREAM``` and wait a few seconds for the data to start flowing.

   ![In-Application Stream](/images/lab1/in_application_streams.png)


5. Scroll to the right until you reach the ```ANOMALY_SCORE``` column. 

   {{% notice note %}}

   **Results Explained**   
   You'll notice floating point values. What these values mean are that, the algorithm considers records with higher ```ANOMALY_SCORE```s as *more anomalous*.
   
   {{% /notice %}} 

   ![Anomaly Scores](/images/lab1/anomaly_score.png)

6. Look further to the right of this and you'll see the ```ANOMALY_EXPLANATION``` column adjacent to it. Notice the values in this (JSON formatted) column. 

   {{% notice note %}}
   
   **Results Explained**  
   In the ```ANOMALY_EXPLANATION``` column, you'll see ```retail_kpi_metric``` being called out with an associated ```ATTRIBUTION_SCORE```. This is the algorithm's way of indicating the extent to which this column contributed to the anomaly score.
   
   {{% /notice %}}
   
   ![Attribution Scores](/images/lab1/kpi_attribution.png)   

