+++
title = "Event Engine"
chapter = true
weight = 10
pre = "1. "
+++


If you're building this workshop as part of a workshop event, we will use the purpose-built Event Engine to provision free AWS accounts that you can use for the duration of the workshop. 

However, if you're using your own personal (or company) AWS account, you can skip this step and move to Cloud9 IDE setup.

Head over to https://dashboard.eventengine.run.

1. Enter your participant hash and go to the next screen

   ![Event Engine Dashboard](/images/event_engine_dashboard.png)
   
2. Click on 'AWS Console'

   ![Event Engine AWS Console](/images/event_engine_aws_console.png)
   
3. Copy-paste the Credential values into a Notepad so you have them for later. Specifically,
   * ```AWS_ACCESS_KEY_ID```
   * ```AWS_SECRET_ACCESS_KEY```
   * ```AWS_SESSION_TOKEN```

   We will refer to these interchangeably as ```AWS_ACCESS_KEY_ID``` or ```ACCESS_KEY_ID```. And as ```AWS_SECRET_ACCESS_KEY``` or ```SECRET_ACCESS_KEY```. And as ```AWS_SESSION_TOKEN``` or ```SESSION_TOKEN```.

   ![](/images/event_engine_console_login.png)   


### Regions

As of this writing, Amazon Forecast is supported in 6 regions (below), **but the accounts provided in this Workshop default to Oregon.**

{{% notice note %}}

If you're using your own account, we still recommended sticking with `us-west-2` (script in lab1 uses `us-west-2`), but if you're keen on another region and comfortable replacing `us-west-2` in the script with the region of your preference, feel free to choose any of the supported regions below.

{{% /notice %}}

If you're working through these steps as part of a workshop event, we strongly recommend using the free AWS account provided to you for this workshop and then perhaps work thru' the labs *again* in your own AWS account after this workshop to reinforce. 

The free AWS accounts made available via Event Engine, however, are only for the duration of this workshop and will be shutdown shortly after. 

Region Name              | Region 
-------------------------|--------
US East (Ohio)           | us-east-2
US East (N. Virginia)    | us-east-1
US West (Oregon)         | us-west-2
Asia Pacific (Singapore) |	ap-southeast-1
Asia Pacific (Tokyo)     | ap-northeast-1
EU (Ireland)             | eu-west-1
