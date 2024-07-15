# Website Traffic Analysis

This repository contains example data collected from a simulated website traffic analysis using AWS CloudWatch.

## Data Files

- `traffic_data.csv`: Contains the traffic data collected and exported from CloudWatch Logs Insights.

## Queries Used

The following queries were used to collect the data:

### Requests Per Hour
```sql
fields @timestamp, @message
| parse @message "* - - [*:*:*:*:*] * * *" as ip, date, time, request, status, size, referrer, agent
| stats count(*) as requestCount by bin(1h)
