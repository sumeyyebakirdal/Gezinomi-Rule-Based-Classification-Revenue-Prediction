# Gezinomi Potential Customer Revenue Calculation 🏖️

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/pandas-v1.3+-green)
![Classification](https://img.shields.io/badge/Method-Rule--Based_Classification-orange)

## 📌 Business Problem
Gezinomi, a leader in the travel industry, aims to define new level-based sales (personas) by utilizing features of past transactions. By creating segments based on these new definitions, the company intends to:
1. Understand which customer profiles are most profitable.
2. Estimate how much a new potential customer will bring to the company on average.

**Example Case:** What is the expected revenue from a customer who wants to visit an "All Inclusive" hotel in "Antalya" during the "High Season"?

---

## 📂 Dataset Story
The dataset contains transaction records of sales made by Gezinomi. Each row represents a unique sale, meaning the table is not unique by customer (one customer can have multiple sales).

* **Dataset Source:** [Kaggle - Gezinomi Dataset](https://www.kaggle.com/datasets/bsrsrc/gezinomi)
* **Total Observations:** ~19,000+
* **Variables:**
    * `SaleId`: Transaction ID
    * `SaleCityName`: City of the hotel (Antalya, İzmir, Girne, etc.)
    * `ConceptName`: Hotel concept (All Inclusive, Bed & Breakfast, etc.)
    * `Seasons`: Seasonality at the time of check-in (High, Low)
    * `Price`: Revenue generated from the sale
    * `SaleCheckInDayDiff`: Difference between sale date and check-in date

---

## 🛠️ Project Roadmap

### 1. Data Understanding & Preprocessing
* Explored basic statistics and unique values for cities and hotel concepts.
* Created a new categorical variable **`EB_Score`** (Early Booking Score) by binning the `SaleCheckInDayDiff` variable into groups: *Last Minuters, Potential Early Bookers, Early Bookers, and Very Early Bookers.*



### 2. Creating Level-Based Personas
We combined features to create a unique identifier for customer behavior:
* **Formula:** `CITY_CONCEPT_SEASON`
* **Example:** `ANTALYA_ALL INCLUSIVE_HIGH`
* This allows us to treat specific trip types as unique "products" or "personas".

### 3. Segmentation
After calculating the average price for each persona, we divided them into **4 Segments (A, B, C, D)** using the `qcut` method based on their price performance:
* **A & B:** Premium/High-value personas.
* **C & D:** Economy/Standard-value personas.



### 4. Revenue Prediction Logic
A custom function was developed to return the segment and expected average revenue for any new customer persona input.

---

## 🚀 Key Insights
* **Seasonality Impact:** Prices significantly peak during the 'High' season across all popular cities.
* **Location Value:** Cities like Antalya and Girne tend to stay in higher segments (A/B) compared to others.
* **Early Booking:** There is a visible correlation between booking lead time and price stability.

---
