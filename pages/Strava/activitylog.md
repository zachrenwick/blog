---
title: Activity Log
hide_title: false
fullWidth: true
---

<img src="https://avatars.githubusercontent.com/zachrenwick" alt="Zach" class="rounded-full w-24 h-24 mb-4">

## Logging Exercise with Strava

I started getting back into endurance sports in 2020 after nearly 8 years of hiatus (in high school and university, road and track cycling were a big part of my life). 

I thought it would be interesting to combine my passions of exercising and working with data. Here you can see I've integrated my Strava/Garmin workouts into this website to analyze how my exercise patterns have changed over time. More is always better, right?


How does it work?

https://github.com/benlcollins/strava-sheets-integration

insert diagram here


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
--where year_dt = '${inputs.selected_item.year}'
group by all
order by 1
```


<BarChart 
    data={activities_over_time}
    x=year_month
    y=activity_hours
/>



What if we looked at it in a calendar view?

<CalendarHeatmap 
    data={activities_over_time}
    date=date_dt
    value=activity_hours
/>