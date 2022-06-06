+++
title = "Step B - Training Data"
weight = 20
+++


## Upload training data
Now that we have created our bucket, lets upload training data which will be used for training a model. 

The training data would consists of three files - items , users and item- user interactions. Remember this is test data and can be changed per your own requirement and usecase.

1. Interaction Data:  Make sure you have downloaded the interactions test data from here [interactions.zip](/testdata/interactions.zip). Rememeber to unzip the interactions zip. 

2. Items Data: Make sure you have downloaded the items test data from here [items.csv](/testdata/items.csv). 

3. Users Data: Make sure you have downloaded the users test data from here [users.csv](/testdata/users.csv). 


## Understanding Data

#### Interactions Data

| ITEM_ID  | USER_ID |EVENT_TYPE |TIMESTAMP | 	DISCOUNT |
| ------------- | ------------- |------------- |------------- |------------- |
| 1  | 3156  | ProductViewed |1591803788|	No       |


#### Items Data

| ITEM_ID  | CATEGORY |STYLE |
| ------------- | ------------- |------------- |
| 63  | beauty  | makeup |


#### User Data

| ITEM_ID  | AGE |GENDER |
| ------------- | ------------- |------------- |
| 1  | 31  | M |
