Question 1: Identified what is the more relevant channel in general and by countries.

SQL Queries:

- 	select *
	from all_sessions

	Select country, channel_grouping, count(*) as channel_grouping_count
	from all_sessions
	where country != '(not set)'
	group by country, channel_grouping
	order by country, channel_grouping_count desc


	select channel_grouping, count(*) as channel_grouping_count
	from all_sessions
	where country != '(not set)'
	group by channel_grouping
	order by channel_grouping
	
Answer: 

	"channel_grouping"	"channel_grouping_count"
	"Organic Search"	8639
	"Direct"	2989
	"Referral"	2579
	"Paid Search"	509
	"Affiliates"	264
	"Display"	125
	"(Other)"	5
	
	"country"	"channel_grouping"	"channel_grouping_count"
	"Albania"	"Organic Search"	2
	"Albania"	"Paid Search"	1
	"Algeria"	"Direct"	3
	"Algeria"	"Organic Search"	1
	"Argentina"	"Organic Search"	31
	"Argentina"	"Direct"	8
	"Argentina"	"Referral"	4
	"Armenia"	"Direct"	1
	"Australia"	"Organic Search"	178
	"Australia"	"Direct"	23
	"Australia"	"Referral"	21
	"Australia"	"Affiliates"	3
	"Austria"	"Organic Search"	31
	"Austria"	"Direct"	8
	"Austria"	"Referral"	1
	"Bahamas"	"Direct"	2
	"Bahamas"	"Organic Search"	1
	"Bahrain"	"Organic Search"	3
	"Bahrain"	"Direct"	1
	"Bangladesh"	"Organic Search"	21
	"Bangladesh"	"Direct"	6
	"Bangladesh"	"Referral"	3
	"Bangladesh"	"Paid Search"	1
	"Bangladesh"	"Affiliates"	1
	"Barbados"	"Direct"	1
	"Barbados"	"Organic Search"	1
	"Belarus"	"Organic Search"	3
	"Belarus"	"Referral"	1
	"Belarus"	"Affiliates"	1
	"Belarus"	"Direct"	1
	"Belgium"	"Organic Search"	50
	"Belgium"	"Direct"	12
	"Belgium"	"Referral"	3
	"Belgium"	"Affiliates"	2
	"Belize"	"Direct"	1
	"Bolivia"	"Organic Search"	4
	"Bosnia & Herzegovina"	"Organic Search"	3
	"Botswana"	"Organic Search"	1
	"Brazil"	"Organic Search"	93
	"Brazil"	"Direct"	37
	"Brazil"	"Referral"	10
	"Brazil"	"Affiliates"	9
	"Brunei"	"Organic Search"	2
	"Bulgaria"	"Organic Search"	8
	"Bulgaria"	"Affiliates"	6
	"Bulgaria"	"Direct"	1
	"Cambodia"	"Organic Search"	4
	"Cambodia"	"Direct"	2
	"Canada"	"Organic Search"	476
	"Canada"	"Direct"	106
	"Canada"	"Referral"	42
	"Canada"	"Paid Search"	8
	"Canada"	"Affiliates"	5
	"Canada"	"Display"	5

Question 2: What is the average time on site for each country and which is the country with the highest average.

SQL Queries:

	select country, avg(time_on_site) as average_time
	from all_sessions
	where country is not null and time_on_site is not null
	group by country
	order by average_time desc

Answer:

	"country"	"average_time"
	"Peru"	859.1818181818181818
	"Nigeria"	752.5000000000000000
	"Tunisia"	726.0000000000000000
	"Slovenia"	696.0000000000000000
	"Kenya"	572.3333333333333333
	"El Salvador"	568.0000000000000000
	"Trinidad & Tobago"	561.0000000000000000
	"Jersey"	518.0000000000000000
	"Réunion"	465.0000000000000000
	"Morocco"	457.1666666666666667
	"Guatemala"	444.4285714285714286
	"Belarus"	441.1666666666666667
	"Argentina"	417.2647058823529412
	"Puerto Rico"	389.0000000000000000
	"Poland"	387.9047619047619048
	"Qatar"	382.5000000000000000
	"Vietnam"	354.3333333333333333
	"Panama"	348.6363636363636364
	"Taiwan"	345.9333333333333333
	"Egypt"	339.0000000000000000
	"South Korea"	337.8409090909090909
	"Myanmar (Burma)"	335.6666666666666667
	"Singapore"	325.5052631578947368
	"Thailand"	325.0882352941176471
	"Venezuela"	324.2800000000000000
	"Israel"	318.2916666666666667
	"China"	313.9473684210526316
	"San Marino"	309.0000000000000000
	"Colombia"	307.2222222222222222
	"Serbia"	298.2500000000000000
	"Spain"	290.4482758620689655
	"Maldives"	289.0000000000000000
	"Mexico"	286.7101449275362319
	"Finland"	277.0769230769230769
	"Indonesia"	276.6071428571428571
	"Canada"	263.9312377210216110
	"Bangladesh"	258.1818181818181818
	"Costa Rica"	257.6666666666666667
	"Pakistan"	256.7083333333333333
	"Cambodia"	255.0000000000000000
	"France"	253.1863354037267081
	"Sweden"	252.9056603773584906
	"Greece"	250.7428571428571429
	"Ukraine"	241.4545454545454545
	"Czechia"	238.3333333333333333
	"Japan"	237.5759162303664921
	"Albania"	236.6666666666666667
	"India"	236.5132530120481928
	"Russia"	232.7931034482758621
	"Malaysia"	226.7435897435897436



Question 3: identify the country with highest level of traffic on the page

SQL Queries:

	select country, count(*)pageviews 
	from all_sessions
	where country != 'not set)'
	group by country
	order by pageviews desc

Answer:

	"country"	"pageviews"
	"United States"	8727
	"India"	719
	"United Kingdom"	668
	"Canada"	642
	"Germany"	336
	"Japan"	241
	"Australia"	225
	"France"	218
	"Taiwan"	174
	"Netherlands"	158
	"Brazil"	149
	"Italy"	135
	"Spain"	119
	"Singapore"	118
	"Mexico"	103
	"Philippines"	100
	"Russia"	99
	"Indonesia"	90
	"Ireland"	87
	"Switzerland"	85
	"Poland"	84
	"Czechia"	81
	"Sweden"	76
	"Hong Kong"	74
	"Belgium"	67
	"Turkey"	66
	"Denmark"	64
	"Israel"	64
	"Ukraine"	63
	"Thailand"	58
	"Malaysia"	54
	"Colombia"	54
	"Romania"	53
	"South Korea"	51
	"New Zealand"	51
	"Greece"	49
	"Pakistan"	47
	"Argentina"	43
	"Austria"	40
	"Slovakia"	39
	"Vietnam"	38
	"Norway"	35
	"Venezuela"	32
	"Hungary"	32
	"Bangladesh"	32
	"Peru"	27
	"Chile"	27
	"South Africa"	26
	"China"	26
	"Portugal"	25



Question 4: Sales per month

SQL Queries:

	select date_trunc('month', a.all_sessions_date) as month, sum(an.units_sold * an.unit_price) as total_sales
	from   all_sessions a
	join   analytics an
	on	   a.visit_id = an.visit_id
	group by month
	order by month;

Answer:

 "month"	"total_sales"
"2017-05-01 "	8605590000
"2017-06-01 "	11254930000
"2017-07-01 "	14740650000
"2017-08-01 "	10968460000


Question 5: Products out of stock and restocking time

SQL Queries:

	Select product_name, (stock_level - ordered_quantity) as Inventary, restocking_lead_time
	from products
	where stock_level - ordered_quantity <= 0
	order by  Inventary 

Answer:

	"product_name"	"inventary"	"restocking_lead_time"
	" Kick Ball"	-14447	5
	" Metallic Notebook Set"	-2108	5
	"Maze Pen"	-1424	9
	"Collapsible Shopping Bag"	-1067	11
	"Switch Tone Color Crayon Pen"	-775	12
	" Protect Smoke + CO White Battery Alarm-USA"	-674	11
	"26 oz Double Wall Insulated Bottle"	-589	9
	" Sunglasses"	-511	8
	" RFID Journal"	-502	3
	"Keyboard DOT Sticker"	-291	9
	"Red Spiral  Notebook"	-273	8
	"23 oz Wide Mouth Sport Bottle"	-260	12
	" Baby Essentials Set"	-184	10
	" Tube Power Bank"	-146	8
	" Snapback Hat Black"	-125	3
	"Android Onesie Gold"	0	19
	" Mobile Phone Vent Mount"	0	7
	" Learning Thermostat 3rd Gen-USA - Stainless Steel"	0	8
	" Women's Short Sleeve Tri-blend Badge Tee Grey"	0	11
	" Toddler Raglan Shirt Blue Heather/Navy"	0	11
	" Toddler Sports T-shirt Red"	0	5
	"Plastic Sliding Flashlight"	0	5
	" Men's Performance 1/4 Zip Pullover Heather/Black"	0	6
	" Zipper-front Sports Bag"	0	7
	" Vintage Henley Grey/Black"	0	7
	" Pet Feeding Mat"	0	8
	" Women's Short Sleeve Performance Tee Pewter"	0	10
	" Tube Power Bank"	0	11
	" Women's Softshell Jacket Black/Grey"	0	13
	" Women's Short Sleeve Tee"	0	13
	" Women's Yoga Pants"	0	15
	" Leather Journal-Brown"	0	16
	" Women's Shell Jacket Blue/Black"	0	16
	"Android Women's Short Sleeve Badge Tee Dark Heather"	0	7
	" Men's Short Sleeve Hero Tee Heather"	0	7
	" 17oz Stainless Steel Sport Bottle"	0	18
	"Android Men's Short Sleeve Tri-blend Hero Tee Grey"	0	16
	" Men's Airflow 1/4 Zip Pullover Black"	0	9
	"Yoga Mat Blue"	0	6
	" Men's Short Sleeve Tee"	0	7
	" Women's V-Neck Tee Charcoal"	0	7
	" 17 oz Double Wall Stainless Steel Insulated Bottle"	0	8
	"Men's Weatherblock Shell Jacket Black"	0	9
	" Women's Lightweight Microfleece Jacket"	0	9
	"Android Youth Short Sleeve T-shirt Aqua"	0	10
	" Youth Girl Tee Green"	0	11
	" Women's Short Sleeve Tri-blend Badge Tee Charcoal"	0	11
	" Snapback Hat Black"	0	12
	"Yoga Block"	0	13
	" Infant Zip Hood Pink"	0	14
