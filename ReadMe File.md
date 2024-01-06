Death And Taxes Readme


Executive Summary
Embarking on the exploration of the enduring idea that life's only certainties are death and taxes, this project seeks to unveil whether there's a significant connection between individuals' tax contributions and their life expectancy. I am particularly intrigued by the prospect of understanding if there are variations in life expectancy between regions with different tax burdens. Through the examination of various tax categories—federal, state, property, and sales, etc.—the aim is to determine how taxes might influence life expectancy. Beyond these considerations, the project also plans to delve into the intricate dynamics of how government spending from tax revenues might impact life expectancy, especially in critical areas like healthcare and social programs. Acknowledging the inherent complexity, this effort is driven by the desire to comprehensively grasp the relationship between taxes and life expectancy in a straightforward and accessible manner.

Motivation
My motivation for this project stems from a curiosity sparked by the commonly heard phrase "death and taxes." Repeated over the course of my life, like many others, I had simply accepted these concepts as inevitable certainties. However, upon reflecting on this expression, I began to question the underlying assumption. Taxes, ostensibly, are intended to enhance our quality of life. Therefore, the logical connection would suggest that an increase in taxes could lead to an improvement in quality of life, subsequently increasing life expectancy. If this assumption doesn't hold true, it raises the intriguing possibility that we might be figuratively taxed to death. In such a scenario, understanding how tax dollars are being spent becomes crucial to unraveling this complex relationship.

Data Question
• What is the relationship, if any, between taxes and regional mortality?
• Do higher or lower taxes influence life expectancy?
• How do specific types of taxes, such as federal, state, property, and sales taxes, affect life expectancy?
• In what ways does the government's allocation of tax money impact life expectancy?

Minimum Viable Product (MVP)
1.	Create a storyboard using PowerBI that shows if there is a correlation between different types of taxes and regional life expectancy.
2.	As best as possible, show correlation between different types of taxes such as sales tax, estate tax, income tax, etc. 
3.	Include in the storyboard data a breakdown that shows what percent of tax money is spent on various categories such as medical services, road, police, housing, etc. 
4.	Have the storyboard be interactive so that user is able to select certain types of taxes or government expenditures to see their effect on life expectancy.

Schedule (through 1/4/2023)
1.	Get the Data (11/24/2023)
2.	Clean & Explore the Data (12/4/2023 -12/08/2023)
3.	Create Presentation of your Analysis (12/20/2023)
4.	Internal demos (1/2/2024)
5.	Demo Day!! (1/04/2024)

Data Sources
Download Center: StatsAmerica
https://taxfoundation.org/data/all/state/sales-tax-rates-2019/
https://taxfoundation.org/data/all/state/state-individual-income-tax-rates-brackets-2019/
https://www.irs.gov/statistics/soi-tax-stats-individual-income-tax-statistics-2019-zip-code-data-soi
https://www.census.gov/data/datasets/2019/econ/local/public-use-datasets.html
https://www.census.gov/data/tables/2019/econ/qtax/historical.html


Known Issues and Challenges
•	Many of the files from the IRS website are .xlsx files types that will require converting to be usable.
•	Tax data is massive and can be broken down into many different categories as well as income brackets. For this reason, determinations will have to be made whether to average out all the tax information for a region or attempt to break it down by specific income brackets. Most likely it will need to be averaged out across all the income brackets. This also makes sense because it might not be possible to find mortality rate by income bracket.  
•	Because tax rates change on a yearly basis, and are different between regions, it is best to do this study over a single year instead of multiple years. While there will be small changes affecting that year, because taxes are always changing, this still works better than looking at rates over multiple years where changes might be more drastic.
•	Because of covid and its effect on mortality from 2020 onward, it is best to pick a year prior to covid for this study. For this I will be using data from 2019 as it is still relatively recent, but the mortality rate has not been skewed by a pandemic. Also, because the data is several years old it is more readily available. 



Creation of the following file folders inside primary folder is recommended in order to correctly run code
"notebooks"
"images"
"data"
"cleaned_data"
".ipynb_checkpoints"
All data downloaded from various data sources websites should be placed inside "data" folder.
See data sources listed above


Running code:
All python notebooks can be found in the "notebooks" folder
It is recommended to run notebooks in the suggeted order as the .csv files generated from one notebooks will be used in later notebooks.


Run 1st.
    "population_notebook" contains all population data and is organized using state and county fips codes. 
Data for this notebook comes from the following .csv files located in the "data" folder
(data/Population_estimates_US_States_Counties.csv) 
(data/CEW - US, States, Counties - Total Ownership.csv) 
(data/Components of Population Change - US, States, Counties.csv) 
(data/fips_table.csv) 
(data/IHME_USA_LE_COUNTY_RACE_ETHN_2000_2019_LT_2019_BOTH_Y2022M06D16.CSV) 
(data/Population by Age and Sex - US, States, Counties.csv)


Run 2nd.
    "state_returns_notebook" contains information related to individual tax returns aggreagated by region
data for this notebook is from  https://www.irs.gov/statistics/soi-tax-stats-individual-income-tax-statistics-2019-zip-code-data-soi website using the .xlsx file
In order to correctly read run this code in python the file must first be opened in excel and alterations be made. On row 4, starting at column U the cell must be ungrouped. The ungrouped cell must then be duplicated and pasted into the empty cell to the right of it. Finally, The orignal cell must be modified so that " #" immediatly follows any words. 
EXAMPLE: Cell U:4 = Total income # Cell V:4 = Total income. 
This must be done for any column where in row 5 the column states "amount" or "number of returns"
The purpose of this is python has a difficult time handling columns with the same name. By adding a " #" to the column title, python is then able to distinquish the name and apply any changes to columns only containg a "#" value.


Run 3rd.
    "state_finances_notebook" contains information related to state revenue and expenditure information. 
Data from notebook comes from https://www.census.gov/data/datasets/2019/econ/local/public-use-datasets.html using the .xlsx "US summary & State Estimates Tables."
 Minor changes to .xlsx file will need to be made for ease of use in python. 
Column B rows 17:77 - the word "revenue" should be added to the end of the description if the word "revenue" does not already exist in the description. 
Column B rows 81:168 - the word "expenditure" should be added to the end of the description if the word "expenditure" does not already exist in the description. 
The following rows should be the sum of the rows below for columns C-JB
98 is the sum of 99-106
108 is the sum of 109-117
119 is the sum of 120-124
126 is the sum of 127-131
144 is the sum of 145-149
151 is the sum of 152-153


Run last
    "master_table_notebook" contains all the cleaned tables from all the other notebooks combined. This notebook must be run last as it utlizes the .csv files generated from the other notebooks. AS this is the final notebook, the .csv file generated from this notebook will be used to create the Tableau dashboard. 