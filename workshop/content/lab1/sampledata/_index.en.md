+++
title = "Sample Data"
weight = 10
+++

{{% notice note %}}
**A note on the KPI metric**  
The ```retail_kpi``` column is meant to be some (any) calculated value that makes sense for your business that you want to maximize (or minimize). You can certainly define multiple such KPIs (Key Performance Indicators). 
{{% /notice %}}

What we're doing when simulating this data, is artificially introducing anomalous values for this KPI. Most values are between 80 - 95, while some values are below 10 (about 3% of the time), so it is easy to spot just glancing at it for the purposes of this lab.



| COL_timestamp | store id | workstation id | operator id | item id | quantity | regular sales unit price | retail price modifier | retail kpi metric |
|--------------|-----------|-----------------|--------------|----------|----------|-----------------------------|-----------------------|------------------------|
2019-08-31T10:40:05.0 | store_36 | pos_2  | cashier_75  | item_1098 | 5 | 64.42 | 5.83 | 87  
2019-09-27T17:12:33.0 | store_43 | pos_10 | cashier_175 | item_4159 | 5 | 50.25 | 7.68 | 85
...                   | ...      | ...    | ...         | ...       |...|...| ... | ... |

