+++ 
title = "Run Code - Optional"
weight = 30
+++

While you can directly use the pre-generated ```retail_analytics.csv``` file to generate forecasts, you can also modify the ```gen_aggregate_pos_data.rb``` Ruby script (or  ```gen_aggregate_pos_data.py``` in Python)  that generates this file and modify it to generate a new ```retail_analytics.csv``` file to see differences in forecast based on changes you made. 

To run this code:

cd into the ```lab3``` directory

```shell
$ cd lab3
```

install bundler (which is used to install ruby dependencies)

```shell
$ gem install bundler
```

then install dependencies

```shell
$ bundle install
```

and run the script like so...

```shell
$ ruby gen_aggregate_pos_data.rb
```
