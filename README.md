# SQL_Project-Analyze-International-Debt-Statistics

![fffffffffff](https://github.com/user-attachments/assets/49f47b8b-9f39-4706-bad1-23c1b3240b5c)

Humans not only take debts to manage necessities. A country may also take debt to manage its economy. For example, infrastructure spending is one costly ingredient required for a country's citizens to lead comfortable lives. The World Bank is the organization that provides debt to countries.

In this project, you are going to analyze international debt data collected by The World Bank. The dataset contains information about the amount of debt (in USD) owed by developing countries across several categories. You are going to find the answers to the following questions:

What is the number of distinct countries present in the database?
What country has the highest amount of debt?
What country has the lowest amount of repayments?

Below is a description of the table you will be working with:

[datalab_export_2025-09-10 17_54_17.xlsx](https://github.com/user-attachments/files/22254636/datalab_export_2025-09-10.17_54_17.xlsx)

**international_debt table :**

**Column**	        **Definition**	                                                                  **Data Type**
country_name	        Name of the country	                                                              varchar
country_code	        Code representing the country	                                                    varchar
indicator_name	      Description of the debt indicator	                                                varchar
indicator_code	      Code representing the debt indicator	                                            varchar
debt	                Value of the debt indicator for the given country (in current US dollars)         	float


-- num_distinct_countries 
-- Write your query here... 

select
	count(distinct country_name) as total_distinct_countries
from
	international_debt




 -- highest_debt_country 
-- Write your query here... 

select
	country_name,
	sum(debt) as total_debt
from
	international_debt
group by country_name
order by total_debt desc
limit 1





-- lowest_principal_repayment 
-- Write your query here... 



select
    country_name, 
    indicator_name,
    MIN(debt) AS lowest_repayment
from
    international_debt
where
	 indicator_code like 'DT.AMT.DLXF.CD'
group by
    country_name, 
    indicator_name,
    indicator_code
order by lowest_repayment
limit 1;


