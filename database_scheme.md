# 📦 Workshop Database Tables

This document describes the structure of the SQL tables used in the final project of the Python for Data Operations workshop.

---

## 🛍️ Table: `products`

**Description**: Holds all the products from the company’s cellphone catalog.

**Columns**:
- `product_id` – Unique primary key  
- `brand`  
- `model`  
- `color`  
- `storage`  
- `os`  
- `screen_size`  
- `connectivity`  
- `sim_card`  
- `ram`  
- `memory_card_type`  
- `upc`  

---

## 💳 Table: `transactions`

**Description**: Contains all transaction records for the products.

**Columns**:
- `product_id` – Foreign key to `products`  
- `date`  
- `customer_id` – Primary key  
- `country`  
- `amount_paid`  

---

## 🗣️ Table: `reviews`

**Description**: Contains user-submitted reviews for products.

**Columns**:
- `product_id` – Foreign key to `products`  
- `review`  
- `review_id` – Primary key  
- `user_id`  
- `location`  
- `verified`  
- `user_age_range`  

---

## 🏷️ Table: `labeled_data`

**Description**: Holds the results of labeling (real or LLM-generated) for each review.

**Columns**:
- `product_id`  
- `review`  
- `brand`  
- `model`  
- `color`  
- `brand_mentioned`  
- `model_mentioned`  
- `color_mentioned`  
- `sentiment`  
- `sentiment_intensity`  
- `price_mentioned`  
- `competitor_mentioned`  
- `battery_life_mentioned`  
- `toxic_language`  
- `fake_sounding`  
- `dangrous_content`  
- `review_id`  

> ⚠️ Note: There is a typo in the column name `dangrous_content`. You may want to correct it to `dangerous_content` for clarity and consistency.

---

## 📤 Table: `sent_to_labeling`

**Description**: Tracks which reviews were sent out for labeling and by whom.

**Columns**:
- `review_id`  
- `load_date`  
- `loaded_by`  

---
