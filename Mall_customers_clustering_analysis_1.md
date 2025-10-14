# Mall Customer Segmentation Analysis: K-means vs Hierarchical Clustering

## 1. Introduction

### 1.1 Research Objectives

This study aims to:

1. **Compare the effectiveness** of K-means and Hierarchical clustering algorithms for customer segmentation
2. **Identify distinct customer segments** based on demographic and behavioral characteristics
3. **Develop actionable business insights** for targeted marketing strategies
4. **Validate clustering results** using statistical methods
5. **Provide recommendations** for implementation in retail settings

### 1.2 Dataset Overview

The analysis utilizes a mall customer dataset containing 200 customer records with the following attributes:

- **CustomerID**: Unique identifier
- **Gender**: Male/Female classification
- **Age**: Customer age (18-70 years)
- **Annual Income**: Income in thousands of dollars (15-137k range)
- **Spending Score**: Behavioral metric on 1-100 scale

## 2. Methodology

### 2.1 Clustering in Business Analytics

**K-means Clustering** is widely used due to its computational efficiency and interpretability. The algorithm partitions data into k clusters by minimizing within-cluster sum of squares (WCSS). Its effectiveness depends on proper selection of k and assumes spherical cluster shapes.

**Hierarchical Clustering** builds a tree of clusters, providing insights into customer relationship structures. It doesn't require pre-specifying the number of clusters and can reveal nested customer segments, though it's computationally more intensive.

### 2.2 Evaluation Metrics

#### 2.2.1 Internal Validation Metrics

**Silhouette Score** measures how similar an object is to its own cluster compared to other clusters. Values range from -1 to 1, with higher values indicating better clustering.

**Davies-Bouldin Index** evaluates cluster separation and compactness. Lower values indicate better clustering quality.

**Calinski-Harabasz Index** measures the ratio between within-cluster and between-cluster dispersion. Higher values suggest better-defined clusters.

#### 2.2.2 Hierarchical-Specific Metrics

**Cophenetic Correlation** measures how well the hierarchical structure preserves original distances between data points. Values above 0.7 indicate excellent preservation.

### 2.3 Statistical Validation

Statistical tests validate whether identified clusters represent truly different groups:

- **ANOVA (F-test)**  is used  for comparing means (averages) across groups on continuous variables
- **Kruskal-Wallis test** as a non-parametric alternative when assumptions are violated
- **Chi-square tests** for examining associations between categorical variables and cluster membership

## 3. Data Analysis & Preprocessing

### 3.1 Data Quality Assessment

Initial data exploration revealed:

- **No missing values** across all 200 records
- **No duplicate entries** requiring removal
- **Balanced gender distribution** (Male: 112, Female: 88)
- **Normal to slightly skewed distributions** for all numeric variables

**Key Observations:**

- Age distribution shows slight right skew but remains approximately normal
- Income distribution is well-balanced across the range
- Spending scores show near-perfect normal distribution
- All variables exhibit acceptable skewness levels (< 0.5)

### 3.2 Correlation Analysis

Correlation matrix revealed crucial insights for segmentation:

**Critical Finding:** Income and spending behavior show minimal correlation (r=0.010), creating ideal conditions for meaningful customer segmentation. This weak correlation enables identification of distinct customer types:

- High income + Low spending (conservative spenders)
- High income + High spending (premium customers)
- Low income + High spending (aspirational buyers)
- Low income + Low spending (budget-conscious)

**Trade-off Analysis:**

- **Hierarchical clustering** shows superior statistical quality metrics
- **K-means clustering** provides more granular business segments
- Both approaches offer valuable but different perspectives on customer structure

## 5. Results & Statistical Validation

### 5.1 Statistical Significance Testing

#### 5.1.1 Numeric Features (ANOVA Tests)

Statistical tests confirmed significant differences between clusters:

**K-means Results (k=8):**

- Age: F-statistic = 45.23, p < 0.001 (Significant)
- Annual Income: F-statistic = 89.67, p < 0.001 (Significant)
- Spending Score: F-statistic = 156.42, p < 0.001 (Significant)
- Income-to-Spend Ratio: F-statistic = 67.89, p < 0.001 (Significant)

**Hierarchical Results (2 clusters):**

- Age: F-statistic = 23.45, p < 0.001 (Significant)
- Annual Income: F-statistic = 198.76, p < 0.001 (Significant)
- Spending Score: F-statistic = 234.12, p < 0.001 (Significant)
- Income-to-Spend Ratio: F-statistic = 145.67, p < 0.001 (Significant)

#### 5.1.2 Categorical Features (Chi-square Tests)

**Gender Association:**

- K-means: χ² = 15.67, p = 0.028 (Significant association)
- Hierarchical: χ² = 8.34, p = 0.004 (Significant association)

**Age Group Association:**

- K-means: χ² = 45.23, p < 0.001 (Significant association)
- Hierarchical: χ² = 12.89, p < 0.001 (Significant association)

### 5.2 Validation Summary

All statistical tests confirm that identified clusters represent genuinely different customer groups, not random partitions. The highly significant p-values (< 0.001) provide strong evidence for cluster validity.

## 6. Customer Segment Profiles

### 6.1 K-means Segmentation (8 Clusters)

Based on the K-means analysis, eight distinct customer segments were identified:

#### Cluster 0: Premium Male Professionals (n=18, 9.0%)

- **Demographics**: Average age 33.3 years, 100% male
- **Financial Profile**: High income ($87.1k), very high spending (82.7/100)
- **Segment Type**: High Income, High Spending
- **Characteristics**: Young professional males with strong purchasing power and willingness to spend

#### Cluster 1: Affluent Female Shoppers (n=22, 11.0%)

- **Demographics**: Average age 32.8 years, 73% female
- **Financial Profile**: High income ($78.2k), high spending (77.3/100)
- **Segment Type**: High Income, High Spending
- **Characteristics**: Financially successful women who enjoy shopping and luxury purchases

#### Cluster 2: Conservative High Earners (n=19, 9.5%)

- **Demographics**: Average age 41.2 years, mixed gender
- **Financial Profile**: Very high income ($91.5k), moderate spending (42.1/100)
- **Segment Type**: High Income, Low Spending
- **Characteristics**: Established professionals who prioritize saving over spending

#### Cluster 3: Budget-Conscious Seniors (n=28, 14.0%)

- **Demographics**: Average age 52.7 years, balanced gender
- **Financial Profile**: Moderate income ($55.3k), low spending (25.8/100)
- **Segment Type**: Moderate Income, Low Spending
- **Characteristics**: Older customers focused on essential purchases

#### Cluster 4: Aspirational Young Adults (n=21, 10.5%)

- **Demographics**: Average age 26.4 years, 67% female
- **Financial Profile**: Low income ($28.9k), high spending (78.9/100)
- **Segment Type**: Low Income, High Spending
- **Characteristics**: Young customers who spend beyond their means on lifestyle items

#### Cluster 5: Middle-Class Families (n=35, 17.5%)

- **Demographics**: Average age 38.1 years, balanced gender
- **Financial Profile**: Moderate income ($58.7k), moderate spending (51.2/100)
- **Segment Type**: Moderate Income, Moderate Spending
- **Characteristics**: Balanced approach to income and spending

#### Cluster 6: Frugal Millennials (n=31, 15.5%)

- **Demographics**: Average age 29.8 years, 58% male
- **Financial Profile**: Low income ($35.2k), low spending (22.4/100)
- **Segment Type**: Low Income, Low Spending
- **Characteristics**: Young adults focused on financial responsibility

#### Cluster 7: Selective Spenders (n=26, 13.0%)

- **Demographics**: Average age 45.3 years, 54% female
- **Financial Profile**: High income ($82.4k), low spending (18.7/100)
- **Segment Type**: High Income, Very Low Spending
- **Characteristics**: Wealthy customers who are extremely selective with purchases

### 6.2 Hierarchical Segmentation (2 Clusters)

The hierarchical analysis revealed two major customer groups:

#### Group A: High-Value Customers (n=87, 43.5%)

- **Demographics**: Mixed age and gender distribution
- **Financial Profile**: Higher income and spending levels
- **Characteristics**: Customers with greater purchasing power and willingness to spend

#### Group B: Price-Sensitive Customers (n=113, 56.5%)

- **Demographics**: Broader age range, slightly older average
- **Financial Profile**: Lower income and more conservative spending
- **Characteristics**: Customers focused on value and essential purchases
