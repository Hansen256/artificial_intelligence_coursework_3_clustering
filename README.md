# Mall Customers Clustering Analysis

## Overview

This project implements a comprehensive customer segmentation analysis for a mall using two popular clustering algorithms: K-means and Hierarchical clustering. The analysis compares both approaches to identify meaningful customer segments based on demographic and behavioral characteristics, providing actionable business insights for targeted marketing strategies.

## Dataset

The analysis uses the Mall Customers dataset containing 200 customer records with the following features:

- **CustomerID**: Unique identifier for each customer
- **Genre**: Gender (Male/Female)
- **Age**: Customer age in years (18-70)
- **Annual Income (k$)**: Annual income in thousands of dollars (15-137k)
- **Spending Score (1-100)**: Behavioral metric indicating spending behavior and loyalty (1-99)

## Project Structure

``` txt
├── mall_customers_analysis_simple.ipynb  # Main analysis notebook
├── Mall_Customers.csv                     # Dataset file
├── Mall_Customers_Clustering_Report.md    # Detailed analysis report
└── README.md                              # This file
```

## Key Findings

### Clustering Results

- **K-means Clustering**: Identified 8 distinct customer segments (optimal k=8, silhouette score: 0.342)
- **Hierarchical Clustering**: Identified 2 major customer groups (silhouette score: 0.663)

### Customer Segments (K-means)

1. **Premium Male Professionals**: High-income males with high spending
2. **Affluent Female Shoppers**: High-income females with high spending
3. **Conservative High Earners**: High-income customers with moderate spending
4. **Budget-Conscious Seniors**: Older customers with moderate income and low spending
5. **Aspirational Young Adults**: Low-income customers with high spending
6. **Middle-Class Families**: Balanced income and spending patterns
7. **Frugal Millennials**: Low-income, low-spending young adults
8. **Selective Spenders**: High-income customers with very low spending

## Requirements

### Python Libraries

- pandas >= 2.3.2
- numpy >= 1.24.0
- scikit-learn >= 1.6.1
- matplotlib >= 3.9.4
- seaborn >= 0.13.2
- scipy >= 1.13.1

### Installation

```bash
pip install pandas numpy scikit-learn matplotlib seaborn scipy
```

## How to Run

### Prerequisites

- Python 3.8 or higher
- Git (for cloning the repository)
- Jupyter Notebook or VS Code with Python extension

### Step-by-Step Instructions

1. **Clone the Repository**

   ```bash
   git clone https://github.com/Hansen256/artificial_intelligence_coursework_3_clustering.git
   cd artificial_intelligence_coursework_3_clustering
   ```

2. **Install Dependencies**

   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn scipy
   ```

3. **Run the Analysis**
   - Open `mall_customers_analysis_simple.ipynb` in Jupyter Notebook or VS Code
   - Execute all cells in sequence to reproduce the complete analysis
   - Alternatively, run the notebook programmatically:

     ```bash
     jupyter nbconvert --execute mall_customers_analysis_simple.ipynb --to notebook --inplace
     ```

4. **View Results**
   - Check the generated visualizations and statistical outputs
   - Refer to `Mall_Customers_Clustering_Report.md` for detailed analysis report

## Usage

### Running the Analysis

1. Ensure all required libraries are installed
2. Open `mall_customers_analysis_simple.ipynb` in Jupyter Notebook or VS Code
3. Run all cells in sequence to reproduce the analysis

### Key Analysis Steps

1. **Data Loading & Preprocessing**: Load dataset, handle missing values, feature engineering
2. **Exploratory Data Analysis**: Statistical summaries, correlation analysis, visualizations
3. **K-means Clustering**: Determine optimal k, perform clustering, evaluate results
4. **Hierarchical Clustering**: Compare linkage methods, determine optimal clusters
5. **Statistical Validation**: ANOVA tests, chi-square tests for cluster significance
6. **Business Insights**: Segment profiling, marketing recommendations

## Business Insights

### Strategic Recommendations

- **Premium Segments**: Focus on luxury products, VIP services, and exclusive experiences
- **Aspirational Segments**: Offer flexible payment options and trend-focused marketing
- **Value-Conscious Segments**: Emphasize competitive pricing and loyalty rewards

### Expected Business Impact

- Improved customer satisfaction through personalized approaches
- Increased conversion rates via targeted marketing (15-25% potential improvement)
- Better resource allocation based on segment-specific strategies
- Enhanced customer lifetime value through segment-appropriate retention programs

## Methodology

### Clustering Algorithms

- **K-means**: Partition-based clustering with elbow method and silhouette analysis for optimal k selection
- **Hierarchical**: Agglomerative clustering with Ward and complete linkage comparison

### Evaluation Metrics

- Silhouette Score: Measures cluster cohesion and separation
- Davies-Bouldin Index: Evaluates cluster compactness and separation
- Calinski-Harabasz Index: Ratio of between-cluster to within-cluster dispersion
- Cophenetic Correlation: Preserves original distance relationships (hierarchical)

### Statistical Validation

- ANOVA F-tests for continuous variables across clusters
- Chi-square tests for categorical associations
- All results statistically significant (p < 0.001)

## Results Summary

| Method | Clusters | Silhouette Score | Davies-Bouldin | Best Use Case |
|--------|----------|------------------|----------------|---------------|
| K-means | 8 | 0.342 | 0.966 | Detailed segmentation |
| Hierarchical | 2 | 0.663 | 0.306 | Major group identification |

## Limitations

- Cross-sectional data (no temporal analysis)
- Limited to 200 customers from single location
- Basic demographic and behavioral features only
- Internal validation only (no external business metrics)
