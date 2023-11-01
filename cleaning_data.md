What issues will you address by cleaning the data?
there many rows under city are 'not set' or 'not avaliable in demo database'






Queries:
Below, provide the SQL queries you used to clean your data.
where city is not null and city !='(not set)' and city !='not available in demo dataset'
       and v2productcategory is not null and v2productcategory != '(not set)' 
       -------to not select rows contain 'not set' and 'not avalible in demo database'
