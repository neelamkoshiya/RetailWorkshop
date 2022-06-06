+++
title = "Step C - Import Data"
weight = 30
+++

We will now build the recommendation engine using Amazon Personalize. 

### Import data

We will import three types data: 1/ user interactions, 2/ items and 3/ users. 

#### Import user interaction data

1. On the aws console home page, search for personalize

![personalize](/images/lab4/step11.png)

2. Click on "Get Started"

![get started](/images/lab4/step11.png)

3. We will first begin by building the dataset group. You can name it `retail`

![dsg](/images/lab4/step12.png)

4. We will then start defining the data set for interactions. Lets name it `retail-dataset-interactions`

![interactions](/images/lab4/step13.png)

5. Below, we will select "create a new schema" radio button and copy paste the below schema. Name it retail-schema-interactions

```
{
  "type": "record",
  "name": "Interactions",
  "namespace": "com.amazonaws.personalize.schema",
  "fields": [
    {
      "name": "ITEM_ID",
      "type": "string"
    },
    {
      "name": "USER_ID",
      "type": "string"
    },
    {
      "name": "EVENT_TYPE",
      "type": "string"
    },
    {
      "name": "TIMESTAMP",
      "type": "long"
    },
    {
      "name": "DISCOUNT",
      "type": "string"
    }
  ],
  "version": "1.0"
}
```
It would look something like this:

![interactions](/images/lab4/step14.png)

Then click the next button

![interactions](/images/lab4/step15.png)

6. We will be importing the data we had uploaded in the S3 bucket. You can name the import job `retail-dataset-interactions-import`

![interactions](/images/lab4/step16.png)

7. For the IAM role, you can select create a new role, this would pop out a window and you can select Any bucket radio button

![import](/images/lab4/step17.png)

![import](/images/lab4/step17.1.png)

![import](/images/lab4/step18.png)

8. Once the IAM role is created, you can put in the data location of the interaction files and click "Finish"

![import](/images/lab4/step19.png)

9. You will be routed to the dashboard and we can now begin to import the users and item files

![import](/images/lab4/step20.png)




#### Import items data

1. From the dashboard, click on import item data. You can provide the name for the data set `retail-dataset-items`

![import](/images/lab4/step21.png)

2. You can click to create a new schema. Name it `retail-dataset-items-schema`

```
{
  "type": "record",
  "name": "Items",
  "namespace": "com.amazonaws.personalize.schema",
    "fields": [
    {
    "name": "ITEM_ID",
    "type": "string"
    },
    {
    "name": "CATEGORY",
    "type": "string",
    "categorical": true
    },
    {
    "name": "STYLE",
    "type": "string",
    "categorical": true
    }
  ],
  "version": "1.0"
}
```
Click next

![import](/images/lab4/step22.png)

3. Define the import job to import the items data. Name it `retail-dataset-items`. Select the IAM role you had just created. Fill in the data destination pointing to item.csv in your s3 bucket

![import](/images/lab4/step23.png)

#### Import users data

1. From the dashboard, select import user. You will be routed to this page where you can feed in the dataset name as `retail-dataset-users`

Click the radio button for create a new schema and copy and paste the below snippet
```
{
  "type": "record",
  "name": "Users",
  "namespace": "com.amazonaws.personalize.schema",
    "fields": [
    {
    "name": "USER_ID",
    "type": "string"
    },
    {
    "name": "AGE",
    "type": "int"
    },
    {
    "name": "GENDER",
    "type": "string",
    "categorical": true
    }
  ],
  "version": "1.0"
}
```
And then click next

![import](/images/lab4/step24.png)

2. Next, we will be defining the import job to import the user data. Name the import job `retail-dataset-users-import` and select the IAM role we had created previously. Fill in the location of you users.csv file in the data destination

![import](/images/lab4/step25.png)

