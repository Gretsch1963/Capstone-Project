# US Housing Price Affordability Analysis
Publisher: John Hickman
Date:  November 2023

## Introduction
US housing values have accelerated at paces that has priced many homebuyers out of the market. In addition, incomes have risen on average at a slower annual pace and mortgage interest rates are the highest seen in a generation. According to Urban Institute, homebuyer affordability is at an all-time low. This project examined the inputs into housing affordability for US homebuyers, examining 22 years of housing values and attempts to use data analytics capabilities of MS Excel to predict where homeowner affordability is going based on the housing values, wages and mortgage interest rates. 

## Prerequisites
Microsoft Excel for Mac 16.76 (this analysis was run on a MacOS version of Excel - while there are similarities to versions from other OS, your results may differ). The following add-ons were used. 
- Analysis ToolPak 
- SPC for Excel

# Data Sources
Data from this project has been sourced from https://www.kaggle.com/datasets/robikscube/zillow-home-value-index} {Zillow} via Kaggle, https://fred.stlouisfed.org/series/MORTGAGE30US {St. Louis Federal Reserve Bank} (FRED) and the https://stats.oecd.org/Index.aspx?DataSetCode=AV_AN_WAGE#} {Organization of Economic Co-operation and Development} 

The primary set of data is from Zillow, as cleansed and provided via Kaggle .This dataset is a time series set of data tracking the monthly median home value of a given state produced by Zillow, a real estate data firm.  The data is a composite of each state for each period's housing value with a focus on single family housing. It uses a bread-basket approach of a mix of different property types and property attributes to arrive at this aggregate value versus accumulating actual home sales for the period which may skew housing prices if too many lower value or higher value properties are sold in any given period. The data is structured  in a CSV format that has 285 rows representing 23 years, calculated monthly, of housing price data by state. Each row has 51 records, representing all 50 states and the District of Columbia. The full data set is about 270kb. This is time series data with a date in representing what period the data sample is from. Column headers are alpha characters for the state name. The rest of the data is numeric representing US dollars in xxxxxx.xx format with no thousands separating commas.  The decimal exceeds two places. There are some values missing from early years from some states. The missing data is not expected to impact the analysis. Since the project focuses on aggregate affordability in the US, it is expected that the null values can be ignored without impact to the outcome. The missing state data is infrequent and in less populous states. All other data looks in a fairly standard format. 

In order to assess affordability, a salary data point is needed to determine how the much income the average US home buyer can afford. The salary data has been sourced from The Organisation for Economic Co-operation and Development (OECD). Per the OECD's website it "is an international organisation that works to build better policies for better lives. Our goal is to shape policies that foster prosperity, equality, opportunity and well-being for all. We draw on 60 years of experience and insights to better prepare the world of tomorrow." The OECD provides a hub for data and analysis on a variety of economic data. This salary dataset contains data on average annual wages for full-time and full-year equivalent employees in the total US economy.  The data is calculated by taking all wages earned and dividing it by the average number of employees in the total economy. The total data set includes salary data for countries outside the United States, but for the purpose of this exercise, only the US data will be leveraged. The data is available in a variety of formats, but will be used in CSV format for simplicity of joining the salary data with the housing price data. No data for the period called upon by the housing data was observed to be missing. The data set has more historical records than the Zillow data set. Older records will be ignored for this analysis. 

The final data set used within the model is pricing data on the average 10 year Treasury yields as obtained via the St. Louis Federal Reserve data website, FRED. Treasury yields have  direct correlation on the 30 year fixed mortgage rate with the rate spread mirroring the average mortgage interest rate. The 10-year Treasury yield refers to the interest rate on the 10-year U.S. Treasury bond. It is a key indicator in financial markets and is closely watched by investors, economists, and policymakers. The data is available in a variety of formats. For this purpose, we'll leverage a CSV for purposes of being able to join the data easily with the other data sets described above. The data does not have any missing values and is fairly clean. The data set covers a much larger period than used for this analysis. Older records will be ignored for this analysis. 


## Project Overview
   
- Excel Workbooks/CSV Files:
    1. Analysis File.xlsx - main workbook for cleaned and formatted data, modeling and chart generation. 
    2. MORTGAGE30US.xls - Raw data obtained from St. Louis Fed for Mortgage Interest Rate history 
    3. Salary Data.xls - Raw data obtained from OECD for US Wage Data history
    4. ZHVI.csv - Raw Housing Data from Zillow by time series by state
    5. 10 year Treasury Data.xls - Raw data obtained from St. Louis Fed for Treasury Bill Rate history
  
## Overleaf Report
For a detailed report and in-depth analysis, refer to the Overleaf report at https://www.overleaf.com/read/chmfhtztznrh#069261

## Reference

1. 30-year fixed rate mortgage average in the united states. https://fred.stlouisfed.org/series/MORTGAGE30US, accessed: November 12, 2023
2. Average annual wages dataset. https://stats.oecd.org/Index.aspx?DataSetCode=AV_AN_WAGE#, accessed: November 12, 2023
3. Market yield on u.s. treasury securities at 10-year constant maturity, quoted on an investment basis dataset. https://fred.stlouisfed.org/series/GS10, accessed: November 12, 2023
4. Zillow home value index dataset. https://www.kaggle.com/datasets/robikscube/zillow-home-value-index, accessed: November 12, 2023
5. HUD: Defining housing affordability (2017), https://www.huduser.gov/portal/pdredge/pdr-edge-featd-article-081417.html#:~:text=Keeping%20housing%20costs%20below%2030,to%20be%20housing%20cost%20burdened., accessed:Novermber 19, 2023
6. Institute, U.: Housing finance at a glance monthly chartbook october 2023 (2023), https://www.urban.org/sites/default/files/2023-10/Housing%20FinancezAt%20a%20Glance%20Monthly%20Chartbook-October%202023.pdf, accessed: Novermber 19, 2023
