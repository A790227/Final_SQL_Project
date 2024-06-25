Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
-------By Cities---

	select a.city, sum(an.units_sold * an.unit_price) as total_revenue
	from all_sessions a
	join analytics an
		on a.visit_id = an.visit_id
	join products p
		on a.product_sku = p.product_sku
	Where a.city != 'not available in demo dataset' and a.city != '(not set)' and a.v2_product_category !='(not set)'
	Group by a.city
	Having sum(an.units_sold * an.unit_price) is not null
	Order by total_revenue desc
	limit 10



--- By Countries---

	select a.country, sum(an.units_sold * an.unit_price) as total_revenue
	from all_sessions a
	join analytics an
		on a.visit_id = an.visit_id
	join products p
		on a.product_sku = p.product_sku
	Group by a.country
	Having sum(an.units_sold * an.unit_price) is not null
	Order by total_revenue desc
	limit 10




Answer:

	"city"	"total_revenue"
	"New York"	11266790000
	"Sunnyvale"	6787810000
	"Mountain View"	3190270000
	"Chicago"	2941730000
	"Seattle"	1959990000
	"San Francisco"	1672680000
	"Palo Alto"	1107980000
	"Pittsburgh"	539640000
	"San Jose"	447000000
	"Dublin"	311960000

	"country"	"total_revenue"
	"United States"	40990590000
	"Sweden"	654990000
	"Mexico"	494990000
	"Canada"	431380000
	"Ireland"	311960000
	"United Kingdom"	281970000
	"Japan"	230170000
	"Chile"	199980000
	"Maldives"	199980000
	"Hong Kong"	198970000




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:

	-------By Cities---
	select a.city, avg(p.ordered_quantity) as average_product
	from all_sessions a
	join products p
		on a.product_sku = p.product_sku
	Group by a.city
	Order by average_product desc


	-------By Countries---
	select a.country, avg(p.ordered_quantity) as average_product
	from all_sessions a
	join products p
		on a.product_sku = p.product_sku
	Group by a.country
	Order by average_product desc

Answer:

	"city"	"average_product"
	"Council Bluffs"	7589.0000000000000000
	"Cork"	3786.0000000000000000
	"Bellflower"	3786.0000000000000000
	"Santiago"	3607.0000000000000000
	"Bellingham"	2836.0000000000000000
	"Detroit"	2748.0000000000000000
	"Westville"	2299.0000000000000000
	"Santa Fe"	1932.5000000000000000
	"Nashville"	1886.0000000000000000
	"Brno"	1548.0000000000000000
	"Zhongli District"	1492.0000000000000000
	"Ghent"	1351.0000000000000000
	"Gurgaon"	1335.8571428571428571
	"Rome"	1310.4000000000000000
	"Mississauga"	1305.2500000000000000
	"Moscow"	1291.8000000000000000
	"Madrid"	1286.4666666666666667
	"Prague"	1216.5000000000000000
	"Belo Horizonte"	1184.0000000000000000
	"Sakai"	1148.0000000000000000
	"Riyadh"	1138.0000000000000000
	"Saint Petersburg"	1106.7500000000000000
	"San Bruno"	1106.4285714285714286
	"San Diego"	1093.5238095238095238
	"Milan"	1091.5454545454545455
	"Athens"	1088.4000000000000000
	"Perth"	1035.8000000000000000
	"Minato"	1033.6969696969696970
	"Wrexham"	1033.0000000000000000
	"Munich"	865.2857142857142857
	"Kirkland"	847.7179487179487179
	"Longtan District"	845.0000000000000000
	"Santa Clara"	826.8275862068965517
	"Sao Paulo"	826.6785714285714286
	"Sherbrooke"	812.6666666666666667
	"Dubai"	798.1428571428571429
	"Menlo Park"	791.0000000000000000
	"Indianapolis"	769.0000000000000000
	"Charlotte"	749.1333333333333333
	"Montreuil"	726.5000000000000000
	"Berlin"	708.7692307692307692
	"Palo Alto"	703.4367816091954023
	"Mexico City"	700.8400000000000000
	"Bucharest"	697.4444444444444444
	"Phoenix"	694.8333333333333333
	"Indore"	689.0000000000000000
	"Seoul"	670.5454545454545455
	"Redmond"	661.1250000000000000
	"Dublin"	661.0588235294117647
	"Singapore"	661.0263157894736842
	"Melbourne"	659.3750000000000000
	"Chicago"	647.2916666666666667
	"Cambridge"	627.1250000000000000
	"(not set)"	620.1864951768488746
	"Hyderabad"	602.3269230769230769
	"Kolkata"	593.2222222222222222
	"Bangkok"	588.0000000000000000
	"Quebec City"	578.1428571428571429
	"Mountain View"	575.6476476476476476
	"Austin"	570.6914893617021277
	"Edmonton"	569.5000000000000000
	"Toronto"	566.8090909090909091
	"Shinjuku"	565.2857142857142857
	"Hong Kong"	564.6734693877551020
	"Vladivostok"	551.0000000000000000
	"Tel Aviv-Yafo"	547.7567567567567568
	"Pozuelo de Alarcon"	541.3333333333333333
	"Pittsburgh"	533.7272727272727273
	"The Dalles"	516.5000000000000000
	"not available in demo dataset"	504.3108943536200027
	"San Francisco"	503.8849104859335038
	"Dallas"	503.2758620689655172
	"Bhubaneswar"	499.0000000000000000
	"Chennai"	497.1969696969696970
	"London"	492.8000000000000000
	"Sunnyvale"	491.9389067524115756
	"Bogota"	488.0000000000000000
	"New Delhi"	487.6944444444444444
	"Atlanta"	483.0877192982456140
	"Seattle"	478.0280373831775701
	"Calgary"	472.2000000000000000
	"Mumbai"	470.3061224489795918
	"San Jose"	468.2216981132075472
	"Cupertino"	466.7000000000000000
	"La Victoria"	465.2500000000000000
	"Warsaw"	463.5217391304347826
	"Bengaluru"	463.4307692307692308
	"Tempe"	447.2500000000000000
	"Salem"	446.2750000000000000
	"Oakland"	445.4285714285714286
	"Hamburg"	437.0909090909090909
	"Redwood City"	435.1666666666666667
	"Buenos Aires"	434.5000000000000000
	"Osaka"	434.3333333333333333
	"Rosario"	433.0000000000000000
	"New York"	431.4963369963369963
	"Karachi"	428.0000000000000000
	"Istanbul"	418.1739130434782609
	"Los Angeles"	403.9368421052631579
	"Kalamazoo"	403.0000000000000000


	"country"	"average_product"
	"Montenegro"	3786.0000000000000000
	"Mali"	3786.0000000000000000
	"Papua New Guinea"	2558.0000000000000000
	"Réunion"	2538.0000000000000000
	"Georgia"	2506.4000000000000000
	"Côte d’Ivoire"	1928.5000000000000000
	"Moldova"	1893.0000000000000000
	"Tanzania"	1429.0000000000000000
	"Trinidad & Tobago"	1379.5000000000000000
	"Armenia"	1351.0000000000000000
	"Oman"	1330.0000000000000000
	"Ethiopia"	1239.0000000000000000
	"Bulgaria"	1231.7272727272727273
	"Portugal"	1219.8571428571428571
	"Morocco"	1203.4285714285714286
	"Sint Maarten"	1100.0000000000000000
	"Puerto Rico"	1099.8333333333333333
	"Uganda"	1033.0000000000000000
	"Sudan"	935.0000000000000000
	"Lebanon"	935.0000000000000000
	"Chile"	930.8400000000000000
	"Laos"	886.6666666666666667
	"Zimbabwe"	844.0000000000000000
	"Dominican Republic"	829.5454545454545455
	"Italy"	758.9834710743801653
	"San Marino"	757.0000000000000000
	"Romania"	751.2826086956521739
	"Tunisia"	748.0000000000000000
	"Taiwan"	732.0750000000000000
	"Algeria"	720.5000000000000000
	"Macau"	701.6666666666666667
	"Honduras"	680.5000000000000000
	"Russia"	663.4204545454545455
	"Czechia"	662.4078947368421053
	"Kazakhstan"	617.0000000000000000
	"Israel"	605.4081632653061224
	"Guatemala"	603.2222222222222222
	"Serbia"	602.2307692307692308
	"Brazil"	593.0703125000000000
	"Panama"	588.6666666666666667
	"Mexico"	587.3977272727272727
	"Ireland"	586.6625000000000000
	"Denmark"	579.5178571428571429
	"Hong Kong"	577.8030303030303030
	"South Korea"	576.6000000000000000
	"Costa Rica"	573.4000000000000000
	"United Kingdom"	568.8044596912521441
	"Nepal"	568.0000000000000000
	"Japan"	558.1380952380952381
	"Thailand"	556.6521739130434783
	"Slovenia"	553.8750000000000000
	"Peru"	551.3076923076923077
	"Myanmar (Burma)"	543.6666666666666667
	"Pakistan"	522.2500000000000000
	"Australia"	520.9154228855721393
	"(not set)"	520.6111111111111111
	"Ukraine"	519.6730769230769231
	"United Arab Emirates"	514.6470588235294118
	"United States"	514.1421516284036305
	"Spain"	510.8834951456310680
	"Slovakia"	510.5555555555555556
	"Albania"	510.3333333333333333
	"Macedonia (FYROM)"	505.0000000000000000
	"Bahamas"	498.0000000000000000
	"Singapore"	497.7708333333333333
	"Indonesia"	495.7875000000000000
	"Canada"	494.8084358523725835
	"Saudi Arabia"	492.5000000000000000
	"Germany"	492.4200000000000000
	"India"	481.5788643533123028
	"Lithuania"	479.9333333333333333
	"Philippines"	475.5176470588235294
	"Malta"	469.5000000000000000
	"Vietnam"	462.1034482758620690
	"Argentina"	460.0303030303030303
	"Croatia"	454.8666666666666667
	"Greece"	452.4047619047619048
	"New Zealand"	446.3043478260869565
	"Netherlands"	444.3873239436619718
	"Kosovo"	433.0000000000000000
	"Colombia"	432.6000000000000000
	"France"	420.5181347150259067
	"Switzerland"	406.5714285714285714
	"Poland"	391.7205882352941176
	"Malaysia"	390.8800000000000000
	"Latvia"	387.6250000000000000
	"Bosnia & Herzegovina"	386.6666666666666667
	"Norway"	385.5666666666666667
	"Uruguay"	367.6363636363636364
	"Cambodia"	362.2000000000000000
	"Turkey"	360.8448275862068966
	"Venezuela"	341.8928571428571429
	"Hungary"	340.0000000000000000
	"Egypt"	322.4545454545454545
	"Austria"	319.0909090909090909
	"Sweden"	317.5645161290322581
	"Finland"	313.7692307692307692
	"Sri Lanka"	307.6666666666666667
	"Jordan"	295.0000000000000000
	"Nigeria"	280.1428571428571429

**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:

	-------By Cities quantity---
	select a.city, a.v2_product_category as product_category, p.ordered_quantity as products_ordered
	from all_sessions a
	join products p
	on a.product_sku = p.product_sku
	Where a.city != 'not available in demo dataset' and a.city != '(not set)' and a.v2_product_category !='(not set)'
	Group by a.city, a.v2_product_category, p.ordered_quantity
	Order by p.ordered_quantity desc

	-------By Cities orders ---

	select a.city,a.v2_product_category as product_category, count (*) 
	from all_sessions a
	Where a.city != 'not available in demo dataset' and a.city != '(not set)' and a.v2_product_category !='(not set)'
	Group by a.city, a.v2_product_category
	Order by count desc

	
	-------By Countries quantity---
	select a.country, a.v2_product_category as product_category, p.ordered_quantity as products_ordered
	from all_sessions a
	join products p
	on a.product_sku = p.product_sku
	Where a.city != 'not available in demo dataset' and a.city != '(not set)' and a.v2_product_category !='(not set)'
	Group by a.country, a.v2_product_category, p.ordered_quantity
	Order by p.ordered_quantity desc

	-------By Country orders ---


	select a.country,a.v2_product_category as product_category, count (*) ---max(sum(p.ordered_quantity)) over (partition by a.v2_product_category) as products_ordered
	from all_sessions a
	Where a.city != 'not available in demo dataset' and a.city != '(not set)' and a.v2_product_category !='(not set)'
	Group by a.country, a.v2_product_category
	Order by count desc

-----

Answer:

	---Cities quantity---
	"city"	"product_category"	"products_ordered"
	"San Bruno"	"Home/Accessories/Sports & Fitness/"	15170
	"Santa Clara"	"Home/Accessories/Sports & Fitness/"	15170
	"Los Angeles"	"Home/Accessories/Fun/"	15170
	"Mountain View"	"Home/Accessories/Sports & Fitness/"	15170
	"San Diego"	"Home/Accessories/Sports & Fitness/"	15170
	"Kirkland"	"Home/Accessories/Fun/"	15170
	"Mountain View"	"Home/Accessories/Fun/"	15170
	"Moscow"	"Home/Accessories/Sports & Fitness/"	15170
	"Council Bluffs"	"Home/Accessories/Fun/"	15170
	"Minato"	"Home/Accessories/Fun/"	15170
	"Sunnyvale"	"Home/Accessories/Fun/"	15170
	"Chicago"	"Home/Accessories/Fun/"	15170
	"Santiago"	"Home/Lifestyle/"	15170
	"New York"	"Home/Accessories/Fun/"	15170
	"San Francisco"	"Home/Lifestyle/"	15170
	"San Francisco"	"Home/Accessories/Fun/"	15170
	"Dublin"	"Home/Accessories/Fun/"	15170
	"Mountain View"	"Home/Lifestyle/"	15170
	"Detroit"	"Drinkware"	10075
	"Sao Paulo"	"Home/Accessories/Drinkware/"	8942
	"Tel Aviv-Yafo"	"Home/Accessories/Drinkware/"	8942
	"Cambridge"	"Home/Drinkware/"	8942
	"Mountain View"	"Home/Accessories/Drinkware/"	8942
	"Gurgaon"	"Home/Drinkware/"	8942
	"London"	"Home/Drinkware/Water Bottles and Tumblers/"	8942
	"Austin"	"Home/Drinkware/"	8942
	"Mexico City"	"Home/Drinkware/"	8942
	"San Jose"	"Home/Drinkware/Water Bottles and Tumblers/"	8942
	"San Francisco"	"Home/Drinkware/Water Bottles and Tumblers/"	8942
	"Charlotte"	"Home/Drinkware/"	8942
	"Kirkland"	"Home/Drinkware/Water Bottles and Tumblers/"	8942
	"Mountain View"	"Home/Drinkware/"	8942
	"Singapore"	"Home/Drinkware/"	8942
	"Santa Clara"	"Home/Accessories/Fun/"	4204
	"Houston"	"${escCatTitle}"	4204
	"Mountain View"	"Home/Accessories/Fun/"	4204
	"Toronto"	"Home/Accessories/Fun/"	4204
	"Minato"	"Home/Accessories/Fun/"	4204
	"New York"	"Home/Accessories/"	4204
	"San Jose"	"Home/Accessories/Fun/"	4204
	"Dallas"	"Home/Accessories/"	4204
	"Mountain View"	"Home/Lifestyle/"	4204
	"Los Angeles"	"Home/Office/Notebooks & Journals/"	3896
	"Mountain View"	"Home/Accessories/Stickers/"	3786
	"Kolkata"	"Home/Accessories/Stickers/"	3786
	"Bellflower"	"Home/Shop by Brand/YouTube/"	3786
	"Sydney"	"Home/Shop by Brand/YouTube/"	3786
	"Toronto"	"Home/Shop by Brand/YouTube/"	3786
	"Chicago"	"Home/Shop by Brand/YouTube/"	3786
	"Dallas"	"Home/Shop by Brand/YouTube/"	3786

	--- Cities orders ---
	"city"	"product_category"	"count"
	"Mountain View"	"Home/Apparel/Men's/Men's-T-Shirts/"	110
	"Mountain View"	"Home/Nest/Nest-USA/"	103
	"Mountain View"	"Home/Electronics/"	83
	"Mountain View"	"Home/Shop by Brand/Google/"	80
	"New York"	"Home/Apparel/Men's/Men's-T-Shirts/"	77
	"Mountain View"	"Home/Apparel/Men's/Men's-Outerwear/"	69
	"Mountain View"	"Home/Office/"	64
	"London"	"Home/Shop by Brand/YouTube/"	62
	"New York"	"Home/Electronics/"	48
	"San Francisco"	"Home/Apparel/Men's/Men's-T-Shirts/"	47
	"Mountain View"	"Home/Apparel/"	46
	"Mountain View"	"Home/Apparel/Women's/Women's-T-Shirts/"	43
	"New York"	"Home/Shop by Brand/Google/"	40
	"San Francisco"	"Home/Apparel/"	38
	"Chennai"	"Home/Shop by Brand/YouTube/"	37
	"Sunnyvale"	"Home/Apparel/Men's/Men's-T-Shirts/"	37
	"Mountain View"	"Home/Apparel/Men's/"	37
	"New York"	"Home/Shop by Brand/YouTube/"	35
	"New York"	"Home/Apparel/"	35
	"Los Angeles"	"Home/Apparel/Men's/Men's-T-Shirts/"	33
	"Mountain View"	"Home/Lifestyle/"	32
	"New York"	"Home/Office/"	31
	"Mountain View"	"Home/Drinkware/"	30
	"Mountain View"	"Home/Shop by Brand/Android/"	30
	"San Jose"	"Home/Apparel/Men's/Men's-T-Shirts/"	29
	"New York"	"Home/Apparel/Men's/Men's-Outerwear/"	29
	"Mountain View"	"Home/Apparel/Women's/Women's-Outerwear/"	28
	"San Francisco"	"Home/Electronics/"	28
	"San Francisco"	"Home/Drinkware/"	27
	"Mountain View"	"Home/Electronics/Audio/"	27
	"Sunnyvale"	"Home/Nest/Nest-USA/"	27
	"Sunnyvale"	"Home/Electronics/"	27
	"Palo Alto"	"Home/Nest/Nest-USA/"	26
	"Mountain View"	"Home/Accessories/Fun/"	26
	"Mountain View"	"Home/Apparel/Women's/"	25
	"New York"	"Home/Apparel/Men's/"	25
	"Sunnyvale"	"Home/Apparel/"	25
	"New York"	"Home/Apparel/Women's/Women's-T-Shirts/"	25
	"San Francisco"	"Home/Shop by Brand/Google/"	24
	"San Francisco"	"Home/Office/"	24
	"Chicago"	"Home/Apparel/Men's/Men's-T-Shirts/"	23
	"Mountain View"	"Home/Bags/"	23
	"Sunnyvale"	"Home/Shop by Brand/Google/"	22
	"San Francisco"	"Home/Nest/Nest-USA/"	22
	"Los Angeles"	"Home/Apparel/"	21
	"Los Angeles"	"Home/Shop by Brand/YouTube/"	21
	"San Jose"	"Home/Shop by Brand/Google/"	20
	"Sunnyvale"	"Home/Office/"	20
	"New York"	"Home/Bags/"	20
	"San Francisco"	"Home/Apparel/Men's/Men's-Outerwear/"	20

	--- Countries quantity---
	"country"	"product_category"	"products_ordered"
	"Russia"	"Home/Accessories/Sports & Fitness/"	15170
	"Chile"	"Home/Lifestyle/"	15170
	"Ireland"	"Home/Accessories/Fun/"	15170
	"United States"	"Home/Accessories/Sports & Fitness/"	15170
	"United States"	"Home/Accessories/Fun/"	15170
	"United States"	"Home/Lifestyle/"	15170
	"Japan"	"Home/Accessories/Fun/"	15170
	"United States"	"Drinkware"	10075
	"Brazil"	"Home/Accessories/Drinkware/"	8942
	"India"	"Home/Drinkware/"	8942
	"United States"	"Home/Accessories/Drinkware/"	8942
	"United Kingdom"	"Home/Drinkware/Water Bottles and Tumblers/"	8942
	"United States"	"Home/Drinkware/Water Bottles and Tumblers/"	8942
	"Israel"	"Home/Accessories/Drinkware/"	8942
	"United States"	"Home/Drinkware/"	8942
	"Singapore"	"Home/Drinkware/"	8942
	"Mexico"	"Home/Drinkware/"	8942
	"Canada"	"Home/Accessories/Fun/"	4204
	"United States"	"Home/Accessories/Fun/"	4204
	"United States"	"Home/Lifestyle/"	4204
	"United States"	"${escCatTitle}"	4204
	"Japan"	"Home/Accessories/Fun/"	4204
	"United States"	"Home/Accessories/"	4204
	"United States"	"Home/Office/Notebooks & Journals/"	3896
	"Singapore"	"Home/Shop by Brand/YouTube/"	3786
	"Romania"	"Home/Shop by Brand/YouTube/"	3786
	"Australia"	"Home/Shop by Brand/YouTube/"	3786
	"United States"	"Home/Shop by Brand/YouTube/"	3786
	"India"	"Home/Shop by Brand/YouTube/"	3786
	"United States"	"Home/Office/"	3786
	"India"	"Home/Accessories/Stickers/"	3786
	"United States"	"Home/Electronics/"	3786
	"United Kingdom"	"Home/Office/"	3786
	"Japan"	"Home/Shop by Brand/YouTube/"	3786
	"Czechia"	"Home/Shop by Brand/YouTube/"	3786
	"Poland"	"Home/Shop by Brand/YouTube/"	3786
	"Turkey"	"Home/Accessories/Stickers/"	3786
	"United States"	"Home/Accessories/Stickers/"	3786
	"India"	"Home/Accessories/"	3786
	"Germany"	"Home/Shop by Brand/YouTube/"	3786
	"United States"	"Home/Accessories/"	3786
	"France"	"Home/Shop by Brand/YouTube/"	3786
	"Australia"	"Home/Lifestyle/"	3786
	"Brazil"	"Home/Accessories/Stickers/"	3786
	"United Kingdom"	"Home/Shop by Brand/YouTube/"	3786
	"United States"	"Home/Brands/YouTube/"	3786
	"Spain"	"Home/Shop by Brand/YouTube/"	3786
	"Canada"	"Home/Accessories/Stickers/"	3786
	"Canada"	"Home/Shop by Brand/YouTube/"	3786
	"Ireland"	"Home/Accessories/Stickers/"	3786

	--- Country orders ---
	"country"	"product_category"	"count"
	"United States"	"Home/Apparel/Men's/Men's-T-Shirts/"	489
	"United States"	"Home/Nest/Nest-USA/"	285
	"United States"	"Home/Electronics/"	282
	"United States"	"Home/Shop by Brand/Google/"	271
	"United States"	"Home/Apparel/"	264
	"United States"	"Home/Apparel/Men's/Men's-Outerwear/"	215
	"United States"	"Home/Office/"	211
	"United States"	"Home/Shop by Brand/YouTube/"	192
	"United States"	"Home/Apparel/Women's/Women's-T-Shirts/"	155
	"United States"	"Home/Drinkware/"	148
	"United States"	"Home/Bags/"	145
	"United States"	"Home/Apparel/Men's/"	131
	"India"	"Home/Shop by Brand/YouTube/"	114
	"India"	"Home/Apparel/Men's/Men's-T-Shirts/"	89
	"United States"	"Home/Apparel/Women's/"	88
	"United States"	"Home/Electronics/Audio/"	88
	"United States"	"Home/Accessories/Fun/"	88
	"United States"	"Home/Shop by Brand/Android/"	88
	"United States"	"Home/Accessories/"	84
	"United States"	"Home/Lifestyle/"	83
	"United States"	"Home/Apparel/Headgear/"	81
	"United States"	"Home/Apparel/Women's/Women's-Outerwear/"	75
	"United Kingdom"	"Home/Shop by Brand/YouTube/"	64
	"United States"	"Home/Electronics/Electronics Accessories/"	60
	"United States"	"Home/Drinkware/Water Bottles and Tumblers/"	56
	"United States"	"Home/Bags/Backpacks/"	53
	"United States"	"Home/Apparel/Kid's/Kid's-Infant/"	49
	"United States"	"Home/Accessories/Stickers/"	47
	"Australia"	"Home/Shop by Brand/YouTube/"	45
	"United States"	"Home/Accessories/Drinkware/"	42
	"United States"	"Home/Apparel/Men's/Men's-Performance Wear/"	37
	"United States"	"Home/Shop by Brand/"	35
	"United States"	"Home/Office/Notebooks & Journals/"	33
	"Canada"	"Home/Apparel/Men's/Men's-T-Shirts/"	31
	"United States"	"Home/Bags/More Bags/"	30
	"United States"	"Home/Office/Writing Instruments/"	30
	"United States"	"Home/Apparel/Kid's/"	29
	"United States"	"Home/Accessories/Housewares/"	27
	"Canada"	"Home/Shop by Brand/YouTube/"	26
	"United States"	"Home/Limited Supply/Bags/"	26
	"United States"	"Home/Apparel/Kid's/Kids-Youth/"	26
	"United States"	"Home/Apparel/Kid's/Kid's-Toddler/"	25
	"United States"	"Home/Electronics/Power/"	24
	"United Kingdom"	"Home/Apparel/Men's/Men's-T-Shirts/"	20
	"United States"	"Home/Apparel/Women's/Women's-Performance Wear/"	19
	"India"	"Home/Apparel/"	18
	"Canada"	"Home/Apparel/"	17
	"Australia"	"Home/Apparel/Men's/Men's-T-Shirts/"	17
	"Australia"	"Home/Electronics/"	16
	"Ireland"	"Home/Shop by Brand/YouTube/"	16

**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:

	-------By Cities---
	WITH city_sales AS (SELECT a.city, a.v2_product_name, SUM(an.units_sold) AS total_revenue
		FROM all_sessions a
		JOIN analytics an
		ON a.visit_id = an.visit_id
		WHERE a.country != 'not available in demo dataset' and a.city != '(not set)' and a.v2_product_category != '(not set)'
		GROUP BY a.city, a.v2_product_name
		HAVING max(an.units_sold) is not null)
		
	SELECT city, v2_product_name AS top_product, total_revenue
	FROM (SELECT city, v2_product_name, total_revenue, ROW_NUMBER() OVER (PARTITION BY city ORDER BY total_revenue DESC) AS rank
		  FROM city_sales) ranked_sales
	WHERE rank = 1
	ORDER BY total_revenue desc

	-------By Countries---

	WITH country_sales AS (SELECT a.country, a.v2_product_name, SUM(an.units_sold) AS total_revenue
		FROM all_sessions a
		JOIN analytics an
		ON a.visit_id = an.visit_id
		WHERE a.country != 'not available in demo dataset' and a.city != '(not set)' and a.v2_product_category != '(not set)'
		GROUP BY a.country, a.v2_product_name
		HAVING max(an.units_sold) is not null)
		
	SELECT country, v2_product_name AS top_product, total_revenue
	FROM (SELECT country, v2_product_name, total_revenue, ROW_NUMBER() OVER (PARTITION BY country ORDER BY total_revenue DESC) AS rank
		  FROM country_sales) ranked_sales
	WHERE rank = 1
	ORDER BY total_revenue desc

Answer:

	---By Cities---
	"city"	"top_product"	"total_revenue"
	"Sunnyvale"	"SPF-15 Slim & Slender Lip Balm"	168
	"New York"	"Google Alpine Style Backpack"	164
	"Chicago"	"Google Alpine Style Backpack"	62
	"Mountain View"	"Google Men's Airflow 1/4 Zip Pullover Black"	54
	"not available in demo dataset"	"Google Twill Cap"	25
	"San Francisco"	"Google Women's Scoop Neck Tee White"	22
	"Seattle"	"Nest® Cam Indoor Security Camera - USA"	12
	"Pittsburgh"	"YouTube Hard Cover Journal"	12
	"Tel Aviv-Yafo"	"YouTube Hard Cover Journal"	5
	"Houston"	"Google Sunglasses"	5
	"Toronto"	"Android Stretch Fit Hat Black"	5
	"Zurich"	"YouTube Men's 3/4 Sleeve Henley"	4
	"Palo Alto"	"Nest® Learning Thermostat 3rd Gen-USA - White"	4
	"Bangkok"	"26 oz Double Wall Insulated Bottle"	3
	"Dallas"	"YouTube Leatherette Notebook Combo"	3
	"Detroit"	"Google 22 oz Water Bottle"	3
	"San Jose"	"YouTube Men's Vintage Tank"	3
	"Ann Arbor"	"Google Men's Vintage Badge Tee Black"	2
	"Bogota"	"YouTube Men's 3/4 Sleeve Henley"	2
	"Dublin"	"YouTube RFID Journal"	2
	"Hyderabad"	"Keyboard DOT Sticker"	2
	"Kirkland"	"Android Sticker Sheet Ultra Removable"	2
	"London"	"Android Hard Cover Journal"	2
	"San Bruno"	"Large Zipper Top Tote Bag"	2
	"Santiago"	"Sport Bag"	2
	"Atlanta"	"Android Men's Vintage Henley"	1
	"Munich"	"Google Twill Cap"	1
	"Hong Kong"	"Android Men's Long Sleeve Badge Crew Tee Heather"	1
	"Berlin"	"Google Doodle Decal"	1
	"Austin"	"Google Men's Airflow 1/4 Zip Pullover Black"	1
	"Washington"	"Google Bib White"	1
	"Paris"	"Android Lunch Kit"	1

	--- by countries---
	"country"	"top_product"	"total_revenue"
	"United States"	"Google Alpine Style Backpack"	227
	"Egypt"	"Android RFID Journal"	9
	"Japan"	"Google Lunch Bag"	7
	"Israel"	"YouTube Hard Cover Journal"	5
	"Canada"	"Android Stretch Fit Hat Black"	5
	"Switzerland"	"YouTube Men's 3/4 Sleeve Henley"	4
	"Netherlands"	"Android Men's Vintage Tank"	4
	"Bulgaria"	"YouTube Men's Vintage Tank"	3
	"Thailand"	"26 oz Double Wall Insulated Bottle"	3
	"Vietnam"	"YouTube RFID Journal"	2
	"Belgium"	"Google 17 oz Double Wall Stainless Steel Insulated Bottle"	2
	"Chile"	"Sport Bag"	2
	"Colombia"	"YouTube Men's 3/4 Sleeve Henley"	2
	"India"	"Keyboard DOT Sticker"	2
	"Ireland"	"Google Laptop Backpack"	2
	"Maldives"	"Google Men's Performance Full Zip Jacket Black"	2
	"Mexico"	"Nest® Cam Indoor Security Camera - USA"	2
	"United Kingdom"	"Android Hard Cover Journal"	2
	"Australia"	"Android Sticker Sheet Ultra Removable"	2
	"Germany"	"Google Doodle Decal"	1
	"South Korea"	"Galaxy Screen Cleaning Cloth"	1
	"Sweden"	"Google Water Resistant Bluetooth Speaker"	1
	"France"	"Android Lunch Kit"	1
	"Taiwan"	"Google Men's Performance 1/4 Zip Pullover Heather/Black"	1
	"Indonesia"	"Google Rucksack"	1
	"Hong Kong"	"Android Men's Long Sleeve Badge Crew Tee Heather"	1
	"Denmark"	"26 oz Double Wall Insulated Bottle"	1
	"Austria"	"Google Car Clip Phone Holder"	1

**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:

	-------By Cities--
	With city_revenue AS ( select a.city, sum(an.units_sold * an.unit_price) as total_revenue
							  from all_sessions a
							  join analytics an
									on a.visit_id = an.visit_id
							  join products p
									on a.product_sku = p.product_sku
								Where a.city != 'not available in demo dataset' and a.city != '(not set)' 
								Group by a.city
								Having sum(an.units_sold * an.unit_price) is not null
								Order by total_revenue ), 
			total_revenue AS (select sum(total_revenue) as overall_revenue
								from city_revenue)

		select cr.city, cr.total_revenue, (cr.total_revenue/ tr.overall_revenue::numeric) * 100 As percentage_contribution
		from city_revenue cr, total_revenue tr
		order by cr.total_revenue Desc


	-------By Countries--
	With country_revenue AS ( select a.country, sum(an.units_sold * an.unit_price) as total_revenue
							  from all_sessions a
							  join analytics an
									on a.visit_id = an.visit_id
							  join products p
									on a.product_sku = p.product_sku
								Where a.country != 'not available in demo dataset' and a.country != '(not set)' 
								Group by a.country
								Having sum(an.units_sold * an.unit_price) is not null
								Order by total_revenue ), 
			total_revenue AS (select sum(total_revenue) as overall_revenue
								from country_revenue)

		select cr.country, cr.total_revenue, (cr.total_revenue/ tr.overall_revenue::numeric) * 100 As percentage_contribution
		from country_revenue cr, total_revenue tr
		order by cr.total_revenue Desc



Answer:

	--- By Cities--
	"city"	"total_revenue"	"percentage_contribution"
	"New York"	11378770000	34.44644512402968890100
	"Sunnyvale"	6787810000	20.54843578676253783300
	"Mountain View"	4341270000	13.14213388824946523500
	"Chicago"	2941730000	8.90536859561374882600
	"Seattle"	1959990000	5.93339068973596882200
	"San Francisco"	1672680000	5.06362988530939460300
	"Palo Alto"	1107980000	3.35413865193886639000
	"San Jose"	765000000	2.31585052864964420700
	"Pittsburgh"	539640000	1.63362820820979607800
	"Dublin"	311960000	0.94438265479417386500
	"London"	281970000	0.85359525955992180000
	"Santiago"	199980000	0.60539057348935405000
	"Toronto"	107930000	0.32673169615314522800
	"Tel Aviv-Yafo"	93600000	0.28335112350536823200
	"Atlanta"	89980000	0.27239245825868625600
	"Bangkok"	74970000	0.22695335180766513200
	"Zurich"	68950000	0.20872927313776858600
	"Ann Arbor"	54970000	0.16640823994754371500
	"Washington"	37990000	0.11500543997830063200
	"Bogota"	33980000	0.10286614505034628800
	"Kirkland"	30990000	0.09381465082725813600
	"Austin"	28580000	0.08651896484811350500
	"Dallas"	20970000	0.06348154978533730600
	"Hong Kong"	18990000	0.05748758371118528600
	"Paris"	17990000	0.05446032811817921500
	"Houston"	17500000	0.05297697287760624000
	"Berlin"	12990000	0.03932405015314886000
	"Munich"	10990000	0.03326953896713671900
	"Detroit"	8970000	0.02715448266926445600
	"Singapore"	7600000	0.02300714250684613900
	"Hyderabad"	6500000	0.01967716135453946100

	--- By Countries ---
	"country"	"total_revenue"	"percentage_contribution"
	"United States"	40990590000	91.33847828140848635700
	"Sweden"	654990000	1.45950058024389852600
	"Mexico"	494990000	1.10297591141075028800
	"Canada"	431380000	0.96123507275777179200
	"Ireland"	311960000	0.69513397305743077600
	"United Kingdom"	281970000	0.62830788044301755300
	"Japan"	230170000	0.51288301890828581200
	"Chile"	199980000	0.44561127045783115300
	"Maldives"	199980000	0.44561127045783115300
	"Hong Kong"	198970000	0.44336070848582190500
	"Netherlands"	103950000	0.23162962078253599600
	"Indonesia"	99990000	0.22280563522891557700
	"Israel"	93600000	0.20856693126739171900
	"Switzerland"	85940000	0.19149831274700474700
	"Egypt"	84420000	0.18811132839308983900
	"Thailand"	80970000	0.18042376522137508000
	"Belgium"	49980000	0.11136939342675468100
	"India"	40460000	0.09015617563118236100
	"France"	35480000	0.07905934531375062200
	"Colombia"	33980000	0.07571692654343985700
	"Vietnam"	33980000	0.07571692654343985700
	"Taiwan"	29980000	0.06680380982261115100
	"Bulgaria"	26950000	0.06005212390658340600
	"Denmark"	24990000	0.05568469671337734000
	"Germany"	23980000	0.05343413474136809200
	"Austria"	12990000	0.02894534655089122300
	"Singapore"	7600000	0.01693492176957454100
	"Romania"	5980000	0.01332510949763891500
	"Australia"	4490000	0.01000497351913022200
	"South Korea"	2990000	0.006662554748819457690300


