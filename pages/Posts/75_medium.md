---
title: 75 Medium Challenge
---


## 75 Medium Challenge: Starting January 2025


Tracking challenge for 75 medium: completing each following daily activities:
- 45 minute workout
- Drinking 1 gallon of water
- Reading 10 pages of a book


Are we on track?

```sql activities_by_date
select 
date_dt,
--count(*) as activity_count,
sum(activity_hours) as activity_hours
from strava_bq.strava_log
where date_dt between  '2025-01-01' and '2025-03-01'
group by all
order by 1
```

<LineChart data={activities_by_date} x=date_dt y=activity_hours yAxisTitle="Daily Activity Hours">
    <ReferenceLine y=0.75 label="45 Daily Target"/>
</LineChart>
