---
title: Activity Log
hide_title: false
fullWidth: true
---

<img src="https://avatars.githubusercontent.com/zachrenwick" alt="Zach" class="rounded-full w-24 h-24 mb-4">

## Logging Exercise with Strava


This page is a future home of activity analytics. Shows how you can visualize your strava data.



```sql sports_count
select 
modified_sport,
count(*) as activity_count
from strava.strava_log
group by all
order by activity_count desc

```

<!-- 4. Add a DataTable component that includes conditional formatting for the case count column (see https://docs.evidence.dev/components/data-table/#conditional-formatting) -->

<BarChart 
    data={sports_count}
    x=modified_sport
    y=activity_count
/>



```sql activities_over_time
select 
week_index,
year(date_dt) as year_dt,
month(date_dt) as month_dt,
concat(year_dt, month_dt) as year_month,
count(*) as activity_count,
sum(activity_hours) as activity_hours
from strava.strava_log
group by all
order by 1
```


<BarChart 
    data={activities_over_time}
    x=year_month
    y=activity_hours
/>