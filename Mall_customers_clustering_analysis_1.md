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

**K-means Clustering** is used due to its computational efficiency and interpretability. The algorithm partitions data into k clusters by minimizing within-cluster sum of squares (WCSS). Its effectiveness depends on proper selection of k and assumes spherical cluster shapes.

**Hierarchical Clustering** builds a tree of clusters, providing insights into customer relationship structures. It doesn't require pre-specifying the number of clusters and can reveal nested customer segments, though it's computationally more intensive.

### 2.2 Evaluation metrics (plain language)

We used a few simple scores to check whether the groups we found are meaningful:

- Silhouette score: Think of this as a clarity score for each group. A higher number (closer to 1) means members of a group are more similar to each other than to people in other groups — in other words, the group is 'clean' and well-separated.
- Davies–Bouldin index: This is a compactness/separation check. A smaller value is better — it means groups are tight and well apart from one another.
- Calinski–Harabasz index: This compares how spread out groups are between each other versus how spread they are inside themselves. A higher value means the groups are more distinct.

These metrics give different views on the same question: do the clusters make sense? We look for consistently good results across them rather than focusing on any single number.

#### Hierarchical-specific check

- Cophenetic correlation: For hierarchical clustering we build a tree showing how groups merge. This number tells us how faithfully that tree represents the actual differences between customers. Values closer to 1 mean the tree is a good reflection of the data; values well below 0.7 suggest the tree may be a loose fit.

### 2.3 Statistical validation

We also use standard statistical checks to make sure the groups are not just random splits:

- ANOVA (F-test): Tests whether the average values (like average age or average income) are different across groups. If the test says "yes," it means those averages are unlikely to be the same by chance.
- Kruskal–Wallis test: A backup test used when the data don't meet the usual assumptions (for example, if distributions are not normal). It asks the same basic question as ANOVA but in a safer way for messy data.
- Chi-square test: Used for categories (for example, gender or age group). It checks whether category counts are spread differently across clusters — for instance, whether some clusters have mostly men while others have mostly women.

Together, these tests tell us whether the numerical and categorical differences we see between groups are real and useful for decision-making.

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

#### Statistical significance

Both the K-means (8 groups) and the Hierarchical (2 groups) segmentations show clear, meaningful differences between their groups for the key numeric measures we looked at: age, annual income, spending score, and the income-to-spend ratio. In everyday terms, this means the clusters are not just random splits of customers — they represent real, distinguishable groups.

What this implies for the business:

- Age: Different clusters contain people of different ages, so age is a useful factor for tailoring promotions.
- Annual Income: The clusters separate customers by income level, so pricing or premium offers can be targeted appropriately.
- Spending Score: Customers in different clusters show distinct spending behaviors, so marketing tactics (discounts, loyalty perks, premium upsells) can be customized per group.
- Income-to-Spend Ratio: The balance between income and spending differs across groups, helping identify customers who spend more than expected for their income (opportunity) and those who are conservative spenders (cost-conscious targets).

In short: the statistical tests confirm the clusters capture meaningful differences that a business can act on, such as tailored promotions, pricing strategies, or customer loyalty programs.

#### 5.1.2 Categorical features

- Gender: Both K-means and Hierarchical clustering show a meaningful relationship between cluster membership and gender. In practice this means some clusters contain noticeably more men or more women — a useful signal for tailoring gender-specific offers or communications.
- Age group: Both methods also show clear differences in age-group composition across clusters. In short, clusters tend to contain different age mixes, so age-based messaging or product targeting is likely to be effective.

### 5.2 Validation summary

All of the checks we ran — the clarity/compactness scores and the statistical tests for numeric and categorical features — point in the same direction: the groups we found are meaningfully different from one another and not the result of random chance. That gives us confidence that the segments are actionable for marketing and pricing decisions.

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
