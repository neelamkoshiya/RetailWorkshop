+++
title = "Step F - Further Processing"
weight = 150
+++

Now we'll slightly modify the streaming SQL we just wrote in the previous step and compare the results.

1. Now copy the streaming SQL in ```retail_pos_analytics_multicolumn_attributions.sql``` into the same SQL Editor as you did before. The SQL statements are also included below for convenience.

   ```sql
    CREATE OR REPLACE STREAM "RETAIL_KPI_ANOMALY_DETECTION_STREAM" (
      "store_id"                    varchar(8),
      "workstation_id"              varchar(8),
      "operator_id"                 varchar(16),
      "item_id"                     varchar(16),
      "quantity"                    integer,
      "regular_sales_unit_price"    real,
      "retail_price_modifier"       real,
      "retail_kpi_metric"           integer,
      "ANOMALY_SCORE"               double,
      "ANOMALY_EXPLANATION"         varchar(512)
    );
    
    -- Compute an anomaly score for each record in the input stream
    CREATE OR REPLACE PUMP "RETAIL_KPI_ANOMALY_DETECTION_STREAM_PUMP" AS
    INSERT INTO "RETAIL_KPI_ANOMALY_DETECTION_STREAM"
      SELECT STREAM "store_id",
                    "workstation_id",
                    "operator_id",
                    "item_id",
                    "quantity",
                    "regular_sales_unit_price",
                    "retail_price_modifier",
                    "retail_kpi_metric",
                    ANOMALY_SCORE,
                    ANOMALY_EXPLANATION
      FROM TABLE(RANDOM_CUT_FOREST_WITH_EXPLANATION (
                     CURSOR( SELECT STREAM "store_id",
                                           "workstation_id",
                                           "operator_id",
                                           "item_id",
                                           "quantity",
                                           "regular_sales_unit_price",
                                           "retail_price_modifier",
                                           "retail_kpi_metric"
                             FROM "SOURCE_SQL_STREAM_001"), 100, 256, 100000, 1, false)
      );
    
    
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
      -- "ANOMALY_EXPLANATION"         varchar(512),
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
      -- "ANOMALY_STREAM"."ANOMALY_EXPLANATION"
      FROM "SOURCE_SQL_STREAM_001" AS "SOURCE_STREAM"
        JOIN "RETAIL_KPI_ANOMALY_DETECTION_STREAM" AS "ANOMALY_STREAM"
          ON  "SOURCE_STREAM"."store_id"       = "ANOMALY_STREAM"."store_id"
              AND "SOURCE_STREAM"."workstation_id" = "ANOMALY_STREAM"."workstation_id"
              AND "SOURCE_STREAM"."operator_id"    = "ANOMALY_STREAM"."operator_id"
              AND "SOURCE_STREAM"."item_id"        = "ANOMALY_STREAM"."item_id";

   ```
   
   ![Edited SQL](/images/lab1/sql_editor.png)
   
2. Click on 'Save and run SQL' and wait for the analytics application to update the stream.

3. Once the data starts flowing, click on the ```RETAIL_KPI_ANOMALY_DETECTION_STREAM``` and wait a seconds for the data to start flowing again.

   ![In-Application Stream](/images/lab1/in_application_streams.png)


4. Now scroll again all the way to the right until you see the ```ANOMALY_SCORE``` and ```ANOMALY_EXPLANATION``` columns. Notice more values in the ```ANOMALY_EXPLANATION``` column than before?

   {{% notice note %}}

   **Results Explained**  
   In the ```ANOMALY_EXPLANATION``` column, in addition to ```retail_kpi_metric```, you'll also notice the presence of ```quantity```,```retail_price_modifier```, and ```regular_sales_unit_price``` metrics. The algorithm is now using all of these numeric values to determine the anomaly score of a record. In this way, you get to cherry pick the metrics data that you think are most relevant and want the algorithm to score. 

   {{% /notice %}}
