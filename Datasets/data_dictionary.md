# Data Dictionary

**Source:** Internal e-commerce & marketing event logs
**Volume:** 300,000+ records across events, transactions, customers, and campaigns
**Note:** Raw data is not published in this repo due to size/privacy. This document describes the schema powering the Power BI model.

---

## 1. Customers Table
| Column | Type | Description |
|---|---|---|
| **customer_id** | Integer | Unique customer identifier |
|** gender** | Text | Male / Female / Other |
| **age** | Integer | Customer age |
| **country** | Text | Customer's country (US, India, UK, Brazil, Canada, Germany, Australia) |
| **loyalty_tier** | Text | Bronze / Silver / Gold / Platinum |
| **acquisition_channel** | Text | Email / Organic / Paid Search / Referral / Social |
| **signup_date** | Date | Date the customer joined |

## 2. Transactions Table
| Column | Type | Description |
|---|---|---|
| **transaction_id** | Integer | Unique transaction identifier |
| **timestamp** | DateTime | Date and time of the transaction |
| **customer_id** | Integer | Foreign key → Customers |
| **product_id** | Integer | Foreign key → Products |
| **quantity** | Integer | Units purchased |
| **discount_applied** | Decimal | Discount amount/percentage applied to the transaction |
| **gross_revenue** | Decimal | Revenue generated from the transaction |
| **campaign_id** | Integer | Foreign key → Campaigns (0 = no campaign attribution) |
| **refund_flag** | Text | Yes / No — whether the transaction was refunded |

## 3. Products Table
| Column | Type | Description |
|---|---|---|
| **product_id** | Integer | Unique product identifier |
| **category** | Text | Electronics / Fashion / Home / Sports / Beauty |
| **brand** | Text | Brand label (e.g., Brand_70, Brand_75) |
| **base_price** | Decimal | Standard list price |
| **launch_date** | Date | Date the product was launched |
| **is_premium** | Boolean (1/0) | Whether the product is flagged as premium |

## 4. Campaigns Table
| Column | Type | Description |
|---|---|---|
| **campaign_id** | Integer | Unique campaign identifier |
| **channel** | Text | Paid Search / Email / Display / Affiliate / Social |
| **objective** | Text | Cross-sell / Retention / Reactivation / Acquisition |
| **start_date** | Date | Campaign start date |
| **end_date** | Date | Campaign end date |
| **target_segment** | Text | Audience segment targeted (e.g., Deal Seekers, Churn Risk) |
| **expected_uplift** | Decimal | Forecasted revenue uplift (e.g., 0.022 = 2.2%) |

## 5. Events Table (User Behavior)
| Column | Type | Description |
|---|---|---|
| **event_id** | Integer | Unique event identifier |
| **timestamp** | DateTime | Date and time of the event |
| **customer_id** | Integer | Foreign key → Customers |
| **session_id** | Integer | Identifier for the browsing session |
| **event_type** | Text | view / click / add_to_cart / bounce / purchase |
| **product_id** | Integer | Foreign key → Products |
| **device_type** | Text | desktop / mobile / tablet / unknown |
| **traffic_source** | Text | Organic / Paid Search / Affiliate / Email / Social / Display |
| **campaign_id** | Integer | Foreign key → Campaigns (0 = no campaign attribution) |
| **page_category** | Text | Page type where the event occurred (e.g., PLP = Product Listing Page) |
| **session_duration_sec** | Decimal | Duration of the session in seconds |
| **experiment_group** | Text | A/B test group (e.g., Control / Test) |
| **Hour** | Integer | Hour of day the event occurred (0–23) |
| **day** | Text | Day of week (Sun–Sat) |
| **datee** | Date | Calendar date of the event |
| **year** | Integer | Calendar year of the event |

---
