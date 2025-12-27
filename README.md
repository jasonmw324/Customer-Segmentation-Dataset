# Mall Customer Segmentation Project

## Project Background
This project analyzes customer behavior at a shopping mall to identify distinct customer segments. Understanding these segments helps the mall design targeted marketing strategies, improve customer engagement, and optimize store layouts or promotions. By grouping similar customers, the mall can better tailor offers based on spending habits, age, and income.

## Objective
Using a selected clustering algorthm find distinct customer segments and based on those clusters characterics suggest hypothetical targeted marketing strategies for each of the clusters.


> The Python code for the analysis can be found [here](Customer_Segmentation.ipynb)(#)

## Dataset Overview
The dataset contains information on **200 mall customers**, with the following variables:

- **customer_id** – unique identifier  
- **age** – customer age
- **gender** – binary indicator of gender (male or female)  
- **annual_income** – yearly income in thousands  
- **spending_score** – measure of purchasing behavior

## Methods

The primary approach for this analysis was **K-Means clustering** to segment customers based on key continuous features. This was chosen based on the following: 
- **Initial Exploration:**  
  During exploratory data analysis (EDA), we assessed the potential impact of categorical variables such as **Gender** on customer behavior. Pairwise scatter plots of Age, Spending Score, and Annual Income showed that Gender was almost evenly distributed across the data, suggesting it would not significantly influence clustering.

- **Alternative Approaches Considered:**  
  Due to k-means only being about to use continious features and standard euclidian distance indorder to account for mixed data types (continuous and categorical), Hierarchical clustering was performed using Gower distance as the dissimilarity metric. However, hierarchical clustering using Gower distance did not produce well-separated clusters, likely due to the limited size of the dataset (200 observations) and the weak influence of categorical variables. The hierarchical clustering analysis suggested two groups, but the separation between them was weak. Increasing the number of groups did not improve the segmentation.

 ![Dendrogram](dendogram.png)
- **Final Model Selection:**  
  Based on the EDA insights and the poor performance of the hierarchical clustering alogrithm gender was dropped and, **K-Means clustering** was chosen using only the continuous features:
  - **Age**
  - **Annual Income (k$)**
  - **Spending Score (1-100)**

- **Number of Clusters (k):**  
  The optimal number of clusters was determined using the **elbow method** to identify diminishing returns in inertia, **silhouette scores** and **visualizations** to assess cluster separation quality.

  ![Elbow Plot](elbow.png)

## Executive Summary

The analysis identified **5 distinct customer groups**:

| Cluster | Label                     | Age       | Spending Score | Annual Income |
|---------|---------------------------|-----------|----------------|---------------|
| 1       | Average Shopper           | 55.64     | 48.85          | 54.38         |
| 2       | Wealthy but Reserved      | 39.87     | 19.36          | 86.10         |
| 3       | Luxury Spenders           | 32.88     | 81.53          | 86.10         |
| 4       | Frugal by Necessity       | 46.25     | 18.35          | 26.75         |
| 5       | Young, Impulsive Spenders | 25.19     | 62.24          | 41.09         |

![3D Cluster Plot](3D-Cluster-Plot.png)



## Recommendations
5 Unique marketing strategies are proposed for each of the distinct types of customer

1. **Average Shopper** – Offer general promotions and loyalty programs to ensure customer retention and consistent shopping.  
2. **Wealthy but Reserved** – Emphasize premium-quality stores and personalized experiences, including upscale restaurant deals and exclusive promotions, rather than frequent sales.  
3. **Luxury Spenders** – Offer more aggressive marketing for high-end items, including premium brand promotions, designer fashion brands, upscale restaurants, and premium jewelry to maximize engagement and sales.  
4. **Frugal by Necessity** – Target this group with more aggressive discounts and value bundles to get large amounts of items for a discounted price.  
5. **Young, Impulsive Spenders** – Collaborate with social media teams to run promotions online to spread awareness and increase sales, focusing on trendy items.

## Next Steps / Future Enhancements
- Explore other clustering methods that can handle categorical variables to see if those methods can account for gender  
- Incorporate additional features like **visit frequency**, **product preferences**, or **demographics**  
- Use **PCA** for dimensionality reduction if dataset expands with more features  

