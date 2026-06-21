# Instacart Market Basket Analysis
The Dataset is an open-source dataset provided by [Instacart]( https://www.instacart.com/store/?categoryFilter=homeTabForYou), which covers grocery orders, products, products purchase in each order and there departments and aisles also, the data contains of orders week and hour of day the orders placed by the Instacart user [Source Data]

## Data Preparation & Exploratory Data Analysis: [Notebook]( https://github.com/Rahul-765/demo-2/blob/main/Notebook%202%20(1).ipynb)

This notebook performs data preparation and exploratory data analysis (EDA), including table consolidation, column standardization, data validation and summary analysis of orders, users and products.

#### Orders: (3.4 million orders placed by 206k customers)
-	order_id: unique identifier for each order
-	user_id: unique identifier for the customer
-	eval_set: which evaluation set this order belongs in
-	order_number: order sequence number for user (1st to nth)
-	order_dow: day of the week the order was placed on
-	order_hour_of_day: hour of the day order placed on
-	day_since_prior_order: days since previous order (where null for first order) 

#### Orders_products: (33.8 million rows)
-	order_id: foreign key
-	product_id: foreign key
-	add_to_cart_order: Sequence in which the product was added to the cart
-	reordered: product has been ordered by this user in the past or not (1= yes or 0 = no)

#### Products (49.6K products)
-	product_id: unique identifier for each product
-	product_name: name of the product 
-	aisle_id: foreign key
-	department_id: foreign key

#### Ailse (134 Ailse)
-	aisle id: unique identifier for each ailse
-	aisle: name of the aisle

#### Department (21 departments)
-	department_id: unique identifier for each department
-	department: name of the department 

### Data Modelling: (now I want to write all the kpis and the data transformation link and then image of data model)

## Customer Behaviour Analysis [Notebook]()
Filename; 01_Customer_Behaviour.ipynb
