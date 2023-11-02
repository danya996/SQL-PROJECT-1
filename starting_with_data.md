Question 1:  ind the total number of unique visitors (`fullVisitorID`)


SQL Queries: 
SELECT COUNT(*)
FROM (SELECT DISTINCT A.fullvisitorID FROM ANALYTICS A) SBQ

Answer: 120018



Question 2:  find the number of unique visitors classified in each channel grouping to create some user images

SQL Queries: 
SELECT COUNT(*), SBQ.channelGrouping
FROM ( SELECT DISTINCT A.fullvisitorID, A.channelGrouping FROM ANALYTICS A) SBQ
GROUP BY SBQ.channelGrouping


Answer: display 844, paid search 3762, direct 21340, referral 18382, other 2, 
        orgainc search 66333, affillates 1469, social 11023



Question 3: find out the products of stock level over 200


SQL Queries: 
SELECT P.SKU, cast(MAX(P.stockLevel) as int)
FROM PRODUCTS P
GROUP BY P.SKU
HAVING cast(MAX(P.stockLevel)as int) > 200

Answer: there are 123 products has stock over 200


Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
