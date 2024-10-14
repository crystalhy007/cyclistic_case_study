# Cyclistic Bike-share Marketing Analysis

- **Author Name**: Yue (Crystal) Hu
- **Date**: October 2024

## Introduction
Cyclistic is a bike-share company in Chicago. Since its inception in 2016, Cyclistic has grown to a fleet of 5,824 bicycles, geotracked and docked across 692 stations throughout Chicago. Riders can unlock bikes from one station and return them to any other station in the system, making it a highly flexible service.

Cyclistic’s marketing strategy has focused on building general awareness and appealing to a broad consumer base. One of its key advantages is the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Casual riders are who purchase single-ride or full-day passes and Cyclistic members are who subscribe to annual memberships.

According to finance analysis, annual members are significantly more profitable than casual riders. As such, the marketing director has identified converting casual riders to annual members as a critical growth strategy. The challenge lies in understanding how these two customer types differ and how Cyclistic can use digital media to influence casual riders to become members.

## Project Goal
The primary goal of this project is to design marketing strategies that aim to convert casual riders into annual members by addressing the following questions:
1. How do annual members and casual riders differ?
2. Why would casual riders buy a membership?
3. How can digital media be used to influence casual riders to become members?

This case study will focus specifically on the first question: **How do annual members and casual riders differ?**

## Data Source
We analyzed trip data from the past 12 months (October 2023 - September 2024) to identify trends and insights. The dataset includes information on:
- Ride ID (primary key)
- Rideable type
- Start and end times
- Start and end stations
- User type (member or casual)

For privacy reasons, the dataset does not include personally identifiable information, such as credit card details.

## Tools Used
The analysis was conducted using:
- **Python** for data processing, transformation, and analysis
  - **pandas**: Data manipulation and analysis
  - **numpy**: Numerical operations
  - **seaborn**: Data visualization

## Data Processing Steps
1. **Load and Combine Data**: 
   - Merged 12 monthly .csv files into a single dataframe.
   - The combined dataset consists of 5,854,544 rows and 13 columns.

   | Column Name           | Data Type  |
   |-----------------------|------------|
   | ride_id               | object     |
   | rideable_type         | object     |
   | started_at            | object     |
   | ended_at              | object     |
   | start_station_name    | object     |
   | start_station_id      | object     |
   | end_station_name      | object     |
   | end_station_id        | object     |
   | start_lat             | float64    |
   | start_lng             | float64    |
   | end_lat               | float64    |
   | end_lng               | float64    |
   | member_casual         | object     |

2. **Initial Data Exploration**:
   - Calculated the duration of each ride.
   - Extracted weekday and month from the start date.
   - Calculated the distance between the start and end stations, using latitudes and longitudes.

   > Note: Distance helps to identify outliers, but a distance of 0 is possible if the bike is returned to the original station.

3. **Data Cleaning**:
   - **Remove Duplicates**: Ensured each row represents a unique ride.
   - **Data Type Correction**: Converted `started_at` and `ended_at` columns to `datetime` type.
   - **Handle Missing Values**: Focused on cleaning missing values in the `end_lat` and `end_lng` columns. Approximately 0.1% (7,441 rows) of the data had missing values, which were removed.
   - **Negative Durations**: Identified and removed 1,089 records with incorrect negative durations.
   - **Outlier Detection**: Focused on detecting outliers in duration and distance. Used the Interquartile Range (IQR) method to calculate upper and lower fences, removing unreasonable data points (e.g., trips lasting over 2 hours and minute/mile less than 2 minutes).

## Data Analysis
To address the question **How do annual members and casual riders differ?**, I analyzed the following:

1. **Number of Rides per User Group**:
   - **Annual Members**: 64% of all rides were from annual members.
   - **Casual Riders**: 36% of the rides were from casual riders.
   
2. **Number of Rides by Rideable Type per User Group**:
   - 90% of both annual members and casual riders used either classic bikes or electric bikes. Both groups showed a strong preference for these rideable types.

3. **Ride Duration Groups**:
   - **Annual Members**: The average ride duration was 12 minutes. Only 6% of the rides exceeded 30 minutes.
   - **Casual Riders**: The average ride duration was 18 minutes, with 16% of rides exceeding 30 minutes. Casual riders tend to have longer rides than annual members.
   
   > We grouped ride durations into four categories: less than 10 minutes, less than 30 minutes, less than 60 minutes, and more than 60 minutes.

4. **Rides by Month**:
   - Both annual members and casual riders showed increased ridership in warmer months (from May to October). 
   - **Casual Riders**: There was a sharp drop (49%) in usage from September to October, indicating that casual riders are more sensitive to weather changes.

5. **Rides on Weekdays vs. Weekends**:
   - **Annual Members**: On average, they took 21% fewer rides on weekends compared to weekdays, suggesting they may use the service more for commuting.
   - **Casual Riders**: They took 48% more rides on weekends, indicating their preference for leisure rides during the weekend.

6. **Top 5 Start Stations per User Group**:
   - **Annual Members**: The top 5 stations are located near public transportation hubs, suggesting that members may use bikes for commuting purposes.
   - **Casual Riders**: The top 5 stations are close to tourist attractions, indicating that casual riders primarily use the service for leisure and sightseeing.

## Recommendations
Based on the data analysis, the following marketing strategies are recommended to convert casual riders into annual members:

1. **Target Casual Riders' Longer Ride Durations**:
   - **Insight**: Casual riders use bikes for longer durations on average.
   - **Recommendation**: Highlight the cost-saving benefits of an annual membership for longer rides. Emphasize that longer rides could be more affordable with a membership.

2. **Seasonal Promotions Targeting Weather Preferences**:
   - **Insight**: Casual riders are more active during warmer months and react strongly to weather changes.
   - **Recommendation**: Launch promotional campaigns at the start of the summer season. Consider offering a flexible payment plan for memberships during peak riding months.

3. **Weekend Leisure Usage**:
   - **Insight**: Casual riders predominantly use bikes on weekends for leisure.
   - **Recommendation**: Promote member-exclusive weekend events, discounts, or rides to build a community around biking. Leverage social media to advertise these events, encouraging casual riders to convert to members for exclusive access.

## Next Steps
To further enhance our understanding and conversion strategies, the following steps should be taken:
1. **Analyze User Demographics**:
   - Gather and analyze user demographic data (age, income, location, etc.) to understand which customer segments are most likely to convert from casual to annual members.
   
2. **Examine App Usage**:
   - Study app usage data (e.g., interaction patterns, feature usage) to identify touchpoints where casual riders could be prompted to consider annual memberships.

3. **Explore Digital Marketing Channels**:
   - Investigate how digital media (social media, email marketing, in-app notifications) can be leveraged to target casual riders and encourage them to become annual members.

[Visit Analysis Presentation]([https://www.tableau.com](https://github.com/crystalhy007/cyclistic_case_study_presentation/blob/main/cyclistic_case_study%20_slides.pdf))
