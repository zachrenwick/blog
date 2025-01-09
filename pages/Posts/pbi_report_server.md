---
title: Power BI Report Server vs Premium
---


## Introduction

In this article I’ll share the top issues and missing features of Power BI Report Server (PBIRS), and explain why I think organizations should choose cloud versions of Power BI over the on-premises PBIRS.

_as of May 2020 – these features may change over time._

![](/posts/images/pbi-south-park.png){fig-alt="Power BI Report Server Bad Time" fig-align="center"}

**To begin with, what is PowerBI.com vs. Power BI Report Server?**

Microsoft offers free, Pro, and Premium licensing options for Power BI in the cloud. Under these cloud options, users access their reports, dashboards and data through the Power BI service on PowerBI.com.

Microsoft also offers an on-premises version of Power BI. Under this framework, IT installs the software – Power BI Report Server (PBIRS) – on a dedicated server or VM, likely somewhere within your corporate network environment. Whereas the cloud versions of Power BI greet you with a customized home page and modern navigation, the PBIRS front end is very similar to SQL Server Reporting Services (SSRS). Users open an internal URL to browse a simple folder UI structure. 

Now that I’ve shared an overview of how the Power BI on-premises architecture compares to cloud versions, let’s jump into the top issues I see with selecting PBIRS over PowerBI.com.

## 1: Power BI Report Server Is Not A Self-Serve Analytics Platform
I’m starting this off with a controversial first item. Microsoft might argue that PBIRS checks the box for enabling self serve analytics. But because of the missing features listed in this article, organizations will quickly find themselves with bottlenecks in delivering BI and analytics to their end users.

The average business user cannot create reports or analyze data on their own with Power BI Report Server. They will need the help of a Power BI developer, or some other power user to create the reports and dashboards for them to consume. 

This is because reports can only be uploaded to PBI Report Server through development in Power BI Desktop, which requires too much background knowledge and skill in DAX and M to immediately start working with.

The bottleneck quickly becomes how quickly specialized Power BI developers can create reports. This does not enable the organization to become “self-service” in any way, shape or form.


How are self-service analytics enabled in cloud versions of Power BI?

To begin with, the Power BI service on PowerBI.com is a cloud-native application. Due to this, end users can immediately begin creating reports from the comfort of their web browsers, without the need to download and install Power BI Desktop.

Similar to using Pivot Tables in Excel, users can utilize existing datasets to quickly drag and drop fields onto a canvas to start analyzing and creating visualizations on their data.


They can also pin their most important or favourite visualizations and tables from various reports to create a customized dashboard. All without the need for a dedicated Power BI developer creating this content for them!


Above image shows visuals pinned from MULTIPLE reports into a centralized view. Built from web browser.

As you’ll soon learn from points #3, #4, #5 and #7, PowerBI.com has other significant features which enable much more self-serve usability. 

## 2: No Major Product Updates 
One of the reasons why Power BI adoption has skyrocketed across enterprises is that their product team releases significant new features every month that are automatically applied to cloud environments.

The same cannot be said about Power BI Report Server (PBIRS). Besides the fact that you need to manually apply server updates, very few new features have been added to the last few releases. As each month wears on, the gap between the cloud and on-premises features widens. 

Many new AI/ML, data viz, and dev-ops features were announced at Microsoft’s Business Applications Summit (MBAS) for PowerBI.com. Unfortunately, I am very doubtful these features will ever trickle down to on-premises customers using PBIRS. 


## 3: Reusable/Shared Datasets
Have you ever noticed a KPI or metric that doesn’t match across different reports? This is a common challenge encountered in Business Intelligence.

This problem is exacerbated in Power BI Report Server, as you cannot share self serve data models/datasets across multiple reports. This means that every report has its own version of the “truth”. Unless your report developers are diligent about manually cross-checking calculations across various reports (a never-ending endeavor), KPI discrepancies will surface. 

This challenge has already been addressed in cloud versions of Power BI. Data modellers can create centralized data sets that are utilized and shared across different reports and dashboards. Thus, the elusive “single version of the truth” can become a reality for your organization. 


Image source: RADCAD (https://radacad.com/power-bi-shared-datasets-what-is-it-how-does-it-work-and-why-should-you-care)

By not having to track down and explain these KPI variances, an immense amount of time (and trust), could be saved for end users and developers.


## 4: Analyze Power BI Datasets in Excel
In point #3, I explained that datasets can (and should!) be utilized across multiple reports in Power BI to avoid KPI and metric discrepancies. 

With cloud versions of Power BI, self service analytics can be taken a step further by allowing datasets to be analyzed in Excel. This means that analysts more comfortable using Excel can connect to live versions of the datasets published to PowerBI.com. When the datasets refresh with new data or additional metrics are added, all changes immediately flow through to the connected Excel sheets. 

This has other positive effects: by enabling Excel users to analyze the data themselves, they will no longer be completely reliant on Power BI developers to create all of their reports and visualizations.



## 5: Data Alerts and Report Subscriptions 
Cloud versions of Power BI allow you to create automated data alerts which notify you when a KPI goes above or above your specified threshold. I previously made a video showcasing this feature.


You can also set up report subscriptions which will automatically email a screenshot of your report to receipts on your specified schedule.


These two features are not natively supported in Power BI Report Server. 

## 6: Python and R Integration
You can create custom visualizations with R or Python programming languages and have these displayed within your Power BI reports.


On top of that, you can also leverage machine learning and AI models created by your data scientists and analysts to be integrated directly in your Power BI datasets. When new data is available, your R and Python scripts can be run as part of your regular data refreshes. 


Again, this seamless integration of R and Python is not available within Power BI Report Server.

## 7: Q&A Functionality
Did you know that Power BI can understand natural language? Imagine typing, “what were sales in 2019?” and immediately receiving an answer (and accompanying data visualization).

I previously demonstrated Q&A features in this YouTube video. Suffice it to say, you could be saving a lot of analysts’ time by offloading some basic queries to the Q&A feature. 


Unfortunately, Q&A in its current form is not available in Power BI Report Server. 

## 8: Better Integration with Microsoft O365 Products 
Power BI recently announced a new integration with Microsoft Teams, which will allow you to embed reports directly. By putting the data even closer to your end-users, organizations can advance their goals of becoming more data driven and encourage more discussion around your results and metrics.


As well, you can now easily copy and paste visuals from PowerBI.com into other Microsoft programs like Excel, Word and Outlook. These visuals will paste with a direct link to the original Power BI report:


## Summary
As you can see, you will encounter major product shortcomings if you choose Power BI Report Server over one of the Power BI cloud licensing options (Pro or Premium). By no means is this an exhaustive list, as there are many other features I could have brought up for comparison.

Considering these points, in today’s fast changing and competitive environment, do you want to invest in software to “keep the lights on”, or do you want to gain a competitive edge and reduce friction in delivering analytics products? To me, the choice is very clear, but I’m not the one paying the bills… which leads me to my next point.

### Why would you choose Power BI Report Server?

To be fair, Power BI Report server could still serve your needs if you are looking to deploy a centralized dashboarding strategy, or if you want to save on costs.

Why? Well.. Power BI in the cloud isn’t cheap. Pro licensing starts at $13 CAD/user/month, and Premium options start at $6000 CAD/month. Certain versions of SQL Server Enterprise with Assurance actually give Power BI Report Server licensing for free. 

However, by selecting Pro or Premium Power BI licencing options, you’ll ensure you have access to the latest and greatest features, support and technology moving forward. 

**If you have any questions or comments, please let me know in the comments below!**