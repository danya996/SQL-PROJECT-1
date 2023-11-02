What are your risk areas? Identify and describe them.
whether the data in sales_report table really affect sales


QA Process:
Describe your QA process and include the SQL queries used to execute it.
SELECT *
FROM (
SELECT DISTINCT T.productSKU, T.total_ordered
FROM SALES_BY_SKU T
) SBQ1
FULL OUTER JOIN 
(
SELECT SR.productSKU, SUM(SR.total_ordered)
FROM SALES_REPORT SR
GROUP BY SR.productSKU
) SBQ2
ON SBQ1.productSKU = SBQ2.productSKU

