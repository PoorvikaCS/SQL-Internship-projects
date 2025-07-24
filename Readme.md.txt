 COVID-19 Data Analytics using SQL

This project analyzes COVID-19 statistics using raw data and SQL queries, focusing on trends, summaries, and insights across countries and time periods.

Objective
To build an interactive SQL-based dataset and derive insights using queries, views, and window functions.

 Tools Used

* SQLite (via DB Browser for SQLite)
* SQL (standard ANSI syntax)
* COVID-19 sample dataset (manually simulated for India, USA, Italy)

 Schema Overview

Table: CovidStats

| Column         | Type    | Description                       |
| -------------- | ------- | --------------------------------- |
| ReportID       | INTEGER | Primary key (auto-increment)      |
| Country        | TEXT    | Country name                      |
| ReportDate     | TEXT    | Date of the report (YYYY-MM-DD)   |
| ConfirmedCases | INTEGER | Total confirmed cases on that day |
| Deaths         | INTEGER | Total deaths reported             |
| Recoveries     | INTEGER | Total recoveries reported         |

Views Created

1. DailyIncrease
   Shows daily increase in confirmed cases using SQL window function LAG().

2. LatestCountryStats
   Returns the most recent statistics for each country.

3. CountrySummary
   Summarizes total confirmed cases, deaths, recoveries, and recovery rate for each country.


>> Interview Questions and Answers

1. What was the objective of your COVID SQL project?
   The objective was to analyze the spread and trends of COVID-19 using SQL. I used queries and views to track daily increases, get country-wise summaries, and compute recovery rates.

2. Which SQL functions did you use in this project?
   I used window functions like LAG() to calculate daily increases, GROUP BY for summaries, JOINs for subqueries, and ROUND() to format recovery rates.

3. How did you calculate the daily new cases?
   I used the LAG() function to get the previous day's cases and subtracted them from the current day’s cases to get the daily increase.

4. What does the LatestCountryStats view show?
   It shows the most recent available report for each country by selecting the max date per country and joining it with the main table.

5. How did you compute the recovery rate?
   Using the formula:
```sql
ROUND(100.0 * SUM(Recoveries) / SUM(ConfirmedCases), 2)
```
This was used in the CountrySummary view.

6. What challenges did you face while building this project?
   Handling NULLs and ensuring correct date ordering for the window function. I also had to simulate realistic data manually while maintaining logical growth in case counts.

7. Can this project be extended further?
   Yes, it can include more countries, columns like tests performed or vaccinations, and even integrate with dashboards using Python libraries like Pandas and Plotly.

8. Why did you choose SQLite for this project?
   SQLite is lightweight, doesn't need server setup, and DB Browser makes it easy to run, test, and visualize queries. It's perfect for compact SQL analytics projects.

9. How did you validate your results?
   I checked data manually and used SELECT queries on views to compare computed values with expected trends. Also, I ensured row counts and date sequences were correct.

10. What did you learn from this project?
    I strengthened my understanding of SQL queries, views, aggregation, window functions, and analytical reporting using SQL. It also taught me how to simulate and clean data for a real-world scenario.