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
### Key points
- Daily Activity Summary
  - Of the 3 exercise intensities (Light, moderate and intense), Light activity is the most common, followed by Intense and then moderate. On a weekly basis, light activity had an average of **25.04** hours a week, followed by Intense at **2.74** hours a week and moderate at **1.76** hours a week.
  - KM Travelled wise, the trend is the same wherein; light activity is the most commmon followed by intense, and then moderate. The KM's travelled per week are as follows: **26.04** - light, **11.69** - intense, **4.46** moderate.
  - The most popular day for exercise appears to be Saturday, where saturday has the highest average steps, light activity and moderate activity, calories burnt and light and moderate KM travelled. Saturday meets the max of each weekday for 6/8 catagories. The least popular day appears to be friday, where friday has the lowest values of exercise for 5/8 catagories.
  - Friday and monday are the laziest days, where each day has an average sedentary hours spent at **16.38** and **16.37**.

- Sleep Activity Summary
  - Sunday is the laziest day, with the highest recorded hours asleep and in bed at **7.5** hours and **8.25** hours respectively.
  - The most active days were tied between friday and thursday, where their lowest recorded values were **6.69** hours asleep on average for both days, **7.26** hours spent in bed on friday and **7.25** hours spent in bed on thursday.
  - In a weeks average, participants were recorded to have slept **48.61** or **6.94** hours a day and spent an average **52.94** hours a week in bed (inclusive of time asleep) or **7.57** hours a day.

### Visualisation
#### Exercise type popularity
![avgHours](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/AvgIntenseHours.PNG)

<br/><br/>
## Conclusion
### Recommendations
