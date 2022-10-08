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

### Data cleaning report
To ensure my analysis would not get cluttered with unnecessary data and tables, I chose to limit which tables I was going to use for analysis. For the purposes of my case study, I opted to use the following 3 tables: [dailyActivity_merged](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/dailyActivity_merged.csv), [sleepDay_merged](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/sleepDay_merged.csv) and [weightLogInfo_merged](https://github.com/Litrus/Jason_Case_Study/blob/main/Fitbase_Data/weightLogInfo_merged.csv). These 3 tables contain the most relevant data for my study, as the other tables are essentially broken down versions of the dailyActivity table. The other tables are too in-depth for the business goal and are better suited for non-marketing purposes.

- **Duplicate** rows have been checked for in all 3 tables with only a few occurences in one table; sleepDay_merged. To fix this, I moved the data into a new Table called sleepDay. Any further cleaning would be done in this table instead of being migrated.
- 


<br/><br/>
## Analysis
### Key points
### Visualisation

<br/><br/>
## Conclusion
### Recommendations
