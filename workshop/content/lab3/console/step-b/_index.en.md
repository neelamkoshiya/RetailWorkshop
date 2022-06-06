+++
title = "Step B - Configure Schema"
weight = "30"
+++

Now we'll create and define the schema the dataset that we'll base forecasts on. The RETAIL domain supports 3 dataset types, TARGET\_TIME\_SERIES, RELATED\_TIME\_SERIES, and ITEM\_METADATA.

TARGT\_TIME\_SERIES is the **core** dataset that has the feature (column) whose value we're trying to forecast. The other two are **optional** and can help add peripheral information (weather, color, etc.) for more accurate forecasts.

1. Enter a name for the dataset against 'Dataset Name'. For example ```JulyToSeptemberSales```.

2. For 'Frequency of your data' dropdowns, leave the first at '1' and choose 'hour' for the second.

3. For 'Data schema', copy and paste the below:
   
   This schema matches the aggregated dataset we generated in ```retail_analytics.csv```.    

    ```json
    {
    	"Attributes": [
    		{
    			"AttributeName": "timestamp",
    			"AttributeType": "timestamp"
    		},
    		{
    			"AttributeName": "item_id",
    			"AttributeType": "string"
    		},
    		{
    			"AttributeName": "demand",
    			"AttributeType": "float"
    		},
    		{
    			"AttributeName": "location",
    			"AttributeType": "string"
    		}
    	]
    }
    ```

   
4. Now click 'Next'.   

   ![Create Dataset](/images/lab3/create_target_timeseries_dataset.png)
