What issues will you address by cleaning the data?
1. there are duplicated record from analytics
2. there are abnormal value of city column and missing data of country column in all_sessions     table
3. in products table, there are two types of SKUs, one is purely numeric, the other is with        letters. However, for   purely numeric SKUs, inventory and order are 0, which seems to         have been abandoned.




Queries:
1. SELECT * FROM analytics
    UNION
   SELECT * FROM analytics

2. SELECT ALS.*, CASE WHEN ALS.CITY='(not set)' THEN 'UNKNOWN_CITY' END AS CITY_
   FROM ALL_SESSIONS ALS
   WHERE ALS.COUNTRY != '(not set)'
3. SELECT * FROM PRODUCTS P WHERE P.SKU > 'A'
