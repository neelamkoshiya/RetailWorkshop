+++
title = "Console / GUI"
weight = 20
+++


## Summary

Here is the internal workflow of Personalize


![Personalize](/images/lab4/personalizehowitworks.png )




The workflow for training, deploying, and getting recommendations from a campaign is:

 1) Create related datasets and a dataset group.

 2) Get training data.

 3) Import historical data to the dataset group.

 4) Record user events to the dataset group.

 5) Create a solution version (trained model) using a recipe.

 6) Evaluate the solution version using metrics.

 7) Create a campaign (deploy the solution version).

 8) Provide recommendations for users.




We are going to work on this lab by using AWS console

Here are the lab steps:

[Step A: Create S3 bucket and set the bucket policy]({{% relref "lab4/console/step-a" %}})

[Step B: Upload training data]({{% relref "lab4/console/step-b" %}})

[Step C: Get started with Amazon Personalize]({{% relref "lab4/console/step-c" %}})

[Step D: Create Solution]({{% relref "lab4/console/step-d" %}})

[Step E: Create Campaign]({{% relref "lab4/console/step-e" %}})

[Step F: Test and get the recommendation!]({{% relref "lab4/console/step-f" %}})

