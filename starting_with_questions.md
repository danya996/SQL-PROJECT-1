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
SELECT COUNT(*), ALS.COUNTRY, ALS.CITY, ALS.v2ProductCategory
FROM ALL_SESSIONS ALS
WHERE ALS.COUNTRY != '(not set)' AND ALS.CITY != '(not set)' AND ALS.CITY != 'not available in demo dataset' AND ALS.v2ProductCategory != '(not set)'
GROUP BY ALS.COUNTRY, ALS.CITY, ALS.v2ProductCategory
ORDER BY COUNT(*) DESC


Answer: Mountain View has the highest order amount, the top categories of prodcuts are Men's T-Shirts, Nest-USA, and Electronics

**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:

Answer: 



**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries: 



Answer: 








