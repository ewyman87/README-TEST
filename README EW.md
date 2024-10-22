# Project 1 - Tech Stock Analysis
## This is an analysis of 3 tech stocks in order to make a purchase recommendation to client 

!['The Quants'](Tech_pic_main.png)





<p align="center">
DISCLOSURE:
<p align="center">
No guarantee can be offered that projections or estimates will actually occur. Actual results may be materially different from projections or estimates. Additionally, past performance should not be relied upon as a forecast of future performance.



## PROJECT DESCRIPTION

**Equity Trading**

While working for The Quants, a large equity-trading company,  your team is tasked with researching a client’s portfolio. Your client wants to invest in tech stocks and needs expert analysis to make the right decision. 

Using NASDAQ historical data, we need to pull five year’s worth of trading data for the major US technology companies: Apple, Microsoft, and Google and compare their historical performance to each other and to the S&P 500 and NASDAQ indexes.

Our goals:  
1. Analyze which stocks are trending upward.  
2. Which are trending downward.  
3. Based on the data, what would you recommend to your client?  
4. How does the tech stock performance compare to the S&P and [NASDAQ](https://www.nasdaq.com/market-activity/quotes/historical) indexes?

## INSTALLATION

1. Ensure you have Python 3.10 or higher installed.
2. Clone this repository: `git clone https://github.com/Pete1001/Tech_stock_analysis.git`
3. Ensure to run '!pip install prophet' at beginning of code

## USAGE

1. Run the project: `Tech_stock_analysis.ipynb`

## DATA PROCESSING:

1. Data Collection: 5 years of daily close data was downloaded from https://www.nasdaq.com/ for each of the stocks (Apple, Google, Microsoft) and both of the indexes (NASDAQ and S&P 500) resulting in 5 .csv files.

2. Data Exploration: After the 5 .csv files were read in as DataFrames and each file was explored through the info() method.  This method revealed that there were no null values and the files for the indexes had 1 less row.  Additionally, the closing price was read in as an object in the three stock since there was a dollar sign ($) included in the price.   

3. Data Cleanup:  
    - Closing price columns were renamed to reference the stock or index   
    - Merge files with only needed columns (closing price columns)  
    - Remove replace() method was used to replace $ with ’’  
    - Change data type from object to float by using the astype() method



**Historical Trends**

    Apple:
    -Industry – Computer Manufacturing
    -5 year performance  - 250% increase
    -Share volume – 19,342,616
    -Current yield – 0.44%
    
    Summary Statistics:
    Mean -  $146.07
    Standard Deviation - $41.33
    

    Microsoft:
    -Industry – Computer Software
    -5 year performance  - 245% increase
    -Share volume – 9,090,960
    -Current yield – 0.72%
    
    Summary Statistics:
    Mean - $281.25
    Standard Deviation - $80.22


    Google (Class A):
    -Industry – Computer Software
    -5 year performance  - 174% increase
    -Share volume – 21,606,095
    -Current yield – 0.49%
    
    Summary Statistics: 
    Mean - $113.88
    Standard Deviation - $31.75

**Correlation and 2024 Trends**  
The correlation matrix shows how the daily returns of Microsoft, Apple, and Google relate to each other in 2024.  

- Microsoft and Apple (0.46): There’s a moderate positive relationship, meaning they sometimes move in the same direction but not strongly aligned.  
- Microsoft and Google (0.61): A stronger positive relationship, indicating that their returns tend to move together more often.  
- Apple and Google (0.39): A weak positive relationship, showing that their returns are relatively independent.  

Although historically all three stocks have an upward trend, more recently (October) the trends are downward.

**Cumulative Returns - 2024**  
- A special function of Pandas called .cumprod() calculates a cumulative returns of the stock.  
- From the analysis of the graph we would expect Apple to have the best growth rate.  
- Additionally, the Google and Apple stocks show more price volatility.   

**Forecast and Expected Growth**  
    
    Apple:
        -The time series forecast for Apple shares shows an upward trend for the next 90 days. 
        -The forecast predicts that the Apple share price will increase 5.4% over the next 90 days.
    
    Microsoft:
        -The time series forecast for Microsoft shares shows an upward trend for the next 90 days. 
        -The forecast predicts that the Google share price will increase 10.4% over the next 90 days.

    Google (Class A):
        -The time series forecast for Google (class A) shares shows an upward trend for the next 90 days. 
        -The forecast predicts that the Google share price will increase 5.4% over the next 90 days.


### APPROACH IN ACHIEVING PROJECT GOALS:

**Stocks**  
1. Look at historical trends for the 3 stocks and determine if we were seeing an upward or downward trend.  
2. We wanted to understand if there was a correlation between any of the 3 stocks.  
3. We wanted to get a closer look at the trends for 2024 only.  
4. The team reviewed cumulative returns.  
5. Prophet was used to forecast expected stock price over the next 90 days and a growth rate calculated from the forecast along with plotting components.  

**Indexes**  
To understand how the stock performance compared to index performance, we also forecasted expected performance using Prophet and calculated an expected growth rate

### RECOMMENDATIONS:

1. By using Prophet we’re able to forecast forward 90 days and measure the expected growth rate of each stock and index.  
    - Microsoft had the highest expected growth rate at 10.4%  
    - Apple and Google had lower expected growth at 5.4%    
    - NASDAQ and S&P indexes had 9.2% and 9.1%, respectively  

2. Historically, October had the lowest expected stock price for Microsoft as shown through .plot_components() method.  
    - This indicates a potentially good time to purchase Microsoft stock

3. The highest projected growth stock is Microsoft.

### PROBLEMS ENCOUNTERED:

Collaborating with Jupyter notebook and GitHub was clunky and troublesome and lead to a number of conflicts identified when trying to merge to main branch.  
- To resolve the team divided coding into sections assigned to specific team members  
- The team also coordinated changes to the code and upload to GitHub during meetings  
- This is a known issue as identified and corrected by NBDEV

During review of the output of .plot_components() the team recognized that the weekly graph looked the same for all stocks  
- The team identified that a forecasting with Monday through Friday data lead to the same graphs  
- The resolution was to turn off weekly seasonality in the Prophet model and adjust the prediction DataFrame to remove weekend days using the following code:  
    - model = Prophet(weekly_seasonality=False)  
    - future_trends = future_trends[future_trends[‘ds’].dt.weekday <5]  

### FUTURE CONSIDERATIONS:

- Impacts of research and development.
- Compare to non-technology stock performance.

## REFERENCES
1. https://www.nasdaq.com/market-activity/quotes/historical

2. GOOGLE COLAB & GENERATIVE AI

3. https://github.com/you915/Sentiment-Analysis-of-Twitter-Data-for-predicting-Apple-stock-price.git  

4. https://bootcampspot.instructure.com/


## TEAM MEMBERS
1. Mark Johnson
2. Pete Link
3. Marianne Mittelstadt
4. Steve Vierling
5. Ethan Wyman


## LICENSE
This project is licensed under The Quants.