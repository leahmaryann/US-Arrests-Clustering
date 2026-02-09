# US Crime Clustering – USArrests Dataset

## Project Overview
This project analyses crime data from the 50 US states using the **USArrests dataset** and applies **unsupervised learning techniques** to group states based on their crime profiles. The dataset contains information about violent crime rates (Murder, Assault, and Rape) and the percentage of urban population in each state.

The main objectives of this project are to:

- Understand the structure and characteristics of the dataset
- Explore relationships between crime features
- Standardize and reduce dimensions using **PCA**
- Apply **hierarchical clustering** and **K-means clustering**
- Compare clustering results and interpret patterns among states

The analysis was performed using Python and various data science libraries.

---

## Dataset
The dataset contains crime statistics for the 50 US states. It includes 4 variables describing crime and population characteristics.

### Variables in the Dataset
- **Murder** – Murder rate per 100,000 people
- **Assault** – Assault rate per 100,000 people
- **UrbanPop** – Percentage of population living in urban areas
- **Rape** – Rape rate per 100,000 people

**Dataset shape:** (50, 4)

**Reference:**  
R. R. Johnson and T. L. Johnson (1977). *USArrests Dataset, R Datasets Package*.

---

## Data Cleaning and Preparation
The following preprocessing steps were completed:

- Checked for missing values (none found)
- Verified correct data types
- Identified outliers using boxplots
- Standardized features due to differing variability
- Applied **PCA** for dimensionality reduction

No major cleaning was required as the dataset is well-structured.

---

## Exploratory Data Analysis
EDA was performed to understand patterns and relationships in the data.

**Key steps included:**

- Summary statistics and descriptive analysis
- Boxplots to check variability and outliers
- Correlation analysis using a heatmap
- PCA to identify the most important components

**Important Insights:**

- **Assault** has the highest variability and potential influence on clustering
- Murder, Assault, and Rape are positively correlated
- UrbanPop has weaker correlations with other features
- The first 2 principal components explain ~87% of variance

---

## Model Development

### Principal Component Analysis (PCA)
- Standardized data using `StandardScaler`
- Reduced dimensionality with PCA
- Selected the first 2 components (PC1 and PC2) for clustering

### Hierarchical Clustering
- Tested **Single**, **Average**, and **Complete** linkage methods
- Calculated **Silhouette Scores** for cluster separation:
  - Single: 0.146
  - Average: 0.349
  - Complete: 0.369 ✅ (best separation)
- Complete linkage provided the clearest and most well-defined clusters

### K-means Clustering
- Applied K-means clustering on the first two principal components
- Set number of clusters `k=3`
- Visualized clusters with state annotations
- Clustering results aligned with hierarchical clustering

---

## Key Findings

- **Cluster 1 (Red):** High rates of violent crime (Murder, Assault, Rape)
- **Cluster 2 (Blue):** Low overall crime rate, moderate urbanization
- **Cluster 3 (Green):** Moderate crime rates with higher urban population
- Regional patterns:
  - Cluster 1: Mostly Midwestern and Northern states
  - Cluster 2: Mostly Southern states
  - Cluster 3: Mostly Western states

States within the same cluster share similar crime profiles, indicating regional crime trends in the US.

---

## Tools and Libraries Used

- Python
- `pandas` – Data manipulation
- `numpy` – Numerical computing
- `seaborn` – Data visualization
- `matplotlib` – Plotting
- `scikit-learn` – PCA, K-means, clustering, scaling
- `scipy` – Hierarchical clustering

---

## How to Run the Project

1. Ensure the file `UsArrests.csv` is in the project directory
2. Open `analysis.ipynb` (or your Python script) in Jupyter Notebook
3. Run the notebook/script cells to reproduce the analysis, PCA, and clustering results

