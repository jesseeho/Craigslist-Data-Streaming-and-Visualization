# CSDA1050-CAP: Craigslist Housing

## Steps to Reproduce

### Step 1 - Craiglist Scraper API
Run the Craiglist Scraper and Multiple File Concatenation.ipynb script

This script has two components:

1) The first component is the Craiglist python API by MIT-Zero which scrapes the website for all real estate listed for sale in Toronto, ON. A maximum of 3000 listing could be pulled per instance. Library: (https://pypi.org/project/python-craigslist/)

2) The concatenation code will combine all .csv files resulting from the scraper in a given folder intoa single combined .csv file. 
Note: There will be duplicate entries as the turnover period for listings is relatively long.

### Step 2 - Craiglist Housing EDA
Run the CL Housing Exploratory Data Analysis (EDA).ipynb script

This script removes duplicate entries based on id number and applies the appropriate data type transformation to fields. The following transformations were completed:

#Geolocation was separated into two fields: latitude and longitude coordinates

#Datetime was separated into date

#Area was separated into value and unit of measurement

#Text column was created from the title by removing emojis and non-latin characters
Data Preparation:

#Missing values were identified using missmap and missing information was extracted from other fields to fill NAN values. It was 	       found that many prices, bedrooms and square footage values were missing (these are critical to real estate analysis).

#Regex functions were used to extract dollar values and bedrooms from the text field. These extracted values were used to fill in NAN    values or dollar values under $2 for price and any missing bedroom information.

#Filtering: rental listing were found in the dataset and were removed by filtering out prices <$100,000. Additionally, listing that      were posted in Toronto region but were for foreign investments were removed by filtering by latitude values within the range of         (43.00000 – 43.900000).

#The resulting dataframe only had missing values in square footage. This could prove to have an significant impact to my analysis. No    method of extracting square footage from other features could be found.

#Identifies outliers and removes them

The final results is a cleaned.csv file that is created in your designated location.

### Step 3 - Craiglist Housing Detailed Analysis
Run the CL Housing Detailed Analysis.ipynb script

This script creates geodataframes using Shapediles and census data extracted from Simply Analytics and from the cleaned dataset produced in step 2 of this document. Some geospatial analysis is done to understand the data and a scoreing system of affordability of listing by neighbourhood is produced. The scoring function can be easily amended (where indicated in the script) to allow for different analysis.

Source: https://simplyanalytics.com/

