What are your risk areas? Identify and describe them.

- Redundancy information 
- Lack of information
- Wrong information
- Ambiguous information
- Ensure integrity database (keys)

QA Process:
Describe your QA process and include the SQL queries used to execute it.

- REDUNDANCY INFORMATION -
	- table (sales_report) fields are contains on the table (products)  (total_ordered), (product_sku), (product_name), ( stock_level), (restocking_lead_time),
	(sentiment_score), (sentiment_magnitude) (risk)

	
- LACK OF INFORMATION -
	- All_sessiones table has 16 fields useless (detail on cleaning_date.md)
	- Analytics table has 4 fields useless (detail on cleaning_date.md)
	
	
- WRONG INFORMATION -
	- all_sessions_time field contains a different format than date (useless)
		--- all_sessions_time ---

			select all_sessions_time
			from all_sessions
			where all_sessions_time = 0
			order by all_sessions_time
				

			select all_sessions_time
			from all_sessions
			where all_sessions_time <> 0
			order by all_sessions_time
			
	field visit_start_time contains a different format than time (useless)
		--- visit_start_time ---

			select distinct visit_start_time
			from analytics
			order by visit_start_time
			
			
- AMBIGUOUS INFORMATION -
	- field city contains 354 = (not set) .02%
	- field city contains 8302 = not available in demo dataset 54.08% (Risk)
		---- city ---

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
		
	- fields units_sold contains = null 4205975 97.78% (hight risk)
		--- unit_price ---

			select distinct unit_price
			from analytics
			order by unit_price desc

			select count(*) unit_price
			from analytics
			where unit_price = 0
			order by unit_price
			
	- fields bounces contains = null 3826283 90.97 % (hight risk)
		--- bounces ---

			select distinct bounces
			from analytics
			order by bounces 

			select count(*) bounces
			from analytics
			where bounces is null
			order by bounces


- ENSURE INTEGRITY DATABASE (KEYS)-

--- products key ---
--- product_sku ---

		select count(distinct product_sku) as product_sku_count
		from ( select product_sku
			   from products
			   group by product_sku
			   having count(product_sku) >= 2 ) as subquery
		order by product_sku_count;

		select distinct product_sku
		from products
		order by product_sku
		
--- sales_by_sku key ---
--- product_sku ---

		select count(distinct product_sku) as product_sku_count
		from ( select product_sku
			   from sales_by_sku
			   group by product_sku
			   having count(product_sku) >= 2 ) as subquery
		order by product_sku_count;
			
		select distinct product_sku
		from sales_by_sku
		order by product_sku

--- sales_report key ---
--- product_sku ---

		select count(distinct product_sku) as product_sku_count
		from ( select product_sku
			   from sales_report
			   group by product_sku
			   having count(product_sku) >= 2 ) as subquery
		order by product_sku_count;
			
		select distinct product_sku
		from sales_report
		order by product_sku

--- all_sessions ---
--- visit_id key --- (553 registers duplicates) 

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
