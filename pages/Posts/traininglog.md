---
title: Training Log
---


## Logging Exercise with Strava

I started getting back into endurance sports in 2020 after a 6 year hiatus. In high school and university, road and track cycling were a big part of my life. 

I thought it would be interesting to combine my passions of exercising and working with data. 

### How does it work?

![Strava Activity Pipeline Diagram](/strava_activity_log_diagram.png)

1. I log all my activities with my Garmin smartwatch
2. The data is then synced with Garmin Connect/Strava
3. I set up a [Strava developer app](https://developers.strava.com/) in order to call the Strava API
4. Someone else shared a [useful Google Apps script](https://github.com/benlcollins/strava-sheets-integration) which I run every 6 hours, dumping activity data into a Google Sheet which I can then query using DuckDB or BigQuery 

Here you can see I've integrated my Strava/Garmin workouts into this website to analyze how my exercise patterns have changed over time. More is always better, right?

### Have I been exercising more over time?

It turns out 2023 was my best year for exercise hours:

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


### Top Sports
What are my recent top sports?

```sql activities_window
WITH monthly_activity_hours AS (
    SELECT 
        modified_sport as sport,
        DATE_TRUNC('month', date_dt) AS date,
        SUM(activity_hours) AS activity_hours
    FROM 
        strava.strava_log
    WHERE date_dt >=  date_trunc('month',current_date()-365)
    GROUP BY 
        1,2
)
SELECT 
    sport,
    sum(activity_hours) as total_activity_hours,
    ARRAY_AGG({'date': date, 'activity_hours': activity_hours}) AS activity_hours
FROM 
    monthly_activity_hours
GROUP BY 
    sport
order by total_activity_hours desc
```

<DataTable data={activities_window}>
    <Column id=sport/>
    <Column id=total_activity_hours title="Trailing 12 Mo Total Hours"/>
    <Column id=activity_hours title="Monthly Hours Sparkline" contentType=sparkline sparkX=date sparkY=activity_hours />
</DataTable>


### Trends By Sport
I seem to have seasonal obsessions with Cycling, Pickleball and in the fall/winter spend more time in the gym. You can see that below:

```sql activities_trend
    SELECT 
        modified_sport as sport,
        DATE_TRUNC('month', date_dt) AS month_dt,
        SUM(activity_hours) AS activity_hours
    FROM 
        strava.strava_log
    WHERE date_dt >= date_trunc('month', current_date()-365)
    and sport != 'Other'
    GROUP BY 
        ALL
```

<LineChart 
    data={activities_trend}
    x=month_dt
    y=activity_hours 
    yAxisTitle="Hours per Month"
    series=sport
/>


### Calendar View
What if we wanted to look at exercise activity in a calendar view?


```sql activities_calendar_view
select 
date_dt,
sum(activity_hours) as activity_hours
from strava.strava_log
where date_dt >= '2020-01-01'
group by all
order by 1
```


<CalendarHeatmap 
    data={activities_calendar_view}
    date=date_dt
    value=activity_hours
/>



```sql activities_by_month
select 
datetrunc('month',date_dt) as month_dt,
sum(elapsed_hours) as elapsed_hours
from strava.strava_log
where date_dt >= '2024-01-01'
group by all
order by 1
```

<BarChart 
    data={activities_by_month} sort="month_dt"
    x=month_dt
    y=elapsed_hours
/>