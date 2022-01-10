# Google-Case-Study-BellaBeat
## How can a Wellness Technology Company Play it Smart?
### Myriam Bengoechea Pardo 
### Last Update: 10th Jan 2022

This case study is part of the Google Data Analytics Certificate Track.

# <span style="color:#FA8072; font-size:20px;"> Table of Contents </span>
* [1. Introduction](#1)
    * [1.1 Products](#1_1)
    * [1.2 Stakeholders](#1_2)
* [2. Ask Phase](#2)
    * [2.1 Business Task](#2_1)
* [3. Prepare Phase](#3)
    * [3.1 Data Sources](#3_1)
    * [3.2 Accessibility and privacy of data](#3_2)
    * [3.3 Data Organization and Verification](#3_3)
    * [3.4 Data credibility and integrity](#3_4)
* [4. Process Phase](#4)
    * [4.1 Installing Packages and Opening Libraries](#4_1)
    * [4.2 Import Datasets](#4_2)
    * [4.3 Preview Datasets](#4_3)
    * [4.4 Formatting and Cleaning](#4_4)
        * [4.4.1  Number of Users Verification](#4_4_1)
        * [4.4.2  Identify Duplicates](#4_4_2)
        * [4.4.3  Remove Duplicates](#4_4_3)
        * [4.4.4  Rename Columns](#4_4_4)
        * [4.4.5  Reformatting Date and Time Columns](#4_4_5)
    * [4.5 Merging Datasets](#4_5)
* [5. Analyze Phase](#5)
    * [5.1 Step Usage](#5_1)
    * [5.2 Sleep Usage](#5_2)
    * [5.3 Analyzing Steps and Sleep per Weekday](#5_3)
    * [5.4 Steps per hour in one day](#5_4)
    * [5.5 Correlation between Daily Steps and Calories](#5_5)
    * [5.6 Analyzing How Often Users wear Devices per day](#5_6)
* [6. Conclusion - Act Phase](#6)


# <span style="color:#FA8072; font-size:20px;"> 1. Introduction </span>
<a class="anchor" id="1"></a>

Bellabeat is a high tech company that manufactures health-focused smart products for women. The devices collect data on the user's activity, sleep, stress and reproductive health. The company has invested in traditional advertising  media, such as radio, out-of-home billboards, print and television but mainly focuses on digital marketing. Bellabeat invests year-round in Google Search, maintaining active Facebook and Instagram pages, and consistently engages consumers on Twitter. Additionally, Bellabeat runs video ads on Youtube and displays ads on the Google Display Network to support campaigns around key marketing dates.
# <span style="color:#FA8072; font-size:16px;"> 1.1 Products </span>
<a class="anchor" id="1_1"></a>
Bellabeats products include the following:
Bellabeat app: The Bellabeat app provides users with health data related to their activity, sleep, stress,
menstrual cycle, and mindfulness habits. This data can help users better understand their current habits and
make healthy decisions. The Bellabeat app connects to their line of smart wellness products.
Leaf: Bellabeat’s classic wellness tracker can be worn as a bracelet, necklace, or clip. The Leaf tracker connects to the Bellabeat app to track activity, sleep, and stress.
Time: This wellness watch combines the timeless look of a classic timepiece with smart technology to track user activity, sleep, and stress. The Time watch connects to the Bellabeat app to provide you with insights into your daily wellness.
Spring: This is a water bottle that tracks daily water intake using smart technology to ensure that you are
appropriately hydrated throughout the day. The Spring bottle connects to the Bellabeat app to track your hydration levels.
Bellabeat membership: Bellabeat also offers a subscription-based membership program for users. Membership gives users 24/7 access to fully personalised guidance on nutrition, activity, sleep, health and beauty, and mindfulness based on their lifestyle and goals.
# <span style="color:#FA8072; font-size:16px;"> 1.2 Stakeholders </span>
<a class="anchor" id="1_2"></a>
**Primary Stakeholder:**
* Urška Sršen (Cofounder and Chief Creative Officer)
* Sando Mur (Mathematician, cofounder; key member of the executive team)

**Secondary Stakeholder:**
* Bellabeat Marketing Analytics Team: A team of data analysts responsible for collecting, analyzing, and reporting data that helps guide Bellabeat’s marketing strategy.

# <span style="color:#FA8072; font-size:20px;"> 2. Ask Phase </span>
<a class="anchor" id="2"></a>
The co-founder has asked me to analyse smart device usage data in order to gain insight into how consumers use non-Bellabeat smart devices. An analysis of Bellabeat’s available consumer data would reveal more opportunities for growth. 
# <span style="color:#FA8072; font-size:16px;"> 2.1 Business Task </span>
<a class="anchor" id="2_1"></a>
* **Goal 1:** Identify trends in smart device usage.
* **Goal 2:** Identify how these trends could apply to Bellabeat customers.
* **Goal 3:** Identify how these trends could help influence Bellabeat’s marketing strategy.

# <span style="color:#FA8072; font-size:20px;"> 3. Prepare Phase </span>
<a class="anchor" id="3"></a>
# <span style="color:#FA8072; font-size:16px;"> 3.1 Data Sources </span>
<a class="anchor" id="3_1"></a>
The data used in this project will come primarily from a data Set [(FitBit Fitness Tracker Data)](https://www.kaggle.com/arashnic/fitbit) available through Mobius and stored in Kaggle. It contains personal fitness trackers from thirty fitbit users. Thirty eligible Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring. It includes information about daily activity, steps, and heart rate that can be used to explore users’ habits.
# <span style="color:#FA8072; font-size:16px;"> 3.2 Accessibility and Privacy</span>
<a class="anchor" id="3_2"></a>
*CC0 1.0 Universal Public Domain Dedication* <br>
The individual who associated a work with this deed has dedicated the work to the public domain by waiving all of their trite to the work worldwide under copyright law, including all related and neighbouring rights, to the extent allowed by law. You can copy, modify, distribute and perform the work, even for commercial purposes, all without asking permission.
# <span style="color:#FA8072; font-size:16px;"> 3.3 Data Organisation and Verification</span>
<a class="anchor" id="3_3"></a>
The dataset contains 18 CSV files. Each file contains quantitative data tracked by the device. Each unique user has data on multiple rows, corresponding to the different dates (total of 31 days per user: 4/12/2016 to 5/9/2016), therefore this data is considered long. A summary table has been included below provided by: [Macarena Lacasa](https://www.kaggle.com/macarenalacasa)

| Table Name | Type | Description |
| --- | --- | --- |
| dailyActivity_merged | Microsoft Excel CSV | Daily Activity over 31 days of 33 users. Tracking daily: Steps, Distance, Intensities, Calories |
|dailyCalories_merged | Microsoft Excel CSV | Daily Calories over 31  days of 33 users |
| dailyIntensities_merged | Microsoft Excel CSV | Daily Intensity over 31 days of 33 users. Measured in Minutes and Distance, dividing groups in 4 categories: Sedentary, Lightly Active, Fairly Active,Very Active |
| dailySteps_merged | Microsoft Excel CSV | Daily Steps over 31 days of 33 users | 
| heartrate_seconds_merged | Microsoft Excel CSV | Exact day and time heartrate logs for just 7 users |
| hourlyCalories_merged | Microsoft Excel CSV | Hourly Calories burned over 31 days of 33 users |
| hourlyIntensities_merged | Microsoft Excel CSV | Hourly total and average intensity over 31 days of 33 users |
| hourlySteps_merged | Microsoft Excel CSV | Hourly Steps over 31 days of 33 users |
| minuteCaloriesNarrow_merged | Microsoft Excel CSV | Calories burned every minute over 31 days of 33 users (Every minute in single row)|
| minuteCaloriesWide_merged | Microsoft Excel CSV | Calories burned every minute over 31 days of 33 users (Every minute in single column)|
| minuteIntensitiesNarrow_merged | Microsoft Excel CSV | Intensity counted by minute over 31 days of 33 users (Every minute in single row) |
| minuteIntensitiesWide_merged | Microsoft Excel CSV | Intensity counted by minute over 31 days of 33 users (Every minute in single column)|
| minuteMETsNarrow_merged | Microsoft Excel CSV | Ratio of the energy you are using in a physical activity compared to the energy you would use at rest. Counted in minutes |
| minuteSleep_merged | Microsoft Excel CSV | Log Sleep by Minute for 24 users over 31 days. Value column not specified |
| minuteStepsNarrow_merged | Microsoft Excel CSV | Steps tracked every minute over 31 days of 33 users (Every minute in single row)|
| minuteStepsWide_merged | Microsoft Excel CSV | Steps tracked every minute over 31 days of 33 users (Every minute in single column) |
| sleepDay_merged | Microsoft Excel CSV| Daily sleep logs, tracked by: Total count of sleeps a day, Total minutes, Total Time in Bed |
| weightLogInfo_merged | Microsoft Excel CSV | Weight track by day in Kg and Pounds over 30 days. Calculation of BMI.5 users report weight manually 3 users not.In total there are 8 users |
# <span style="color:#FA8072; font-size:16px;"> 3.4 Data Credibility and Integrity</span>
<a class="anchor" id="3_4"></a>
There is a possibility of experiencing a sampling bias since we are limited to 30 users and we have no demographic information from the users. Additionally, the data is quite outdated (approximately 6 years old), therefore it is probable that it doesn't give us a good representation of the entire population now.

# <span style="color:#FA8072; font-size:20px;"> 4. Process Phase </span>
<a class="anchor" id="4"></a>
The analysis of the data will be conducted in R due to the large and numerous tables in the dataset.
# <span style="color:#FA8072; font-size:16px;"> 4.1 Installing Packages and Opening Libraries </span>
<a class="anchor" id="4_1"></a>
The following packages will be installed:
* tidyverse
* here
* skimr
* janitor
* lubridate
* ggpubr
* ggrepel

