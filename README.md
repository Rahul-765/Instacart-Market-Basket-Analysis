#  Instacart Market Basket Analysis

This project analyze customer purchasing behaviour using the **Instacart Grocery Shopping Dataset**, an open-source dataset released by **[Instacart](https://www.instacart.com/store/?categoryFilter=homeTabForYou)**, one of the largest online grocery delivery and pickup platforms in the United States.

The dataset contains grocery orders, purchased products, aisles and departments. It includes customer order history, product level transactions, shopping day, shopping hour, order sequence and reorder information, making it ideal for customer behaviour analysis and market basket analysis

This project explore customer shopping patterns, product popularity, basket composition and reorder behaviour to generate actionable business insights for retail and e-commerce.

## Data Preparation & Exploratory Data Analysis [Notebook]( https://github.com/Rahul-765/Instacart-Market-Basket-Analysis/blob/main/01_Data_Preparation_and_EDA.ipynb)

This notebook prepares the Instacart dataset for analysis by consolidating the original source tables, standardizing column names, validating data integrity and generating summary statistics.

#### orders: (3.4 million orders placed by 206k customers)
-	order_id: unique identifier for each order
-	user_id: unique identifier for the customer
-	eval_set: which evaluation set this order belongs in
-	order_number: order sequence number for user (1st to nth)
-	order_day_of_week: day of the week the order was placed on
-	order_hour: hour of the day order placed on
-	days_since_prior_order: days since previous order (where null for first order) 

#### orders_products: (33.8 million rows)
-	order_id: foreign key
-	product_id: foreign key
-	add_to_cart_order: Sequence in which the product was added to the cart
-	reordered: product has been ordered by this user in the past or not (1= yes or 0 = no)

#### products (49.6K products)
-	product_id: unique identifier for each product
-	product_name: name of the product 
-	aisle_id: foreign key
-	department_id: foreign key

#### aisles (134 aisle)
-	aisle_id: unique identifier for each ailse
-	aisle: name of the aisle

#### department (21 departments)
-	department_id: unique identifier for each department
-	department: name of the department 

### Data Modelling:
<p align="center">
  <img src="assets/erd-diagram.png" width="600">
</p>

## Customer Behaviour Analysis [Notebook]( https://github.com/Rahul-765/Instacart-Market-Basket-Analysis/blob/main/02_Customer_Behaviour.ipynb)

This notebook explores customer purchasing behaviour by answering key business questions related to customer loyalty and shopping patterns. The analysis examines how customers are distributed by lifetime order count, identifies peak shopping days and hours, compares high-value customers with the average shopper, and measures customer lifespan to better understand long-term engagement.

| Insight | Result |
|---------|--------|
| Total customers analysed | **206,209** |
| Total orders analysed | **3,421,083** |
| Most common order frequency | **4–8 orders per customer lifetime** |
| Largest shopping frequency segment | **Monthly shoppers: 52.3% (107,897 customers)** |
| Peak shopping day | **Sunday, followed by Monday** |
| Peak shopping time | **6–9 PM, followed by 12–5 PM** |
| Largest lifespan bucket | **180–365 days: 41.1% of customers** |
| Customers active beyond 1 year | **<1% (1,568 customers)** |

> The typical Instacart customer remains active for 6–12 months, shops approximately once every 2–4 weeks and places 4–8 orders during their lifetime. Shopping activity is occurring during the 6–9 PM evening window followed by 12–5 PM afternoons.

> The analysis suggests that retailers should focus on Marketing campaigns and promotions should be scheduled around peak shopping periods, particularly Sunday evenings to maximise customer engagement. Since the majority of customers shop once every 2–4 weeks, personalised reminders and targeted offers timed to this purchasing cycle could encourage more frequent orders and improve long-term customer retention.

## Basket and Product Analysis [Notebook](https://github.com/Rahul-765/Instacart-Market-Basket-Analysis/blob/main/03_Basket_Product_Analysis.ipynb)

This notebook analyse shopping basket and product purchasing patterns to understand what customers buy. The analysis examines basket size across the customer journey, identifies the departments and aisles driving the highest sales and reorder rates, compares first-time and repeat shopping baskets, and highlights the products most frequently added first to the cart.

| Insight | Result |
|---------|--------|
| Total orders analysed | **3,346,083** |
| Total items sold | **33,819,106** |
| Average basket size | **10.11 items** per order |
| Basket size range | Min **1** item · Max **145** items |
| Top department by volume | **Produce** - highest order count and highest reorder rate |
| Top purchased product | **Banana** - most ordered product across all order stages |

> Fresh produce dominates purchasing behaviour. The ten most-purchased products are all fresh produce items, with Banana ranking as the single most purchased product. \
> Products most frequently added first to the basket represent the strongest purchase intent, indicating the items customers visit the platform specifically to buy. When these products also exhibit high reorder rates, they become key drivers of long-term customer loyalty.

> The analysis suggests that retailers should prioritise inventory availability, pricing and merchandising within fresh produce, as this category consistently drives both basket composition and repeat purchasing. Because basket size remains relatively stable throughout the customer lifecycle, strategies that encourage customers to shop more frequently are likely to deliver greater long-term value than initiatives focused solely on increasing basket size. 

## Reorder Analysis [Notebook](https://github.com/Rahul-765/Instacart-Market-Basket-Analysis/blob/main/04_Reorder_Analysis.ipynb)

This notebook investigates repeat purchasing behaviour to understand customer loyalty and product retention. The analysis measures how reorder rates change as customers place more orders, identifies the departments, aisles and products with the strongest repeat purchasing behaviour and segments customers based on the proportion of new versus repeat products in their shopping baskets.

| Insight | Result |
|---------|--------|
| Total items sold | **33,819,106** |
| Total reordered items | **19,955,360** |
| Overall reorder rate | **59.01%** — nearly 6 in every 10 items is a repeat purchase |
| Reorder rate — orders 1–10 | **42.4%** |
| Reorder rate — orders 11–20 | **69.2%** — largest single jump: +26.8 percentage points |
| Reorder rate — orders 31–40 | **79.0%** — approaching stability |
| Reorder rate — orders 70+ | **83–85%** — fully habitual |
| Fastest loyalty department | **Produce** — 61.7% reorder at orders 2–10, rising to 90.3% at orders 70+ |
| Slowest loyalty department | **Personal care** — 27.6% reorder at orders 2–10 |

> Nearly six in every ten purchased items are reorders, demonstrating that customer purchasing behaviour is primarily habitual rather than exploratory. The largest increase in reorder behaviour occurs between the first 10 orders and the 11–20 order stage, where reorder rates increase by almost 27 percentage points. This represents the critical habit-formation period in the customer journey. \
> Although reorder rates vary across departments during the early stages, all departments converge towards higher repeat purchasing behaviour as customers become more experienced. Produce consistently achieves the highest reorder rates, while Personal Care remains the least frequently reordered department.

> These findings suggest that customer retention initiatives should focus on the first 10 orders, where purchasing habits are still forming and improvements are likely to have the greatest long-term impact. Loyalty programmes, personalised offers, and targeted onboarding campaigns during this period are likely to generate stronger customer lifetime value than interventions aimed at long-established customers. At the same time, consistently high-performing categories such as Produce should remain a strategic priority for maintaining customer engagement and repeat purchasing.

## Purchasing Patterns & Cohort Retention [Notebook](https://github.com/Rahul-765/Instacart-Market-Basket-Analysis/blob/main/05_Purchasing_Patterns_and_Cohort.ipynb)
This notebook examines two questions that sit at the heart of retail basket strategy and customer lifecycle management: which product categories are purchased together in the same basket and how many customers continue placing orders as their order sequence grows. The first delivers true market basket analysis through department co-occurrence and affinity scoring. The second maps the customer loyalty funnel through sequence-based cohort retention.

| Insight | Result |
|---------|--------|
| Strongest department pair | Dairy Eggs + Produce (1,841,091 co-occurrences) |
| Produce basket presence | Appears in 7 of the top 10 department pairs |
| Second strongest pair | Produce + Snacks (1,128,643 co-occurrences) |
| Customers retained to order 10 | 110,728 (53.7%) |
| Customers retained to order 100 | 1,374 (0.7%) |
| Highest customer attrition | Between the 4th and 5th orders |

> Dairy Eggs and Produce form the backbone of the Instacart basket, appearing together in more than 1.8 million orders. Produce also appears in most of the highest-frequency department combinations, highlighting its role as a key basket anchor. The retention analysis shows that customer attrition is concentrated during the early purchasing journey, while a small but valuable segment of highly engaged customers continues placing orders over the long term. 

> Together these analyses demonstrate how purchasing relationships and customer retention complement one another. Product and department affinity identify opportunities for recommendations, bundling and merchandising, while the cohort analysis highlights the stages of the customer journey where retention initiatives can have the greatest impact on long-term customer lifetime value.
