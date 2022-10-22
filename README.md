# Stock Data Analysis for 2017 & 2018
## Overview of Project
### Background
Steve is working with his parents, who currently have all their money invested into DAQO New Energy Corp, to help inform them of the best green energy stocks to invest in. While he promised to look specifically into DAQO stock, he will analyze a large variety of green energy stocks to diversify their funds. I will be assisting Steve in the analysis of this stock data with Visual Basic for Applications, also known as VBA, which is a programming language built within Excel that allows written, complicated scripts to perform complex analyses and automate tasks.
### Purpose
The purpose of this analysis is to use VBA and refactored code to aid Steve in measuring the total daily volume (total number of shares traded throughout the day; measures how actively a stock is traded) and yearly return (% difference in price from the beginning of the year to the end of the year) for each stock in 2017 and 2018.
## Results
### 2017 Stock Performance vs. 2018 Stock Performance
To calculate the total daily volume and yearly return for each stock in 2017 and 2018, I used the following code, which includes For loops and If-Then statements.<img width="562" alt="For Loops   If-Then Statements" src="https://user-images.githubusercontent.com/107401667/197350881-89358253-813f-404e-a77b-3ebd66528284.png"> The first For loop (2a) tells the computer to run through all twelve positions in the array, tickers(11), <img width="203" alt="Tickers Array" src="https://user-images.githubusercontent.com/107401667/197350923-d9b71d64-3ca4-4853-be63-ae83836e8f7d.png"> . Ticker is the variable that equals this array. Once one ticker is analyzed, the totalVolume for the next tickerIndex is initialized to zero before the totalVolume is calculated. 
The nested For loop (2b) is to run through all the rows in the spreadsheet. It begins on row 2 and ends on RowCount, a variable that returns the row number of the last row in column A that has data. The following code was used to create RowCount:<img width="303" alt="RowCount" src="https://user-images.githubusercontent.com/107401667/197350994-2da9db0a-ce04-4432-8252-790cf47833f1.png"> . This code was taken from https://stackoverflow.com/questions/18088729/row-count-where-data-exists  . 
The first If-Then statement (3a) inside the nested For loop is used to calculate the total daily volume of the specific ticker it is running on. If the current value of that cell is equal to Ticker, then the new totalVolumes(tickerIndex) will equal the current totalVolumes(tickerIndex) plus the total volume for that cell.
To calculate the yearly return of each tickerIndex, I used the following code that is outlined in the first green rectangle. The yearly return is equal to the tickerEndingPrices(tickerIndex) divided by the tickerStartingPrices(tickerIndex) minus one. I then used the second green rectangle of code to change this answer into a percentage. The tickerStartingPrices(tickerIndex) is found with the second If-Then statement (3b) in the nested For loop. If the value of the previous cell does not equal Ticker and the current cell does equal Ticker, then the current cell’s value equals the tickerStartingPrices(tickerIndex). The tickerEndingPrices(tickerIndex) is found with the third If-Then statement (3c) in the nested For loop. If the value of the next cell does not equal Ticker and the current cell does equal Ticker, then the current cell’s value equals the tickerEndingPrices(tickerIndex). <img width="677" alt="Yearly Return" src="https://user-images.githubusercontent.com/107401667/197351602-36cc85ba-9f00-4238-8eb4-a049a7061f33.png"> . 
To help Steve decide which year of data he wants to run the analysis on for total daily volume and yearly return, I used the InputBox() command at the beginning of the code. <img width="438" alt="yearValue" src="https://user-images.githubusercontent.com/107401667/197352010-4701cad5-b4f8-4cf0-965f-920d64fb77e5.png"> The InputBox displays the message, “What year would you like to run the analysis on?” and Steve enters 2017 or 2018. This equals the variable, yearValue, which is used to activate the worksheet with the correct stock data for that year. This line of code is placed before the For loop (2a). <img width="189" alt="yearValue Worksheet Activation" src="https://user-images.githubusercontent.com/107401667/197352074-16baf60b-5c77-4b0e-9681-27db23107f3b.png">
Once Steve chooses the year of stock data he wants to run the code on and the code is ran, the following stock performance results are presented. ![image](https://user-images.githubusercontent.com/107401667/197352117-bf1682c0-e524-4855-8583-c40a2d4d36a4.png) ![image](https://user-images.githubusercontent.com/107401667/197352141-a4e3f589-4eb6-4015-9df1-ccd6a8c803e6.png) The only Ticker that has an increase in both, total daily volume and yearly return, from 2017 to 2018 is RUN. Even though RUN is the only Ticker with an increase in both, multiple Tickers had an increase in total daily volume from 2017 to 2018. This includes HASI, SEDG, TERP, and VSLR. Besides RUN, the only other Ticker to have an increased yearly return from 2017 to 2018 is TERP; however, its yearly return is still in the negatives. If Steve’s parents want to still stay with DQ, I recommend that Steve tries to convince them to at least diversify their funds by investing into RUN too.
### Original Script Execution Time vs. Refactored Script Execution Time
By refactoring the code script, the execution time decreased for 2017 and 2018.  For 2017, the original script execution time is 0.6328125 seconds ![image](https://user-images.githubusercontent.com/107401667/197352329-49916eef-964a-4a4d-8d08-18452f6707ee.png) , while the refactored script execution time is 0.5546875 seconds ![image](https://user-images.githubusercontent.com/107401667/197352346-509cbbad-b2dd-4681-87ea-1416fab1476e.png) . While the original script execution time for 2018 was 0.6914063 seconds, ![image](https://user-images.githubusercontent.com/107401667/197352367-c2e2e792-c912-44fd-910b-144c84adcd5a.png) the refactored script execution time was 0.5390625 seconds ![image](https://user-images.githubusercontent.com/107401667/197352407-62c16d40-0ce3-44e7-a77b-03d3f42be5e8.png) . By combining the differences for each year, Steve saves a total of 0.2304688 seconds. The following is a piece of refactored code that helped save execution time. ![image](https://user-images.githubusercontent.com/107401667/197352423-e5655fab-6b36-4e75-b988-040fa7fdb390.png) . Specifying the tickerIndex value to zero (1a) and initializing the three output arrays with their specfic data types (1b), allows the computer to know how these variables are declared before iterating over all the rows of data. This will allow the computer to accept the correct type of data for the correct variable. 
## Summary
1. What are the advantages or disadvantages of refactoring code?

    A disadvantage of refactoring code is it can be time consuming trying to create the most effective, refactored code. Another possible disadvantage is forgetting to push your changes in Github and losing track of changes you made with the code. Even though these are two disadvantages that exist, refactoring code is beneficial in the long run. It decreases the chances of errors and reduces the time needed to run the analyses, leading to quick and efficient results.
2. How do these pros and cons apply to refactoring the original VBA script?
 
   The con of consuming more time on the code was present, because I had to go back and initialize variables. However, I did not experience the con of forgetting to push my changes in Github. The pro of reducing the time ran for the analysis was applied by incorporating an array of all the tickers. If this was not used, I would have had to type out the code twelve individual times for each ticker. This also decreases the chance of error because I wrote out the code once, rather than writing it out twelve different times and possibly writing it incorrectly one of those times. Lastly, initializing the values and specifying the data types of variables does not leave room for the variables to misinterpreted, thus reducing chances of errors.
