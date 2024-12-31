## Brazilian E-Commerce Public Dataset by Olist

This is my study project on descriptive analysis of the dataset from Kaggle 

### About DATASET

This is a Brazilian ecommerce public dataset of orders made at Olist Store, the largest department store in Brazilian marketplaces (like Wildberries).
The dataset has information of 100k orders from 2016 to 2018 made at multiple marketplaces in Brazil. 
This is real commercial data, it has been anonymised, and references to the companies and partners in the review text have been replaced with the names of Game of Thrones great houses. [Link to the dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

#### Tools: SQL, BigQuery

### Objectives of the EDA
#### Revenue Analysis
* Total revenue
* Number of orders Over-time
* What are the most popular product categories on Olist, Which product category generates highest revenue?
* What is the average order value (AOV) on Olist, and how does this vary by product category or payment method?
* Which product categories have the highest profit margins
* Number of orders by Pricing & sized by revenue generated

### Data schema
Let's look at our data
![schema](https://github.com/tata411/SQLanalysis_ecommerce/blob/ce9597c084c55562d28ca718b7473329de241cc7/%D0%91%D0%B5%D0%B7%20%D0%BD%D0%B0%D0%B7%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F.png)

### Data preparation& cleaning

```
--Check duplicates and null values:
SELECT 
order_id,
COUNT(*) as count_id
 FROM `orders` 
GROUP BY order_id
HAVING count_id >1
 LIMIT 1000;

SELECT *
 FROM `orders` 
 WHERE order_id IS NULL OR
    customer_id IS NULL OR
    order_status is NULL;
```

```
--Check status of orders
SELECT DISTINCT(order_status)
FROM`orders` ;
```
![pic2](https://github.com/tata411/SQLanalysis_ecommerce/blob/c7198ae10f021fa18910387339a2fefcdf05c5a8/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-12-31%20%D0%B2%2008.41.21.png)

```
SELECT MIN(order_purchase_timestamp) as min_date,
MAX (order_purchase_timestamp) max_date
FROM orders]; 

```
![pic3](https://github.com/tata411/SQLanalysis_ecommerce/blob/ffa70385cb3656dc8cb66f5b1e437a6a400ee48a/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-12-31%20%D0%B2%2009.00.46.png)

```
SELECT
DISTINCT LENGTH(order_id) as length_order_id
FROM orders; 
--32 symbols in order_id 

SELECT
DISTINCT LENGTH(customer_id) as l
FROM orders 
--32 symbols in customer_id 

```
