---
output:
  pdf_document: default
  html_document: default
---
# Kickstarting with Excel

## Overview of Project

### Purpose
The purpose of this analysis is to review the outcomes of various campaigns based on the amount of their fundraising goals and when they were launched. By analyzing this data, we're gathering historical information in which Louise can compare the results of her campaign. She'll also be able to determine if her campaign performed under or below previous campaigns with similar characteristics.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
To begin the analysis of Outcomes Based on Launch Date, a column for the year of date creation was added to the Kickstarter data set. To add this column I used the =YEAR() formula to extract the year from the Date Created Conversion column. Once this column was added, I pivoted the data with the following fields.
  Filters: Parent Category, Years
  Columns: Outcomes
  Rows: Date Created Conversion
  Values: Count of Outcomes
  ![Pivot Table - Theater Outcomes by Launch Date](Documents/Data Analytics Bootcamp/Resources/Pivot Table_by Launch Date.png)
Next, I filtered for Parent Category for just Theater (since Louise is focused on campaigns for theater projects) and then inserted a line graph based on this filtered pivot table. The line graph shows the month of Date Created Conversion on the x-axis and count of outcomes on the y-axis. The legend allows us to break out the count of outcomes by the actual outcome result, so we have 3 lines for successful, failed, and canceled campaigns.
![Theater Outcomes by Launch Date](Documents/Data Analytics Bootcamp/Resources/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals
To begin the analysis of Outcomes Based on Goals, I first had to gather the number of successful, failed, and canceled campaigns based on the goal amount. I divided up the goal amount into 12 buckets using $5000 ranges. I then used =COUNTIFS() to calculate the number of cases that fell into each bucket. The Outcomes column in the Kickstarter dataset served as criteria_range1 and criteria1 was updated to successful, failed, or canceled accorddingly. The Goal column in the Kickstarter dataset served as criteria_range2 and criteria2 was updated depending on the goal range in the spreadsheet. Sample formulas are listed below.
  Less than 1000:
    Number Successful: =COUNTIFS(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D,"<1000")
    Number Failed: =COUNTIFS(Kickstarter!$F:$F, "failed", Kickstarter!$D:$D,"<1000")
    Number Canceled: =COUNTIFS(Kickstarter!$F:$F, "canceled", Kickstarter!$D:$D,"<1000")
  20000 to 24999
    Number Successful: =COUNTIFS(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D,">20000",Kickstarter!$D:$D,"<24999")
    Number Failed: =COUNTIFS(Kickstarter!$F:$F, "failed", Kickstarter!$D:$D,">25000",Kickstarter!$D:$D,"<29999")
    Number Canceled: =COUNTIFS(Kickstarter!$F:$F, "canceled", Kickstarter!$D:$D,">25000",Kickstarter!$D:$D,"<29999")
  Greater than 50000
    Number Successful: =COUNTIFS(Kickstarter!$F:$F, "successful", Kickstarter!$D:$D,">50000")
    Number Failed: =COUNTIFS(Kickstarter!$F:$F, "failed", Kickstarter!$D:$D,">50000")
    Number Canceled: =COUNTIFS(Kickstarter!$F:$F, "canceled", Kickstarter!$D:$D,">50000")

Next, I summed the number of successful, failed, and canceled campaigns to get the number of Total Projects in column E. I used the =SUM(B2:D2) formula & copied it down through all cells for the various goal ranges. Then to calculate the percentage of successful, failed, and canceled campaigns for each goal range. I divided the number of cases for each category by the total number of cases (e.g. =B2/E2). Once I had all of percentages calculated, I inserted a line graph, titled Outcomes Based on Goals, with the goal ranges on the x-axis and percentage on the y-axis.
![Outcomes Based on Goal](Documents/Data Analytics Bootcamp/Resources/Outcomes_vs_Goals.png)

### Challenges and Difficulties Encountered
When completing this analysis, I ran into difficulties navigating the =COUNTIFS formula at first. I was confused on where the range to be evaluated was entered and how to set the criteria I was looking for. To help me use the formula, I conducted a brief Google search that showed me that the criteria range goes first and the criteria you're searching for is inserted second between quotation marks.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?
  1. Launching campaigns in May or June may increase the chances of success for that campaign.
  2. Launching a campaign in December has little to not effect on the result of the campaign.

- What can you conclude about the Outcomes based on Goals?
  The chances of success is negatively correlated with the goal amount while the     chances of failure is positively correlated with the goal amount. Meaning the      higher the goal, the higher the chances of failure.

- What are some limitations of this dataset?
  I think a limitation would be that all of the dollar values are recorded in USD    but the currency column says that some campaigns took place in different           countries/currencies. It would be useful to have a column that has the campaign's   true value in it's respective currency & a column that converts that value to      USD.

- What are some other possible tables and/or graphs that we could create?
  I think it would be usefull to see the number of backers for successful campaigns   by goal range to show Louise how many potential supporters she'll need depending   on her campaign goal.
