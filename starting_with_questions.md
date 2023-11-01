Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
create view transaction_revenue as
select cast(als.productprice/10000 as int) as productprice, sr.total_ordered, 
cast (productprice/10000 *total_ordered as int) as transaction_revenue, als.productsku
from all_sessions als
join sales_report sr using (productsku)

select country, city, transaction_revenue
from all_sessions als
join transaction_revenue using (productsku)
order by transaction_revenue desc


Answer: USA Chicago




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries: 
select  als.city,cast (avg(sr.total_ordered) as float)
from all_sessions als
join sales_report as sr using(productsku)
where city is not null and city !='(not set)' and city !='not available in demo dataset'
group by city
order by avg(sr.total_ordered) desc

select  als.country,cast (avg(sr.total_ordered) as float)
from all_sessions als
join sales_report as sr using(productsku)
where country is not null 
group by country
order by avg(sr.total_ordered) desc


Answer: 





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:
select  country, v2productcategory
from all_sessions
where country is not null and city !='(not set)' 
       and v2productcategory is not null and v2productcategory != '(not set)'
group by v2productcategory, country
order by country desc

select  city), als.v2productcategory
from all_sessions
where city is not null and city !='(not set)' and city !='not available in demo dataset'
       and v2productcategory is not null and v2productcategory != '(not set)'
group by v2productcategory, city
order by city desc



Answer: I did not find any pattern from the data, because I could see different typys of product coming from same Countries ans Cities


**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:
select  als.city, als.v2productcategory, sr.total_ordered
from all_sessions als
join sales_report as sr using(productsku)
where city is not null and city !='(not set)' and city !='not available in demo dataset'
       and v2productcategory is not null and v2productcategory != '(not set)'
order by city desc, total_ordered desc

select  als.country, als.v2productcategory, sr.total_ordered
from all_sessions als
join sales_report as sr using(productsku)
where city is not null and city !='(not set)' and city !='not available in demo dataset'
       and v2productcategory is not null and v2productcategory != '(not set)'
order by country desc, total_ordered desc
            



Answer: the top selling products are mostly drinkwares, office, appreal, ect...
        the products that people buy the most are relative to our daily life, which are more popular and easy to sell.



**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries: 
create view transaction_revenue as
select cast(als.productprice/10000 as int) as productprice, sr.total_ordered, 
cast (productprice/10000 *total_ordered as int) as transaction_revenue, als.productsku
from all_sessions als
join sales_report sr using (productsku)

select country, city, transaction_revenue
from all_sessions als
join transaction_revenue using (productsku)
order by transaction_revenue desc


Answer: developed countries has higher revenue








