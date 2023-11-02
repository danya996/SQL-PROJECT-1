Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
SELECT SUM(ALS.totalTransactionRevenue / 1000000), ALS.COUNTRY, ALS.CITY
FROM ALL_SESSIONS ALS
WHERE ALS.COUNTRY != '(not set)' AND ALS.CITY != '(not set)' AND ALS.CITY != 'not available in demo dataset' AND ALS.totalTransactionRevenue IS NOT NULL
GROUP BY ALS.COUNTRY, ALS.CITY
ORDER BY SUM(ALS.totalTransactionRevenue / 1000000) DESC


Answer: USA has highest level of transaction revenue, 
        top cities are San Francisco, Sunnyvale, Altanta




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries: 
SELECT SBQ.COUNTRY, SBQ.CITY, ROUND(AVG(SBQ.productQuantity),2)
FROM(
SELECT SUM(ALS.productQuantity) AS productQuantity , ALS.COUNTRY, ALS.CITY
FROM ALL_SESSIONS ALS
WHERE ALS.COUNTRY != '(not set)' AND ALS.CITY != '(not set)' AND ALS.CITY != 'not available in demo dataset' AND ALS.productQuantity IS NOT NULL
GROUP BY ALS.COUNTRY, ALS.CITY
) SBQ
GROUP BY SBQ.COUNTRY, SBQ.CITY
ORDER BY AVG(SBQ.productQuantity) DESC

Answer:  Spain has the highest average, followed by USA
         Madrid has the highest average, followed by Salem




**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:
SELECT SUM(ALS.productQuantity) AS CNT, ALS.COUNTRY, ALS.CITY, ALS.v2ProductCategory
FROM ALL_SESSIONS ALS
WHERE ALS.COUNTRY != '(not set)' 
  AND ALS.CITY != '(not set)' 
  AND ALS.CITY != 'not available in demo dataset' 
  AND ALS.productQuantity IS NOT NULL 
GROUP BY ALS.COUNTRY, ALS.CITY, ALS.v2ProductCategory
ORDER BY SUM(ALS.productQuantity) DESC


Answer: the top categories of prodcuts are bags, Nest-USA, Drinkware

**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:
SELECT SBQ.COUNTRY, SBQ.CITY, SBQ.v2ProductName, MAX(CNT_SOLD)
FROM (
  SELECT SUM(ALS.productQuantity) AS CNT_SOLD, ALS.COUNTRY, ALS.CITY, ALS.v2ProductName 
  FROM ALL_SESSIONS ALS
  WHERE ALS.COUNTRY != '(not set)' 
  AND ALS.CITY != '(not set)' 
  AND ALS.CITY != 'not available in demo dataset' 
  AND ALS.v2ProductName != '(not set)'
  AND ALS.productQuantity IS NOT NULL 
  GROUP BY ALS.COUNTRY, ALS.CITY, ALS.v2ProductName
) SBQ
GROUP BY SBQ.COUNTRY, SBQ.CITY, SBQ.v2ProductName

Answer:  the top three are wazed dress socks, google note book reused shopping bags.



**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries: 
SELECT SUM(Als.totalTransactionRevenue / 1000000) AS SUM_TOTAL, Als.COUNTRY, Als.CITY
FROM ALL_SESSIONS als
WHERE Als.COUNTRY != '(not set)' AND Als.CITY != '(not set)' AND Als.CITY != 'not available in demo dataset'
GROUP BY Als.COUNTRY, Als.CITY
ORDER BY SUM(Als.totalTransactionRevenue / 1000000) DESC


Answer:  The country has highest revenue is USA and the top three cities are all from USA, San Fransico, Sunnyvale, Atlanta. There are all from developed cities and country.








