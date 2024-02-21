## SITUATION
You’ve just been hired as an eCommerce Database Analyst for Maven Fuzzy Factory, an online retailer which has just launched their first product.

## BRIEF
As a member of the startup team, you will work with the CEO, the Head of Marketing, and the Website Manager to help steer the business.

You will analyze and optimize marketing channels, measure and test website conversion performance, and use data to understand the impact of new product launches.

## PROJECT SOURCE
- Advanced SQL: MYSQL Data Analysis and Business Inteliigence UDEMY
## TOOLS USED
- MYSQL
## DATABASE
We will be working with six related tables, which contain eCommerce data about:

- Website Activity
- Products
- Orders & Refunds
## Entity Relationship Diagram

![ERD](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/b8a1bde0-37f8-4d0d-b56f-c13ce79da329)

## ANALYZING TRAFFIC SOURCES
### Business Concept: Traffic Source Analysis
Traffic source analysis is about understanding where your customers are coming from and which channels are driving the highest quality traffic.

### Common Use Cases : Traffic Source Analysis
- Analyzing search data and shifting budget towards the engines, campaigns or keywords driving the strongest conversion rates
- Comparing user behavior patterns across traffic sources to inform creative and messaging strategy
- Identifying opportunities to eliminate wasted spend or scale high-converting traffic
## TASK
**1. 📌 FINDING TOP TRAFFIC SOURCES**

***Steps***:
- Breakdown of sessions by UTM source, campaign and referring domain
- Filter results up to sessions before '2012-04-12' and group results by utm_source, utm_campaign and http_referer
  
***Query***:

![site_traffic_breakdown](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/1f07d624-9e73-4abd-a96f-0c674b96a77a)

***Result***:

![answer_site_traffic_breakdown](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/1db75f5d-6050-478e-b7e9-d3a74ca75b40)


- Most sessions came from gsearch nonbrand campaign traffic.
  
**2. 📌 TRAFFIC CONVERSION RATE**

***Steps***:

- Calculate CVR from session(COUNT) to order(COUNT). If CVR < 4% need to reduce bids, otherwise if CVR >= 4% can increase bids to drive more volume
- Filter sessions < '2012-04-12', utm_source = 'gsearch' and utm_campaign = 'nonbrand'
  
***Query***:

![traffic_source_conversion_rate_2](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/090606cb-7e48-408e-9126-be0709c853f4)


***Result***:

![answer_traffic_source_conversion_2](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/b44dabb1-15d2-467e-9263-9ca34d77997a)

- The conversion rate is less than 4%, which is 2.88%, hence we have to reduce bids.

**💡 Business Concept: Bid Optimization**

Analyzing for bid optimization is about understanding the value of various segments of paid traffic, so that you can optimize your marketing budget.

**💡 Common Use Cases: Bid Optimization**

- Using conversion rate and revenue per click analyses to figure out how much you should spend per click to acquire customers
- Understanding how your website and products perform for various subsegments of traffic (i.e. mobile vs desktop) to optimize within channels
- Analyzing the impact that bid changes have on your ranking in the auctions, and the volume of customers driven to your site

**3. 📌 TRAFFIC SOURCE TRENDING**

***Steps***:
Calculate trend and impact on sessions for gsearch nonbrand campaign after bidding down on Apr 15, 2021
Filter to < '2012-05-10', utm_source = 'gsearch', utm_campaign = 'nonbrand'

***Query***:

![gsearch_volume_trends_3](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/3f215d72-ce25-4992-bf6c-433ee837e32f)


***Result***:

![answer_gsearch_vtrends_3](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/a5b9883d-06d4-483a-8b67-448ce3caec13)


- The sessions after 2021-04-15 have dropped. Continue to monitor session volume.
  
**4. 📌 TRAFFIC SOURCE BID OPTIMIZATION**

***Steps***:
Calculate the conversion rate from session to order by device type

***Query***:

![gesearch_device_level_perf_4](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/36151a8d-e7dd-4eb8-a243-3095490fb974)


***Result***:

![answer_device_level_perf_4](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/2e7d271b-5ef2-49e5-9e32-0317808d298e)


- Desktop bids were driving nearly 4% of the conversion rate, so we should transfer the paid traffic spent to the desktop channel instead.

**5. 📌 TRAFFIC SOURCE SEGMENT TRENDING**

***Steps***:

Calculate (with pivot) weekly session trends for both desktop and mobile after bidding up on the desktop channel on 2012-05-19
Filter to between '2012-04-15' to '2012-06-19', utm_source = 'gsearch', utm_campaign = 'nonbrand'

***Query***:

![gsearch_device_level_trend_5](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/c94c1f52-a7bf-453b-9864-59969613857a)

***Result***:

![answer_device_trend_5](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/6a528d76-6adb-426b-a2ae-1f7c29e05237)

- Desktop volume increased after bidding on 2012-05-19, but mobile volume dropped dramatically. Focusing on desktops was able to optimize spending efficiently.

## ANALYZING WEBSITE PERFORMANCE

**💡 Business Concept : Analyzing Top Website Content**
Website content analysis is about understanding which pages are seen the most by your users, to identify where to focus on improving your business.

**💡 Common Use Cases: Analyzing Top Website Content**
- Finding the most-viewed pages that customers view on your site
- Identifying the most common entry pages to your website – the first thing a user sees
- For most-viewed pages and most common entry pages, understanding how those pages perform for your business objectives
  
**TASK**

**1. 📌 IDENTIFYING TOP WEBSITE PAGES**

***Steps***:

Find page view count by page view url, filter date < 2012-06-09 and sort session count descencing

***Query***:

![top_website_pages_6](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/a1f95e8f-f14f-49fa-a82f-a59e95349f19)


***Result***:

![answer_top_website_pages_6](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/de703a57-b5ee-499a-a8bb-ace1de09cc25)

- homepage, products, and original Mr Fuzzy are the most-viewed website pages with the highest traffic.

**2. 📌 IDENTIFYING TOP ENTRY PAGES**

***Steps***:
- Create cte to find the first page landed/entry for each session, filter date to < 2012-06-12
- Count session based on landing page

***Query***:

![top_entry_pages_7](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/54fbc16a-c2a3-410b-8b69-c11205acdfa4)


***Result***:

![answer_top_entry_pages_7](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/33a0e62e-7285-48ca-ba08-042571ef227e)


- Homepage is the top landing page. Analyze landing page performance, for the homepage specifically.

**💡 Business Concept : Landing Page Performance and Testing**

Landing page analysis and testing is about understanding the performance of your key landing pages and then testing to improve your results.

**💡 Common Use Cases: Landing Page Performance and Testing**
- Identifying your top opportunities for landing pages – high volume pages with higher than expected bounce rates or low conversion rates
- Setting up A/B experiments on your live traffic to see if you can improve your bounce rates and conversion rates
- Analyzing test results and making recommendations on which version of landing pages you should use going forward

**3. 📌 BOUNCE RATE ANALYSIS**

***Steps***:
- Find the first website_pageview_id for relavant seasson with filter to date < '2012-06-14' and pageview_url is '/home'
- Count page views for each session to identify bounces (website_pageview_id = 1)
- Summarize by counting total session and bounced session

***Query***:

![landing_page_home_8_1](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/7a6f0ebf-5180-4db6-ac74-630d55c598e1)

![answer_landing_page_home_8_1](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/f69c2dcd-2294-4800-b2f9-8e93b0375aee)

![bounced_home_8_2](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/f0e9c09d-ad71-46de-b614-a31f066b7bff)

![answer_bounced_home_8_2](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/a913a6fa-f30c-4198-b0a3-ef9256870915)

![bounced_session_8_3](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/99987c45-87a1-42a8-b3f2-7856656680d2)

![answer_bounced_session_8_3](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/4e96421e-7f76-41a9-89d1-430bfd633dc6)

- A 60% bounce rate is pretty high especially for paid search.

**4. 📌 ANALYZING LANDING PAGE TESTS**

***Steps***:
- Find when /lander-1 was created on the website by use either date or pageview id to limit the results
- Find the first website_pageview_id for relavant season with filter by date periode, between '2012-06-01' and '2012-08-31'
- Count page views for each session to identify bounces (website_pageview_id = 1) each landing page
- Summarize by counting total session and bounced session each landing page

***Query***:

![lander1_creation_9](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/1ae5cd58-dfab-42cf-acec-3067a0770487)

![answer_lander1_creation_9](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/2dffaac2-e8ab-4321-b1f8-5773e9196366)

![landing_page_test_9_1](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/1f096a97-720a-423e-9cb0-b36091832747)

![answer_landing_page_test_9_1](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/ac2aa559-4422-4d89-976c-e5b9d8163491)

![bounced_test_9_2](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/46f371f0-3cd8-480e-82a5-891b76df3091)

![answer_bounced_test_9_2](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/2f64bf75-fa49-43d0-aeea-b3e5210990d7)

![bounced_test_9_3](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/822de9d6-cccc-4b06-adcc-4c26cbea245a)

![answer_bounced_test_9_3](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/65353e20-e56e-4410-8935-b72d58acf262)


- The Lander page has a lower bounce rate than home page. Fewer customers have bounced on the lander page.

**5. 📌 LANDING PAGE TREND ANALYSIS**

***Steps***:
- Pull paid gsearch nonbrand campaign traffic on /home and /lander-1 pages, trended weekly since 2012-06-01 and the bounce rates.
- Find the first website_pageview_id for relavant season with select created_at and filter
- Count page views for each session to identify bounces (website_pageview_id = 1)
- Summarize sessions, bounced sessions and bounce rate by week

***Query***:

![landing_page_trend_10](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/d7c54a0b-166a-4128-87ea-52744c358de2)

![answer_landing_page_trend_10](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/d4486f87-4f31-4220-96eb-a238167c1546)

![bounced_trend_10_1](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/30972676-6044-4b10-9cc7-239f980d583d)

![answer_bounced_trend_10_1](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/f4777d2b-77a9-405e-b7c2-3c03beb5d957)

![bounce_home_lander_10_2](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/9c29cbdc-79eb-4e20-b9f3-0c5349120321)

![answer_bounce_home_lander_10_2](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/3c1defdb-4c9e-497c-ab04-6702aa99eb24)

- All traffict was directed to home until 2012-06-17, and starting on 2012-08-05, all traffic was directed to lander-1. There has been improvement as the bounce rate decreased from more than 60% to about 50%.

**💡 Business Concept : Analyzing and Testing Conversion Funnels**

Conversion funnel analysis is about understanding and optimizing each step of your user’s experience on their journey toward purchasing your products.

**💡 Common Use Cases: Analyzing and Testing Conversion Funnels**

- Identifying the most common paths customers take before purchasing your products
- Identifying how many of your users continue on to each next step in your conversion flow, and how many users abandon at each step
- Optimizing critical pain points where users are abandoning, so that you can convert more users and sell more products

**6. 📌 BUILDING CONVERSION FUNNELS**

***Steps***:

- Select all pageviews for relevant session, create pageview level in temporary table, filter to date between '2012-08-05' and '2012-09-05'
- Aggregate data to assess funnel performance
- Agregate data to be click rate\

***Query***:

![analyze_conversion_funnel_11](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/c4008a0d-e063-45f4-9a7f-dde069b0a361)

![analyze_conversion_funnel_11_1](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/bf910b92-e049-4b20-80ea-6f71553f3c5b)

![answer_analyze_conversion_funnel_11](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/ba0e7a02-14b8-4293-bd8b-d15de9fdabab)

![funnel_performance_12](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/fad39174-622f-4d4e-b8a6-2981dba1359e)

![answer_funnel_performance_12](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/c770b5dd-b62f-418f-bac4-edcaf5dcc9d1)

![aggregate_Click_rate_13](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/1f33ea0a-4eed-4d9f-9483-3c3a8317319b)

![answer_aggregare_click_rate_13](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/3ef75385-5b98-408f-bfca-a1a1da51fbc3)


- Lander-1, mrfuzzy, and billing pages has lowest clickthrough rate. More information on billing page will make customers more comfortable to insert their credit card information.

**7. 📌 ANALYZING CONVERSION FUNNEL TEST**

***Steps***:
- Find first time '/billing-2 was seen
- Select all pageviews for relevant session
- Aggregate and summarize the conversion rate

***Query***:

![billing2_14](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/4fcb96ae-b6f7-448f-bdb0-8eb41729710b)

![answer_billing2_14](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/64613c0b-8a2d-414b-81ca-30bc881d1c8e)

![billing_test_15](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/42e74738-e9dc-4ea1-829e-9bafdd467dff)

![answer_billing_test_15](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/db29cbdc-64b7-41ea-9e63-85869db99488)

![answer_billingS_test_15_result](https://github.com/Shivani1279/Maven_Factory_MySql/assets/117190648/cf769b16-e531-4234-b8dd-48f640dd00a0)


- /billing-2 page has session to order converstion rate at 62%, much better than billing page at 46%.
