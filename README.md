# Numpy & Pandas Project
Big data explorer using Numpy and Pandas and analytics
# Business Scenario
We work as data analysts, and our client operates a major e-commerce business in India (we’ll refer to it as Company X). Every day, X receives thousands of orders through its website and aims to deliver them as quickly as possible. To fulfill these deliveries, X has partnered with several courier services across India, who charge a fee for each delivery they complete.

# The charges are dependent upon two factors:
●	Weight of the product
●	Distance between the warehouse and customer’s delivery address

On average, each shipment costs around ₹100. So, if Company X ships about 1,00,000 orders in a month, they end up paying nearly ₹1 crore to their courier partners. Since this is a significant expense, X wants to ensure that the delivery charges billed by their courier companies for each order are accurate.

# Dataset
Format: CSV

# Technologies Used
● SQL
● PySpark
● Python
● PowerBI
● Jupyter Notebook
● Pandas
● GitHub

# Input Data
# 1. X’s internal data spread across three reports: 
●	Website order report- which will list Order IDs and various products (SKUs) part of each order. Order ID is common identifier between X’s order report and courier company invoice
●	SKU master with gross weight of each product-This should be used to calculate total weight of each order and during analysis compare against one reported by courier company in their CSV invoice per Order ID. The courier company calculates weight in slabs of 0.5 KG multiples, so first you have to figure out the total weight of the shipment and then figure out applicable weight slabs. For example:
-	If the total weight is 400 gram then weight slab should be 0.5
-	If the total weight is 950 gram then weight slab should be 1
-	If the total weight is 1 KG then weight slab should be 1
-	If the total weight is 2.2 KG then weight slab should be 2.5

●	Warehouse pincode to All India pincode mapping -(this should be used to figure out delivery zone (a/b/c/d/e) and during analysis compare against one reported by courier company in their CSV invoice per Order ID.

# 2. Courier company invoice in CSV file:
● Invoice Details: Includes AWB Number (courier’s internal ID), Order ID (from Company X), shipment weight, warehouse pickup pincode, customer delivery pincode, delivery zone, shipment charges, and shipment type.

● Courier Rate Card: Contains rates based on weight slabs and pincodes.If the invoice mentions “Forward charges”, only forward charges (“fwd”) apply.
If it mentions “Forward and RTO charges”, both forward (“fwd”) and return (“rto”) charges apply. Charges are calculated as:
A fixed rate for the first 0.5 KG
An additional rate for every extra 0.5 KG
Total charge = fixed + additional (if applicable)

# Output Data 1
A resultant CSV/Excel file with the following columns:
●	Order ID
●	AWB Number
●	Total weight as per X (KG)
●	Weight slab as per X (KG)
●	Total weight as per Courier Company (KG)
●	Weight slab charged by Courier Company (KG)
●	Delivery Zone as per X
●	Delivery Zone charged by Courier Company
●	Expected Charge as per X (Rs.)
●	Charges Billed by Courier Company (Rs.)
●	Difference Between Expected Charges and Billed Charges (Rs.)

# Output Data 2
| Summary                                               | Count     | Amount (Rs.)                   |
|-------------------------------------------------------|-----------|--------------------------------|
| **Total orders where X has been correctly charged**   | <count>   | <total invoice amount>         |
| **Total orders where X has been overcharged**         | <count>   | <total overcharging amount>    |
| **Total orders where X has been undercharged**        | <count>   | <total undercharging amount>   |
