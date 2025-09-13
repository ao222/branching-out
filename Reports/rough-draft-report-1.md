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

# Outline
## Title and Introduction
## Data 
## Methods
## Review
## Tentative schedule and task distribution 

# Forecasting Homelessness: A Community Data Approach
## Background

The OEDC, an economic consortium of developed nations, estimates its member nations have on average 25 people per 10,000 unhoused [source](https://www.oecd.org/en/topics/sub-issues/affordable-housing/homelessness.html). Here in the United States, data from 2024 estimates about 23 people per 10,000 are unhoused [source](https://www.developmentaid.org/news-stream/post/157797/homelessness-statistics-in-the-world). Although it seems other wealthy nations also struggle with housing their most vulnerable populations, one must ask if there is a better way. 

One Finish non-profit said, “The ethical perspective means that homelessness has to be eliminated because human dignity belongs to everyone. A home is a human right,” [source](https://www.goodgoodgood.co/articles/finland-homeless-housing-first-approach). According to research [source](https://nlihc.org/resource/systematic-research-review-finds-benefits-housing-first-programs-us-outweigh-costs) the cost per person per year for homelessness is $18,247 while the cost of Housing First initiatives is $16,479. Therefore, society has both a moral and economic impetus to scale successful initiatives efficiently. Understanding the nature and causes of the homeless population is vital in this effort. 

We will be building a model to predict the size of the homeless population in local areas based on economic and demographic data. We will also identify the importance of each predictor to better understand what impacts the overall size of the homeless population. Identifying these variables could inform policy makers on strategy and policy development to help decrease homelessness. While predicting the number of people suffering homelessness in a local area could help with logistics and planning. 

## Data

Our data was obtained from the project, ‘Predictive Model Based on Homelessness’ located at this [GitHub repo](https://github.com/BU-Spark/ds-ciss-predictive-homlessness/tree/main). The file [Final_Dataset.csv](https://github.com/BU-Spark/ds-ciss-predictive-homlessness/blob/76d8be480f6b32075f4193776988ed61aac92687/Final_Dataset.csv) contains 20 columns prepared by combining various government datasets. Below are tables representing the 20 columns, their descriptions, and their sources. This information was obtained from dataset documentation at the above repo.

### Data Descriptions

| Parameter	| Description |
|----|----|
|Total Population |	Total population of the local area (CoC coded area)|
|Median Gross Rent |	Median gross rent for a 2-bedroom apartment.|
|Median Household Income	| Median household income in the past 12 months.|
|Poverty_Rate	| Poverty rate, indicating the percentage of individuals living below the poverty line.|
|Vacancy_Rate |	Percentage of rental properties that are vacant.|
|Renter_Household_Rate |	Percentage of households that are renter-occupied.|
|Cost_Burdened_Rate |	Percentage of renter households paying more than 30% of their income toward rent.|
|Unemployment_Rate |	Unemployment rate, showing the percentage of the labor force that is unemployed.|
|Total Year-Round Beds (ES, TH, SH) |	the capacity of the homeless service system, number of permanent year-round beds across three program types.|
|Average Temperature |	Average Temp of the local area (??)|
|Overall Homeless |	Homeless population counts|
|Overall Homeless Individuals |	Homeless population counts|
|Overall Homeless People in Families |	Homeless population counts|
|Unsheltered Homeless |	Homeless population counts|
|Sheltered Total Homeless |	Homeless population counts|
|Overall_Homeless_Per_Capita |	Homeless popoulation counts per capita|
|Overall_Homeless_Individuals_Per_Capita |	Homeless popoulation counts per capita|
|Overall_Homeless_People_in_Families_Per_Capita |	Homeless popoulation counts per capita|
|Unsheltered_Homeless_Per_Capita |	Homeless popoulation counts per capita|
|Sheltered_Homeless_Per_Capita |	Homeless popoulation counts per capita|

### Data Sources

|Parameter | Source|
|---------|-----------|
|Total Population |	ACS Table 'B01003_001E'|
|Median Gross Rent |	ACS Table `B25031_004E`|
|Median Household Income |	ACS Table `B19013_001E`|
|Poverty_Rate |	ACS Table `B17001_001E`|
|Vacancy_Rate |	ACS Table `B25004_001E`|
|Renter_Household_Rate |	ACS Table `B25008_001E`|
|Cost_Burdened_Rate |	ACS Table `B25106_006E`, `B25106_010E`, `B25106_014E`, `B25106_018E`|
|Unemployment_Rate |	ACS Table `B23001_001E`|
|Total Year-Round Beds (ES, TH, SH) |	HUD’s Housing Inventory Count (HIC)|
|Average Temperature |	???|
|Overall Homeless |	source11|
|Overall Homeless Individuals |	source12|
|Overall Homeless People in Families |	source13|
|Unsheltered Homeless |	source14|
|Sheltered Total Homeless |	source15|
|Overall_Homeless_Per_Capita |	source16|
|Overall_Homeless_Individuals_Per_Capita |	source17|
|Overall_Homeless_People_in_Families_Per_Capita |	source18|
|Unsheltered_Homeless_Per_Capita |	source19|
|Sheltered_Homeless_Per_Capita |	source20|

## Methods
## Review
## Tentative schedule and task distribution 
