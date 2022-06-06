+++
title = "Step B - Stream Data"
weight = 20
+++

Since we've created the Kinesis Data Stream to which we can send data to, we'll start running our simulation script that generates the PoS data and send that data to the stream that we just created.

To run this script, switch to the browser tab where you have the Cloud9 IDE open. Go to the Cloud9 IDE terminal and run:

```shell
cd ~/environment/retail/lab1/src
```

```shell
gem install bundler
```

```shell
bundle install
```

```shell
mkdir config
touch config/aws.yml
```

Replace ```ACCESS_KEY_ID```, ```SECRET_ACCESS_KEY```, and ```SESSION_TOKEN``` with what you copied into your notepad at the beginning and then run:

{{% notice info %}}

The whitespace after each of the colons `:` below is critical, so preserve the whitespace after the colon when you copy-paste each of the values. Otherwise, it isn't valid YAML syntax and the script will fail to parse the values.

{{% /notice %}}

```shell
echo "access_key_id: ACCESS_KEY_ID" >> config/aws.yml
echo "secret_access_key: SECRET_ACCESS_KEY" >> config/aws.yml
echo "session_token: SESSION_TOKEN" >> config/aws.yml
```

{{% notice warning %}}

Did you remember to replace ```ACCESS_KEY_ID```, ```SECRET_ACCESS_KEY```, and ```SESSION_TOKEN``` above? And preserve the whitespace after the `:`?

{{% /notice %}}

{{% notice tip %}}

**OPTIONAL**: If you're using the AWS account provided via Event Engine, ignore this. But if you're running in your own account and selected a different region, make sure you edit the script and change `us-west-2` on line 15 to the region you prefer.

{{% /notice %}}

As mentioned earlier, the ```gen_pos_log_stream.rb``` script artificially introduces anomalous values for the KPI metric. Most values are between 80 - 95, but some values are below 10 (we inject these anomalous values about 3% of the time).


Execute the script by running:


```shell
ruby gen_pos_log_stream.rb
```

Wait for the script to start running and then switch back to the AWS console to continue with the steps below.



