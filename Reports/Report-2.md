## Task Schedule

| Week Number  | Original Due Date   | Task| Completed Date | Pending Due Date |
|--------------|------------|------|----------|---------|
| Week 1       | Sept. 27th | Gather ACS Tables| Oct. 31 | |
|        |  | Merge ACS Tables, Coc Counts, NOAA Weather Data| Oct. 31| |
| Week 2       | Oct. 4th   | Create Per Capita and other Features| Oct. 31| |
|        |    | Determine Type of Variables| Nov. 8| |
|        |    | Identify outliers and any data issues| Nov. 8| |
|        |    | Apply Transformations| Nov. 8| |
|        |    | Handle missing values| Nov. 8| |
|        |    | Describe data variable statistics| Nov. 8| |
| Week 3       | Oct. 11th  | Visualize Data| Nov. 8 | |
|        |   | Point out interesting relationships and patterns from visualizations| Nov. 8 | |
| Week 4       | Oct. 18th  | 5 page Write-Up| Nov. 8 | |
| **Report 2**     | **Oct. 25th**  |   | Nov. 8 | |
| Week 5       | Oct. 25th  | Explain CatBoost, Extra Trees Regressor, and K-Neighbors Regressor Include model assumption advantages and disadvantages of each method | | Nov. 19 |
| |            | Describe any feature creation|| Nov. 19 |
|        |   | Explain the selection process and cross-validation used|| Nov. 19 |
|        |   | Explain bias variance trade-off|| Nov. 19 |
| Week 6       | Nov. 1st   | Construct CatBoost Model|| Nov. 19 |
|        |    | Construct Extra Trees Regressor Model|| Nov. 19 |
|        |    | Construct K-Neighbors Regressor Model|| Nov. 19 |
| Week 7       | Nov. 8th   | Tune Model Hyperparameters|| Nov. 19 |
|        |    | Interpret model coefficients and feature importance|| Nov. 19 |
| Week 8       | Nov. 15th  | 5 Page Write-Up|| Nov. 19 |
| Week 9       | Nov. 23rd  | Presentation Slides|| Nov. 19 |
| **Presentation** | **Nov. 23rd**  |   || Nov. 19 |
| **Final Report** | **Nov. 30th**  |   |

There was significant modification to the original plan, including reduced scope and due dates moved. These modifications were caused by significant unforseen complexities in obtaining the dataset. The revised plan with updated due dates is above along with current completed tasks.

## Acquiring PIT Count Data
The file [PIT_count_preparation.ipynb](Notebooks/PIT_count_preparation.ipynb) acquires annual Point-in-Time (PIT) Homeless Count data.  Sourced from a downloaded excel file (2007-2024-PIT-Counts-by-CoC.xlsb). The script uses the pandas library to read all sheets and then iterates through them, selecting sheets with year names between 2009 and 2024. For each selected year, a 'year' column is added. The data from these annual sheets is then concatenated, and a specific subset of nine key columns is selected to create a new dataset. The script cleans this dataset by dropping rows with more than four missing values to remove non-CoC-count information. Finally it saves the dataset into a CSV file.

## Acquiring HIC Count Data
The [HIC_count_preparation.ipynb](Notebooks/HIC_count_preparation.ipynb) file processes annual Homeless Inventory Count (HIC) data. The data from 2007 to 2024 is from a multi-sheet Excel file named 2007-2024-HIC-Counts-by-CoC.xlsx. Using the pandas library, the code iterates through each sheet extracting the relevant data, and renames the first two columns. Next, the code adds a column to each DataFrame saving the year information. The DataFrames representing each year are concatenated into a single DataFrame called HIC_count. Finally, the dataset is saved to a CSV file named "hic_counts.csv".

## Acquiring ACS Data

The Jupyter Notebook, [Acquire_ACS_Data.ipynb](Notebooks/Acquire_ACS_Data.ipynb), acquires, validates, and processes American Community Survey (ACS) demographic and housing indicators from the U.S. Census Bureau API. This output enables the application of advanced machine learning techniques.

### Methodology and Validation

The download_variables function serves as the foundation for the acquisition process. This function executes the numerous required API calls by generating the full Cartesian product of all desired ACS variables and the targeted time period. The function then unifies the raw results into a single dataframe, indexed by identifiers (GEOID and Year). The function find_all_missing_years validates the documented variables by comparing the expected variables with the retrieved metadata. This process signifies which variables require alternative calculation strategies.

### Addressing Missing Years

The calculation of Median Rent for a 2-bedroom apartment was the most significant complexity addressed for these variables. Since the direct ACS variable (B25031_004E) was absent for the initial years (2009–2014), the notebook downloaded a related set of variables that provide grouped frequency data (counts of units within discrete rent brackets) and applied the standard linear interpolation formula for grouped data: 
$$Median = L + \frac{\frac{n}{2} - F}{f} \times w$$
This statistical method provided a median estimate for the missing period, which the notebook subsequently affirmed by comparison with the actual ACS-reported values during the years of overlap.
Other variables needing correction were the Poverty Rate, Vacancy Rate, and Renter Occupied Rate, which were mathematically constructed by summing their component count variables.

The notebook addressed inconsistencies in the Rent Burdened Rate, a measure of renter households paying over $30\%$ of income toward rent, by correcting for a documentation error that mistakenly referenced owner-occupied units. The function find_all_missing_years indicated that the corrected variables were missing from 2009. The notebook downloads other consistently available variables. 
The final, and perhaps most granular, effort involved the Unemployment Rate, which lacked data for the 2009-2010 period. To produce a seamless dataset, the notebook manually aggregated and summed the counts of the unemployed and the labor force across numerous age and gender-specific cohorts to reconstruct the total figures for the missing years.

The culmination of this entire notebook is the production of a single, unified ACS_data.csv DataFrame. This consolidated resource represents a validated, temporally consistent, and reproducible input dataset.
