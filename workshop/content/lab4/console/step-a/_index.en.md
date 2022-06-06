+++
title = "Step A - Create S3 Bucket"
weight = 10
+++

## Create S3 bucket and set bucket policy

### Create S3 bucket

1. Search S3 in the AWS console. 

![s3](/images/lab4/step1.png)

2. Once you are on the landing page for S3, click on "Create Bucket" button on the right side of the page

![Create bucket](/images/lab4/step2.png)

3. Bucket name needs to be unique globally. I would suggest personalize-demo-firstnamelastname. Remember to replace firstnamelastname with your own names 

![Bucket details](/images/lab4/step3.png)

Rest of the details you can keep as it is and hit "create bucket" at the bottom of the page

![Bucket details](/images/lab4/step4.png)

You will redirected to landing page, and you should be able to see the bucket created.

![Bucket details](/images/lab4/step5.png)

### Set bucket policy  

In order for the personalize service to access this bucket data, we will have to set the bucket policy

1. Click on the Permission tab in the bucket 

![Bucket details](/images/lab4/bucketpolicystep1.png)

2. Scroll down to bucket policy and click the below snippet to add it. Remember to replace the bucket name(bucket-name) with your bucket

```
{
    "Version": "2012-10-17",
    "Id": "PersonalizeS3BucketAccessPolicy",
    "Statement": [
        {
            "Sid": "PersonalizeS3BucketAccessPolicy",
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::bucket-name",
                "arn:aws:s3:::bucket-name/*"
            ]
        }
    ]
}
```

![Bucket details](/images/lab4/bucketpolicystep2.png)

