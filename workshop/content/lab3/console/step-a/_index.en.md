+++
title = "Step A - Forecast"
weight = 20
+++

### Regions

If you're using an AWS account vended by the Event Engine for this lab, you will be in `us-west-2`. This is displayed as "Oregon" in the top right-hand corner of the AWS console and is referred to as ```us-west-2``` when using the CLI or API.

If you're using one of your own AWS accounts, please note the region that you created your Cloud9 IDE console in and remain within that region.

### Step A

1. In the same browser window that you have the Cloud9 IDE open, open up a new browser tab and point it to https://console.aws.amazon.com/forecast. On the top right-hand corner of the console, note the region you're in. This will typically look like this:

   ![Region Selection](/images/lab3/region_selection.png)
   
2. Click on 'Create dataset group'. If you've already used Amazon Forecast before, it may be called 'View dataset groups'

   ![Create Dataset Group 1](/images/lab3/forecast_create_dataset_group1.png)

2. We'll first give this dataset group a name. Against 'Dataset group name' enter something descriptive.

3. For 'Forecasting domain', choose 'Retail'.

4. Click 'Next'.

   ![Create Dataset Group 2](/images/lab3/create_dataset_group.png)
