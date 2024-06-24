What issues will you address by cleaning the data?

- All_sessiones (Table) 15134 Registers
	- field all_sessions_time contains 5098 = 0 33% 
	
	- all_sessions_time field contains a different format than date (useless)
	
	- We can not change the format to work with this field (Risk)

	- field country contains 24 = (not set) .001% (Future_goals)
	
	- field city contains 354 = (not set) .02%
	
	- field city contains 8302 = not available in demo dataset 54.08% (Risk)

	- field total_transaction_revenue contains = null 15053  99.46% (useless)
	
	- field transactions contains = null 15053  99.46% (useless)
	
	- field time_on_site contains = null 3300  0.21%
	
	- field session_quality_dim contains = null 13906  91.88% (useless)
	
	- field visit_id contains = duplicate 553 0.036% (Future_goals)
	
	- field product_refund_amount contains = null 15134  100% (useless)
	
	- field product_quantity contains = null 15081  99.64% (useless)
	
	- field product_price contains = '0' 376  0.024% 
	
	- field product_revenue contains = null 15130  99.99% (useless)
	
	- field v2_product_category contains = '(not set) and '${escCatTitle}' 776  0.051% (Future_goals)
	
	- field product_variant contains = (not set) 15094  99.73% (useless)
	
	- field currency_code contains = (USD) 14862  98.20% (useless)
	
	- field item_quantity contains = null 15134  100% (useless) 
	
	- field item_revenue contains = null 15134  100% (useless) 
	
	- field transaction_revenue contains = null 15130  99.99% (useless)
	
	- field transaction_id contains = null 15125  99.99% (useless)
	
	- field search_keyword = null 15134  100% (useless)
	
	- field ecommerce_action_type "what this info means" (useless)
	
	- field ecommerce_action_step "what this info means" (useless)
	
	- field ecommerce_action_option contains = null 15103 99.85% (useless)
	
	TO SUMMARISE HALF OF TABLE IS USELESS
	
- Products (Table) 1092 Registers

	TO SUMMARISE THE DATA ARE ACCURATE ACCORDING WITH THE CONTEXT OF THE FIELDS

- sales_by_sku (Table) 462 Registers

	TO SUMMARISE THE DATA ARE ACCURATE ACCORDING WITH THE CONTEXT OF THE FIELDS	
	
- sales_report (Table) 454 Registers

	- All fields are contains on the (products) table (total_ordered), (product_sku), (product_name), ( stock_level), (restocking_lead_time),
	(sentiment_score), (sentiment_magnitude) (risk)

	TO SUMMARISE THE DATA ARE ON THE TABLE (PRODUCTS). FIELDS ARE ACCURATE ACCORDING WITH THE CONTEXT OF THE FIELDS	

- analytics (table) 4301122 Registers
	
	- field visit_start_time contains a different format than time (useless)
	
	- field user_id = null all fields  100% (useless)
	
	- fields social_engagement_type contains "Not socially Engaged" 100% (useless)
	
	- fields units_sold contains = null 4205975 97.78% (hight risk)
	
	- fields timeonsite contains = null 477465 11.35% 
	
	- fields bounces contains = null 3826283 90.97 % (hight risk)
	
	- fields revenue contains = null 4285767 99.64 % (useless)
	
	- fields unit_price contains = '0' 188314 0.04 % 
	
	TO SUMMARISE THERE ARE 4 FIELDS WITHOUT INFO (VISIT_START_TIME),(USER_ID ), (SOCIAL_ENGAGEMENT_TYPE), (REVENUE),
	AND TWO RELEVANT FIELDS WITH AMBIGUOUS INFORMATION TO USE FOR WORK
	
Queries:

Below, provide the SQL queries you used to clean your data.

---- all_sessions ----

select *
from all_sessions


--- all_sessions_time ---

select all_sessions_time
from all_sessions
where all_sessions_time = 0
order by all_sessions_time
	

select all_sessions_time
from all_sessions
where all_sessions_time <> 0
order by all_sessions_time

--- country ---

select country
from all_sessions
where country = '(not set)'
order by country

select distinct country
from all_sessions
where country <> '(not set)'
order by country

--- city ---

select city
from all_sessions
where city = '(not set)'
order by city

select city
from all_sessions
where city = 'not available in demo dataset'
order by city


select distinct city
from all_sessions
order by city


select city
from all_sessions
where city = 'not available in demo dataset'
order by city

--- total_transaction_revenue ---

select count (*) total_transaction_revenue
from all_sessions
where total_transaction_revenue is null


select total_transaction_revenue
from all_sessions
where total_transaction_revenue is not null

--- transactions ---

select count (*) transactions
from all_sessions
where transactions is null


select count (*) transactions
from all_sessions
where transactions is not null

--- time_on_site ---

select count (*) time_on_site
from all_sessions
where time_on_site is null


select count (*) time_on_site
from all_sessions
where time_on_site is not null

--- pageviews ---

select distinct pageviews
from all_sessions
order by pageviews

--- session_quality_dim ---

select count (*) session_quality_dim
from all_sessions
where session_quality_dim is null

select distinct session_quality_dim
from all_sessions
where session_quality_dim is not null

--- all_sessions_date ---

select distinct all_sessions_date
from all_sessions
order by all_sessions_date

--- visit_id ---

select count(distinct visit_id) as visit_id_count
from ( select visit_id
       from all_sessions
       group by visit_id
       having count(visit_id) >= 2 ) as subquery
order by visit_id_count;

select visit_id
from all_sessions
group by visit_id
having count(visit_id) >= 2
order by visit_id;

--- all_sessions_type ---

select distinct all_sessions_type
from all_sessions
order by all_sessions_type

--- product_refund_amount ---

select count (*) product_refund_amount
from all_sessions
where product_refund_amount is null

--- product_quantity ---

select count (*) product_quantity
from all_sessions
where product_quantity is null

select product_quantity
from all_sessions
where product_quantity is not null
order by product_quantity

--- product_price ---
	
select distinct product_price
from all_sessions
order by product_price

select count(*) product_price
from all_sessions
where product_price = 0
order by product_price

select *
from all_sessions
where product_price = 0
order by product_price

--- product_revenue ---

select count (*) product_revenue
from all_sessions
where product_revenue is null

--- product_sku ---

select distinct product_sku
from all_sessions
order by product_sku

--- v2_product_name ---

select distinct v2_product_name
from all_sessions
order by v2_product_name


--- v2_product_category ---

select distinct v2_product_category
from all_sessions
order by v2_product_category

select count(*) v2_product_category
from all_sessions
where v2_product_category = '(not set)' 
order by v2_product_category

select count(*) v2_product_category
from all_sessions
where v2_product_category = '${escCatTitle}'
order by v2_product_category

--- product_variant ---

select count(*) product_variant
from all_sessions
where product_variant = '(not set)' 
order by product_variant

--- currency_code ---

select distinct currency_code
from all_sessions
order by currency_code
	
	
select count(*) currency_code
from all_sessions
where currency_code is null
order by currency_code

select count(*) currency_code
from all_sessions
where currency_code = 'USD'
order by currency_code


--- item_quantity ---

select count (*) item_quantity
from all_sessions
where item_quantity is null


--- item_revenue --- --

select count (*) item_revenue
from all_sessions
where item_revenue is null

--- transaction_revenue ---

select count (*) transaction_revenue
from all_sessions
where transaction_revenue is null

--- transaction_id ---

select count (*) transaction_id
from all_sessions
where transaction_id is null

--- search_keyword ---

select count (*) search_keyword
from all_sessions
where search_keyword is null

--- page_title ---

select count(*) page_title
from all_sessions
where page_title is null

--- page_path_level1 ---

select distinct page_path_level1
from all_sessions

--- ecommerce_action_type ---

select distinct ecommerce_action_type
from all_sessions
order by ecommerce_action_type


--- ecommerce_action_step ---

select distinct ecommerce_action_step
from all_sessions
order by ecommerce_action_step


--- ecommerce_action_option ---

select distinct ecommerce_action_option
from all_sessions
order by ecommerce_action_option

select count (*) ecommerce_action_option
from all_sessions
where ecommerce_action_option is null
order by ecommerce_action_option

---- products ----

select *
from products

--- product_sku ---

select count(distinct product_sku) as product_sku_count
from ( select product_sku
       from products
       group by product_sku
       having count(product_sku) >= 2 ) as subquery
order by product_sku_count

select distinct product_sku
from products
order by product_sku

--- product_name ---
	
select distinct product_name
from products
order by product_name

--- ordered_quantity ---
	
select distinct ordered_quantity
from products
order by ordered_quantity

--- stock_level ---

select distinct stock_level
from products
order by stock_level

--- restocking_lead_time  ---
	
select distinct restocking_lead_time
from products
order by restocking_lead_time

--- sentiment_score  ---
	
select distinct sentiment_score
from products
order by sentiment_score

select count(*) sentiment_score
from products
where sentiment_score is null
order by sentiment_score

--- sentiment_magnitude  ---
	
select distinct sentiment_magnitude
from products
order by sentiment_magnitude

select count(*) sentiment_magnitude
from products
where sentiment_magnitude is null
order by sentiment_magnitude

---- sales_by_sku ----

select *
from sales_by_sku

--- product_sku ---

select count(distinct product_sku) as product_sku_count
from ( select product_sku
       from sales_by_sku
       group by product_sku
       having count(product_sku) >= 2 ) as subquery
order by product_sku_count
	
select distinct product_sku
from sales_by_sku
order by product_sku

--- product_sku ---

select distinct total_ordered
from sales_by_sku
order by total_ordered

---- sales_report ----

select *
from sales_report

--- product_sku ---

select count(distinct product_sku) as product_sku_count
from ( select product_sku
       from sales_report
       group by product_sku
       having count(product_sku) >= 2 ) as subquery
order by product_sku_count
	
select distinct product_sku
from sales_report
order by product_sku

--- total_ordered ---

select distinct total_ordered
from sales_report
order by total_ordered

--- product_name ---

select distinct product_name
from sales_report
order by product_name

--- stock_level --- --

select distinct stock_level
from sales_report
order by stock_level

--- restocking_lead_time  ---
	
select distinct restocking_lead_time
from  sales_report
order by restocking_lead_time

--- sentiment_score  ---
	
select distinct sentiment_score
from sales_report
order by sentiment_score

select count(*) sentiment_score
from sales_report
where sentiment_score is null
order by sentiment_score

--- sentiment_magnitude  ---
	
select distinct sentiment_magnitude
from sales_report
order by sentiment_magnitude

select count(*) sentiment_magnitude
from sales_report
where sentiment_magnitude is null
order by sentiment_magnitude

--- ratio  ---
	
select distinct ratio
from sales_report
order by ratio

select count(*) ratio
from sales_report
where ratio is null
order by ratio

select count(*) ratio
from sales_report
where ratio is not null
order by ratio

---- Analytics ----

select *
from analytics

--- visit_number

select distinct visit_number
from analytics
order by visit_number

--- visit_id ---

select count(distinct visit_id) as visit_id_count
from ( select visit_id
       from analytics
       group by visit_id
       having count(visit_id) >= 2 ) as subquery
order by visit_id_count

select visit_id
from analytics
group by visit_id
having count(visit_id) >= 2
order by visit_id;
	
select distinct visit_id
from analytics
order by visit_id

--- visit_start_time ---

select distinct visit_start_time
from analytics
order by visit_start_time

--- visit_date ---

select distinct visit_date
from analytics
order by visit_date

--- full_visitor_id ---

select distinct full_visitor_id
from analytics
order by full_visitor_id

--- user_id ---

select distinct user_id
from analytics
order by user_id

--- channel_grouping ---

select distinct channel_grouping
from analytics
order by channel_grouping

select count(*) channel_grouping
from analytics
where channel_grouping = 'Other'
order by channel_grouping

--- social_engagement_type ---

select distinct social_engagement_type
from analytics
order by social_engagement_type

--- units_sold ---

select distinct units_sold
from analytics
order by units_sold

select count(*) units_sold
from analytics
where units_sold is null
order by units_sold

select count(*) units_sold
from analytics
where units_sold is not null
order by units_sold

--- pageviews ---

select distinct pageviews
from analytics
order by pageviews

select count(*) pageviews
from analytics
where pageviews is null
order by pageviews

--- timeonsite ---

select distinct timeonsite
from analytics
order by timeonsite desc

select count(*) timeonsite
from analytics
where timeonsite is null
order by timeonsite

--- bounces ---

select distinct bounces
from analytics
order by bounces 

select count(*) bounces
from analytics
where bounces is null
order by bounces

--- revenue ---

select distinct revenue
from analytics
order by revenue desc

select count(*) revenue
from analytics
where revenue is null
order by revenue

--- unit_price ---

select distinct unit_price
from analytics
order by unit_price desc

select count(*) unit_price
from analytics
where unit_price = 0
order by unit_price

