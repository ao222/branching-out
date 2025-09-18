# Directions and Requested Word Count

## Title and Introduction
(2 points): Describing background information and importance of each problem
1.33 PAGES
370 Words


## Data 
(1 point): Choosing and describing dataset(s) (no need for coding at this stage). Explain how the data is collected. Mention the number of observations and variables, and the description of each variable.
.66 PAGES
185 Words


## Methods
 (2 points): Description and justification of the methods
1.33 PAGES
370 Words


## Review
 (3 points): Review of earlier results with similar datasets. You need to cite these works at the end of the report.
2 PAGES
560 Words


## Tentative schedule and task distribution 
(1 point): Task distribution among the members. Tentative start and end date of each task. 
.66 PAGES
185 Words


## Organization (1 point):
 The structure and placement of the content should be at a good academic level. The report should be 5-6 pages.

# Forecasting Homelessness: A Community Data Approach
## Background

The OEDC, an economic consortium of developed nations, estimates its member nations have on average 25 people per 10,000 unhoused [source](https://www.oecd.org/en/topics/sub-issues/affordable-housing/homelessness.html). Here in the United States, data from 2024 estimates about 23 people per 10,000 are unhoused [source](https://www.developmentaid.org/news-stream/post/157797/homelessness-statistics-in-the-world). Although it seems other wealthy nations also struggle with housing their most vulnerable populations, one must ask if there is a better way. 

One Finish non-profit said, “The ethical perspective means that homelessness has to be eliminated because human dignity belongs to everyone. A home is a human right,” [source](https://www.goodgoodgood.co/articles/finland-homeless-housing-first-approach). According to research [source](https://nlihc.org/resource/systematic-research-review-finds-benefits-housing-first-programs-us-outweigh-costs) the cost per person per year for homelessness is $18,247 while the cost of Housing First initiatives is $16,479. Therefore, society has both a moral and economic impetus to scale successful initiatives efficiently. Understanding the nature and causes of the homeless population is vital in this effort. 

We will be building a model to predict the size of the homeless population in local areas based on economic and demographic data. We will also identify the importance of each predictor to better understand what impacts the overall size of the homeless population. Identifying these variables could inform policy makers on strategy and policy development to help decrease homelessness. While predicting the number of people suffering homelessness in a local area could help with logistics and planning. 

## Data

Our data was obtained from the project, ‘Predictive Model Based on Homelessness’ located at this [GitHub repo](https://github.com/BU-Spark/ds-ciss-predictive-homlessness/tree/main). The file [Final_Dataset.csv](https://github.com/BU-Spark/ds-ciss-predictive-homlessness/blob/76d8be480f6b32075f4193776988ed61aac92687/Final_Dataset.csv) contains 20 columns prepared by combining various government datasets. Below are tables representing the 20 columns, their descriptions, and their sources. This information was obtained from dataset documentation at the above repo.

### Data Descriptions
| Parameter	| Description | Sources |
|----|----|----|
|Total Population |	Total population of the local area (CoC coded area)|ACS Table 'B01003_001E'|
|Median Gross Rent |	Median gross rent for a 2-bedroom apartment.|ACS Table `B25031_004E`|
|Median Household Income	| Median household income in the past 12 months.|ACS Table `B19013_001E`|
|Poverty_Rate	| Poverty rate, indicating the percentage of individuals living below the poverty line.|ACS Table `B17001_001E`|
|Vacancy_Rate |	Percentage of rental properties that are vacant.|ACS Table `B25004_001E`|
|Renter_Household_Rate |	Percentage of households that are renter-occupied.|ACS Table `B25008_001E`|
|Cost_Burdened_Rate |	Percentage of renter households paying more than 30% of their income toward rent.|ACS Table `B25106_006E`, `B25106_010E`, `B25106_014E`, `B25106_018E`|
|Unemployment_Rate |	Unemployment rate, showing the percentage of the labor force that is unemployed.|ACS Table `B23001_001E`|
|Total Year-Round Beds (ES, TH, SH) |	the capacity of the homeless service system, number of permanent year-round beds across three program types.|HUD’s Housing Inventory Count (HIC)|
|Average Temperature |	January Average Temperature of the encompassing state| National Centers for Environmental Information (NOAA) |
|Overall Homeless |	All people experiencing homelessness| HUD's Point in Time Count|
|Overall Homeless Individuals |	People experiencing homelessness not in a family| HUD's Point in Time Count|
|Overall Homeless People in Families |	People experiencing homelessness part of a family unit| HUD's Point in Time Count|
|Unsheltered Homeless |	People experiencing homelessness unsheltered |HUD's Point in Time Count|
|Sheltered Total Homeless |	People experiencing homelessness in shelters| HUD's Point in Time Count|
|Overall_Homeless_Per_Capita |	People experiencing homelessness counts per capita| HUD's Point in Time Count|
|Overall_Homeless_Individuals_Per_Capita |	People experiencing homelessness counts per capita| HUD's Point in Time Count|
|Overall_Homeless_People_in_Families_Per_Capita |	People experiencing homelessness counts per capita| HUD's Point in Time Count|
|Unsheltered_Homeless_Per_Capita |	People experiencing homelessness popoulation counts per capita| HUD's Point in Time Count|
|Sheltered_Homeless_Per_Capita |	People experiencing homelessness popoulation counts per capita| HUD's Point in Time Count|

### Data Details

#### ACS Tables
The American Community Survey, produced by the Census Bureau, carries out 3.5 million surveys each year and is the leading survey informing federal policy. It releasese three data products: 1 year estimates, 1 year supplemental estimates, and 5 year estimates. These three products represents geographies of 65,000 for the 1 year estimates, geographies of 20,000 for the 1 year supplemntal estimates, and drills down to neighborhood-level and rural counties for the 5 year estimates. In this project we rely on the 1 year supplemental estimates **(TODO: confirm we use supplemental and not 1 year estimates).** The ACS ask questions regarding a wide area of topics in categories of social, economic, demographic, and housing. These areas are delimitted below.

|Social|Economic|Demographic|Housing|
|------|--------|-----------|-------|
Ancestry|Class of Worker|Age|Computer & Internet Use
Citizenship|Commuting|Hispanic Origin|Costs (Mortgage, Rent, Taxes, Insurance)
Citizen Voting Age Population|Employment Status|Race|Heating Fuel
Disability|Food Stamps (SNAP)|Relationship|Home Value
Educational Attainment|Health Insurance|Sex|Occupancy
Fertility|Hours/Week, Weeks/Year| |Plumbing/Kitchen Facilities
Grandparents|Income| |Structure
Language|Industry & Occupation| |Tenure (Own/Rent)
Marital Status| | |Utilities
Migration| | |Vehicles
School Enrollment| | |Year Built/ Year Moved In
Veterans| | |

#### Housing Inventory Count (HIC)

The Housing Inventory Count (HIC) is a snapshot of all the programs within a Continuum of Care (CoC) that offer beds and units specifically for people experiencing homelessness. For permanent housing projects, this includes people who were homeless when they first entered, based on HUD’s definition. The inventory is organized into five program types: Emergency Shelter, Transitional Housing, Rapid Re-Housing, Safe Haven, and Permanent Supportive Housing [https://www.hudexchange.info/programs/hdx/pit-hic/#2025-pit-count-and-hic-guidance](https://www.hudexchange.info/programs/hdx/pit-hic/#2025-pit-count-and-hic-guidance)

#### Point-in-Time Count (PIT)

The Point-in-Time (PIT) Count is a one-night snapshot in January of how many people are experiencing homelessness, both sheltered and unsheltered. HUD requires Continuums of Care (CoCs) to conduct this count each year for people staying in emergency shelters, transitional housing, and Safe Havens. In addition, CoCs must count unsheltered individuals every other year (in odd-numbered years). Each community is responsible for planning, organizing, and carrying out the count locally. [https://www.hudexchange.info/programs/hdx/pit-hic/#2025-pit-count-and-hic-guidance](https://www.hudexchange.info/programs/hdx/pit-hic/#2025-pit-count-and-hic-guidance)

#### NCEI

NOAA’s statewide temperature data come from thousands of weather stations, checked for accuracy and adjusted for changes in equipment or location. These readings are mapped onto a fine grid and averaged to give reliable monthly statewide values, providing a consistent record of U.S. climate back to 1895.

## Methods

A preliminary run by PyCaret produced the following table. 
### Leaderboard
Model|MAE|MSE|RMSE|R2|RMSLE|MAPE|TT (Sec)
|----|---|---|----|--|-----|----|-------|
CatBoost Regressor|0.0005|0.0|0.0008|0.7869|0.0008|0.3289|3.692
Extra Trees Regressor|0.0004|0.0|0.0008|0.7798|0.0008|0.3294|0.28
Light Gradient Boosting Machine|0.0005|0.0|0.0009|0.7468|0.0009|0.3464|0.316
Random Forest Regressor|0.0005|0.0|0.0009|0.7315|0.0009|0.3481|0.57
Gradient Boosting Regressor|0.0006|0.0|0.001|0.6686|0.001|0.4305|0.278
K Neighbors Regressor|0.0006|0.0|0.001|0.6583|0.001|0.4306|0.08
Decision Tree Regressor|0.0006|0.0|0.0013|0.4422|0.0013|0.4105|0.048
Bayesian Ridge|0.0009|0.0|0.0015|0.3382|0.0014|0.7461|0.022
Least Angle Regression|0.0009|0.0|0.0015|0.3381|0.0014|0.7462|0.028
Ridge Regression|0.0009|0.0|0.0015|0.3381|0.0014|0.7462|0.044
Linear Regression|0.0009|0.0|0.0015|0.3381|0.0014|0.7462|9.166
Orthogonal Matching Pursuit|0.001|0.0|0.0016|0.2296|0.0016|0.847|0.024
Huber Regressor|0.0009|0.0|0.0016|0.1986|0.0016|0.568|0.036
Lasso Regression|0.0012|0.0|0.0018|-0.0018|0.0018|1.0766|1.94
Elastic Net|0.0012|0.0|0.0018|-0.0018|0.0018|1.0766|0.038
Lasso Least Angle Regression|0.0012|0.0|0.0018|-0.0018|0.0018|1.0766|0.028
Dummy Regressor|0.0012|0.0|0.0018|-0.0018|0.0018|1.0766|0.024
AdaBoost Regressor|0.0017|0.0|0.0019|-0.1044|0.0019|1.8322|0.138
Passive Aggressive Regressor|0.0018|0.0|0.0026|-1.0549|0.0025|1.0|0.026
## Review
## Tentative schedule and task distribution 
