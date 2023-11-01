What issues will you address by cleaning the data?
there many rows under city are 'not set' or 'not avaliable in demo database'
find transaction revenue is mostly null





Queries:
Below, provide the SQL queries you used to clean your data.
where city is not null and city !='(not set)' and city !='not available in demo dataset'
       and v2productcategory is not null and v2productcategory != '(not set)' 
       -------to not select rows contain 'not set' and 'not avalible in demo database'
select cast(als.productprice/10000 as int) as productprice, sr.total_ordered, cast (productprice/10000 *total_ordered as int) as transaction_revenue
from all_sessions als
join sales_report sr using (productsku)
       -------usd productprice from all_sessions table and total_ordered from sales_report table to calculate the transaction revenue
