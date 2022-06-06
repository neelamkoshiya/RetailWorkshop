+++
title = "Step D - Train Predictor"
weight = 50
+++

We'll now train a Predictor on this dataset that we just imported.


1. Click on 'Start' under 'Train a predictor' (in the middle column)

   ![Train Predictor](/images/lab3/train_predictor.png)
   
2. Enter something descriptive for 'Predictor name'
 
3. For 'Forecast horizon' enter 30 days (we'll attempt to predict demand over the next 30 days)

4. For 'Forecast frequency' enter '1' in the first drop down and 'day' in the second. Our forecast frequency will be daily.

5. For 'Algorithm selection', choose the 'Automatic' option. Amazon Forecast will make the best decision and choose among the available forecasting algorithms. 

   Forecast supports 5 algorithms, ARIMA, DeepAR+, ETS, NPTS, and Prophet. You can read more about these algorithms here https://docs.aws.amazon.com/forecast/latest/dg/aws-forecast-choosing-recipes.html

6. For 'Forecast dimensions', click the drop-down and choose 'Location'

   ![](/images/lab3/forecast_choose_dimensions.png)
   
7. **OPTIONAL** We're not assuming any holidays in this simulation, so you can choose to leave the 'Country for holidays' blank.   
   
   The final choices should have the Train predictor screen looking something like this:

   ![Predictor Details](/images/lab3/predictor_details.png)   

   
7. Click on 'Train Predictor'. If all succeeds, you will see a screen that shows training is in progress

   ![Predictor Training In-progress](/images/lab3/predictor_training_inprogress.png)
