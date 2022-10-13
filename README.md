# Google Data Analytics Capstone Project - Bellabeat Wellness
##### A capstone project by Jason Qu 
## Introduction 
This capstone project is the final case study of the Google Data Analytics Course provided via Coursera. This case study entails what I have learnt throughout the Google Data Analytics course as well as the application of business concepts and skills that I have learnt during my time in University.

### Bellabeat Wellness
Bellabeat Wellness is a health and wellness brand, designed for women. The company develops wearables and acommpanying products that monitor biometrics and lifestyle data in order to empower women by helping them understand how their bodies work and to make healthier lifestyle choices. Their vision is to ["Empower women to reconnect with themselves"](https://bellabeat.com/about/). 

<br/><br/>
## Business Task & Stakeholders
### Scenario
Bellabeat is a successful small company, but they have the potential to become a larger player in the
global smart device market. Urška Sršen, cofounder and Chief Creative Officer of Bellabeat, believes that analyzing smart
device fitness data could help unlock new growth opportunities for the company. 

### Business Task
I have been asked to analyze smart device data (fitBit dataset) to gain insight into how consumers are using their smart devices in order to determine an appropriate business strategy and direct focus towards certain Bellabeat products.

### Stakeholders
- Urška Sršen: Bellabeat’s cofounder and Chief Creative Officer
- Sando Mur: Mathematician and Bellabeat’s cofounder; key member of the Bellabeat executive team
- Bellabeat marketing analytics team: A team of data analysts responsible for collecting, analyzing, and reporting data that helps guide Bellabeat’s marketing strategy.

<br/><br/>
## About the Data
### Source
Data has been provided by Bellabeat via [Kaggle](https://www.kaggle.com/datasets/arashnic/fitbit) through Amazon Mturk (3rd party source). The dataset contains personal fitness tracking data from 33 fitbit users. Users have consented to submission of personal tracker data for research purposes. Due to the nature of the data source, I am unable to verify the integrity of the data and whether or not it has been subjected to any kind of bias.

### Storage
For the purpose of this case study, I have opted for Microsoft's SQL Servers and SSMS because they allow me to view the data in a much cleaner format than Excel/Sheets/R Studio would, and allow me to manipulate and view the data quickly (Simple SQL queries to filter and sort than Excel/Sheets and cleaner than R). A cleaner and quicker view of the data helped me to decide what aspects of the data I believed should be cleaned. Excel/Sheets would have been a good option as well as there aren't many rows and visualisation could have been done in the same place. Doing the case study in SQL also allows me to document my process better than Excel/Sheets would.

The dataset was downloaded from Kaggle and stored into Microsoft SQL servers.

### Limitations
- The sample size is too small (33) to represent a proper population and will have a high margin of error if used for real world project purposes.
- The dataset does not specify demographic information such as: age, sex, ethnicity, etc...
- The dataset is outdated (2016) for the current date.
- The dataset comes from a 3rd party provider (Amazon Mturk), so there is a lack of integrity.
- The metadata is vague. Data pertaining to sleep is not explained; how it is collected or how their algorithm functions (Is sleep determined by a user's heart rate or movement? If someone is sedentary, how does it differentiate between sleeping and sedentary?). Does not specify how steps are tracked, just that they are and that users can also input their steps tracked.

### Assumptions/Notes
- The level of activity is not specified in the dataset (light, moderate and very active), however having searched it up online, fitBase have provided an updated medadata PDF outlining that each level is as followed: <3 MET's, 3-6 MET's and >6 MET's, which are a unit of measurement for [exercise intensity](https://www.healthline.com/health/what-are-mets).

### Data cleaning report
To ensure my analysis would not get cluttered with unnecessary data and tables, I chose to limit which tables I was going to use for analysis. For the purposes of my case study, I opted to use the following 3 tables: [dailyActivity_merged](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/dailyActivity_merged.csv), [sleepDay_merged](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/sleepDay_merged.csv) and [weightLogInfo_merged](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/weightLogInfo_merged.csv). These 3 tables contain the most relevant data for my study, as the other tables are essentially broken down versions of the dailyActivity table. The other tables are too in-depth for the business goal and are better suited for non-marketing purposes.

- **Duplicate** rows have been checked for in all 3 tables with only a few occurences in one table; sleepDay_merged. To fix this, I moved the data into a new Table called sleepDay. Any further cleaning would be done in this table instead of being migrated.
- **Incomplete, Inaccurate and inconsistent** data has been filtered out of the raw dataset by applying filters relating to: steps recorded, minutes spent in a sedentary state and calories burnt. This filter basically removed any data that had rows containing a 0 or max value for the row entered, data that did not make sense such as someone being sedentary for 24 hours and rows that were automatically recorded by the fitBit device despite having improper or no values. This process also indirectly removed outstanding outliers, if there were any as it would filter out non-sensical data too.
- **Adjusting and converting** Columns to become more user friendly and certain data types to ensure certain math functions would work properly on them. Dates were converted into their relative weekday in order to apply aggregation on the data and to catagorize it. This would allow me to pull summary data from the table and also point out key facts pertaining to each table, where needed.

<br/><br/>
## Analysis
The analysis was carried out in a combination of SQL, Google Sheets and Tableau. I used SQL to merge the dailyActivity and sleepDay tables together in order to assess the data from both tables at once. I exported each cleaned set out of SQL and then imported them to both Tableau and Sheets. I used sheets to create summary pivot tables and to gather the averages of each column of data, which allowed me to extract vital key points and figures. These figures allowed me to determine popular trends among the data in the bullet points below. I also used Sheets to create numerous scatter plots, comparing many numerical variables to determine any trends. Tableau was used to visualise the differences between catagorical data, namely the Activity hours columns and the KM travelled columns.

### Key points
- Daily Activity Summary
  - Of the 3 exercise intensities (Light, moderate and intense), Light activity is the most common, followed by Intense and then moderate. On a weekly basis, light activity had a total average of **25.04** hours a week, followed by Intense at **2.74** hours a week and moderate at **1.76** hours a week.
  - KM Travelled wise, the trend is the same wherein; light activity is the most commmon followed by intense, and then moderate. The KM's travelled per week are as follows: **26.04** - light, **11.69** - intense, **4.46** moderate.
  - The most popular day for exercise appears to be Saturday, where saturday has the highest average steps, light activity and moderate activity, calories burnt and light and moderate KM travelled. Saturday meets the max of each weekday for 6/8 catagories. The least popular day appears to be friday, where friday has the lowest values of exercise for 5/8 catagories.
  - Friday and monday are the laziest days, where each day has an average sedentary hours spent at **16.38** and **16.37**.

- Sleep Activity Summary
  - Sunday is the laziest day, with the highest recorded hours asleep and in bed at **7.5** hours and **8.25** hours respectively.
  - The most active days were tied between friday and thursday, where their lowest recorded values were **6.69** hours asleep on average for both days, **7.26** hours spent in bed on friday and **7.25** hours spent in bed on thursday.
  - In a weeks average, participants were recorded to have slept **48.61** or **6.94** hours a day and spent an average **52.94** hours a week in bed (inclusive of time asleep) or **7.57** hours a day.

### Visualisation
#### Exercise type popularity (Hours spent)
![avgHours](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/IntensityHours.png)
Light activity is predominantly the most popular choice, followed by intense and then moderate. Users seem to exercise a lot on Tuesday and Saturday.
<br/><br/>

#### Exercise type popularity (KM Travelled)
![avgKM](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/IntensityKMTravelled.PNG)
Again, light activity is the predominant activity level recorded for the amount of KM's travelled by an individual on average. The trend here is the same as the hours spent where the most popular day for exercise is Tuesday, followed by Saturday.
<br/><br/>

#### Calories burnt on a daily basis
![calories](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/CaloriesBurnt2.png)
Users again tending to exercise/burn the most amount of calories on Tuesday and Saturday.
<br/><br/>

#### Calories burnt relative to steps
<img src="https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/CaloriesVsSteps2.PNG" align="left"/>
Calories burnt relative to steps does indeed show a slight positive linear slope. Although the R coefficient is low, the statistical significance is probably high. Users are more likely to burn calories if they increase their step count everyday.
<br clear="left"/>
<br/><br/>

#### Effect of different levels of activity on amoutn of calories burnt 
![CaloriesActivity](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/CaloriesActivityCombined.PNG)
The comparison of each activity level reveals that the highest intensity of activity has the greatest positive association with calories burnt. Light and moderate are quite close together in terms of trends. This could be explained by the fact that moderate activity in hours only has **554 rows** when entries of 0 are filtered out and light activity has **843 rows**. Light activity or [<3 MET's](https://www.healthline.com/health/what-are-mets#examples) as defined by healthline, is activity described as: sitting at a desk, sitting while playing cards, standing at a desk, washing dishes and various other sitting activites. Due to the nature of light activity, this category will almost always have a non-zero entry and could possibly skew the outcome of any function.
<br/><br/>

#### Calories burnt while sedentary
![CaloriesSedentary](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/CaloriesVsSedentary2.PNG)

Not strong enough to prove any hypothesis about the correlation between hours spent idle and calories burnt.
<br/><br/>


#### Time spent asleep daily
![Sleep](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/TimeAsleep.png)

Where Tuesday and Saturday are supposedly the hot days for exercise, the respective following days of both are also the seemingly laziest. Wednesday and Sunday both top the hours spent asleep at **7.24** and **7.50** respectively.
<br/><br/>

#### Time asleep relative to calories burnt
![SleepCalories](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/SleepVsCalories.PNG)

No noticeable trend between calories burnt and hours slept.
<br/><br/>

#### Effect of time spent asleep on different levels of activity
![SleepActivity](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/SleepActivityCombined.PNG)

Unlike calories burnt, sleep definitely does not seem to have an effect on how much each type of exercise is done on average. The moderate activity hours graph shows a slightly negative slope, but the R coefficient is too small to be able to confirm anything.
<br/><br/>

#### Hours delegated by users to each activity on a weekly basis
![Hours](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/HoursDivided.PNG)

Almost **3/4** of user's time was spent in a sedentary state. Almost **1/5** of those hours were spent doing light activity. Moderate and Intense levels of exercise only took up a combined **4.5%** of people's weekly exercise. From the pivot tables generated, each activity in order of most to least hours respectively: **12.01, 3.65, 0.43 and 0.30** hours are spent on each activity per week, on average. The [CDC](https://www.cdc.gov/physicalactivity/basics/adults/index.htm) recommends that adults need at least 150 minutes or 2.5 hours of moderate-intense levels of physical activity. Combined, moderate and intense hours recorded only total 0.73, almost 2 hours short of the recommended amount.
<br/><br/>

<br/><br/>
## Conclusion
### Activity
- There is shown to be positive linearity between calories burnt and intensive activity or even walking.
- Users prefer intense activity over moderate. Intense activity is shown to be effective in burning calories. However, the amount of hours spent in a week on either exercise is no where near CDC's recommended amount.
- There is no consistent pattern of days where people choose to exercise. This could be capitalised on and could encourage users to spread or manage their exercise schedules better.
- Time spend sedentary takes up almost 75% of a users activity cycle. This could be improved.

### Sleep
- Sleep data did not reveal any noticeable trends.
- Just like activity data, there were favourable days of sleep for users; the days following the most active exercise days. This could also be an opportunity for growth, where users could manage their sleep patterns better.

### Weight log
The weight log table was left out by choice, due to an underwhelming amount of records. None of the weight records were taken into account when conducting analysis, as there was insufficient rows to actually allow any kind of useful inner join. There could be a lot of improvement to data regarding weight, such as user incentives to record their own weights. The automatic reporting feature does not help to smooth the data and only creates more error in data cleaning and analyzing. 

### Recommendations
#### Balancing wellness with exercise
Currently, Bellabeat focuses simply on wellness and data recording. Their primary product is the [health tracker](https://bellabeat.com/catalog/), the Leaf Chakra or Leaf Urban. Their other products are simply accessories for the Leaf device. While they understand the importance of wellness and even provide a [how to wellness page](https://bellabeat.com/journal/), they should push for products that motivate women to exercise more. Bellabeat could emphasize on this by engineering gear, tailored towards more intensive and even moderate exercise. These products could be something as simple as Bellabeat Joggers, fitness apparel or even a drink bottle to encourage physical activity.

#### Encouraging sleep
While sleep does not appear to be much of a problem in the data, the [CDC](https://www.cdc.gov/sleep/features/getting-enough-sleep.html) recommends that adults 18-60 get at least 7+ hours of sleep per night. The sleep graph indicates that users are only 7+ hours of sleep on 2/7 days of the week. With many studies on effects of sleep relative to weight loss and better health, Bellabeat should definitely encourage users to record sleep activity more and encourage people to sleep more each night when possible. Bellabeat already has a mobile app called Bellabeat Wellness Coach, they should emphasize on their app and inform users about the importance of sleep relative to health and wellness.

#### Weight positivity
Weight positivity is another important factor that Bellabeat could emphasize on, as there is great potential for growth in this area of Bellabeat's wellness line. Bellabeat should push for body image positivity and let users know that their data is safe. Small things like motivational messages through their app could be a good motivator for people to start recording weight data more often.
