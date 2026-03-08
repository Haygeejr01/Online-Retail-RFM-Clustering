# Customer Segmentation via RFM Analysis & K-Means Clustering

## Overview
This project applies unsupervised machine learning to real-world e-commerce transaction data. The goal was to transform raw sales data into actionable, behavioral customer segments using **RFM (Recency, Frequency, Monetary)** modeling and **K-Means Clustering**. 

Instead of forcing a single mathematical output, this project provides a "menu" of segmentation strategies (2, 3, and 4 clusters) to allow marketing stakeholders to choose the model that best fits their campaign budget and retention goals.

## The Business Problem
Marketing teams waste resources when they apply a "one-size-fits-all" approach to promotions. By clustering customers based on their actual purchasing habits, the business can deploy targeted campaigns—such as rewarding VIPs, re-engaging hibernating accounts, or offering second-purchase discounts to new buyers.

## Tools & Tech Stack
* **Python** (Data manipulation and modeling)
* **Pandas & NumPy** (Data cleaning, aggregation, and RFM feature engineering)
* **Scikit-Learn** (StandardScaler, K-Means algorithm)
* **Matplotlib** (3D Scatter plotting and data visualization)

## Methodology
1. **Data Preprocessing:** Cleaned the raw online retail dataset by handling missing values and removing canceled orders.
2. **Feature Engineering (RFM):** Aggregated transaction data at the customer level to calculate:
   * *Recency:* Days since the last purchase.
   * *Frequency:* Total number of purchases.
   * *Monetary:* Total money spent.
3. **Scaling:** Applied `StandardScaler` to handle the heavy right-skewness of the Monetary and Frequency variables, ensuring the distance-based K-Means algorithm weighed all features equally.
4. **Hyperparameter Tuning:** Evaluated the optimal number of clusters (k) using the **Elbow Method (Inertia)** and **Silhouette Score**.

## Results & Business Strategy Options
While the mathematical evaluations strongly pointed to **k=2** as the cleanest split, pure mathematics doesn't always provide the granularity required for marketing. I developed three distinct models for stakeholder review:

* **Option 1: The 2-Cluster Model (The Mathematical Ideal)**
  * Splits the dataset purely into *High-Value* and *Low-Value/Lost* customers. Best for broad, high-level campaigns.
* **Option 2: The 3-Cluster Model (The Balanced Approach)**
  * Segments into *VIPs, Regulars,* and *Lost* customers. Ideal for standard retention programs.
* **Option 3: The 4-Cluster Model (The Granular Approach)**
  * **The VIPs (Champions):** Lowest recency (avg 10 days), high frequency (13 purchases), massive spend (£7,793).
  * **The Regulars:** Consistent mid-tier buyers (£1,743 average spend).
  * **New/Promising:** Recent visits, but very low frequency and spend. Prime targets for conversion campaigns.
  * **Lost/Hibernating:** Highest recency (183 days) and lowest spend. 

## Visualizations
By plotting the standardized RFM values on a 3D axis, we can physically see how the K-Means algorithm separated the customer base.

![3D Cluster Plot](online4.jpg)

## How to Run This Project
1. Clone the repository.
2. **Unzip the `online_retail.zip` file** to access the raw dataset.
3. Ensure you have the required libraries installed (`pip install pandas numpy scikit-learn matplotlib`).
4. Run the Jupyter Notebook to see the step-by-step EDA, clustering logic, and 3D visualizations. 
5. The final segmented dataset is exported as `rfm_customer_segments.csv`.
