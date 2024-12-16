---
title: Training Log
fullWidth: true
---


## Logging Exercise with Strava

I started getting back into endurance sports in 2020 after a 6 year hiatus. In high school and university, road and track cycling were a big part of my life. 

I thought it would be interesting to combine my passions of exercising and working with data. Here you can see I've integrated my Strava/Garmin workouts into this website to analyze how my exercise patterns have changed over time. More is always better, right?

Well, let's start with that. Have I been exercising more over time?


```sql activities_by_year
select 
cast(year(date_dt) as string) as year_dt,
sum(activity_hours) as activity_hours
from strava.strava_log
where date_dt >= '2020-01-01'
group by all
order by 1
```





<BarChart 
    data={activities_by_year} sort="year_dt"
    x=year_dt
    y=activity_hours
/>


What are my top sports?







```sql activities_calendar_view
select 
date_dt,
sum(activity_hours) as activity_hours
from strava.strava_log
where date_dt >= '2020-01-01'
group by all
order by 1
```





What if we looked at it in a calendar view?

<CalendarHeatmap 
    data={activities_calendar_view}
    date=date_dt
    value=activity_hours
/>