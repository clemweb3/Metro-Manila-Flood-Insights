# 🌊 Metro Manila Flood Prediction & Risk Insights Dashboard
Dashboard Overview
## Dashboard Overview

![Dashboard Overview](images/dashboard_overview.png)

End-to-end analysis of Metro Manila flood data, combining spatial, meteorological, and topographic information with predictive modeling and an interactive Power BI dashboard.

## Project Overview

This project builds a full pipeline to understand and predict flood behavior:

- Starting from raw geospatial and rainfall data sourced online. 
- Performing data cleaning, outlier detection, and feature engineering.  
- Engineering interpretable flood risk indices and spatial clusters.  
- Training predictive models from baseline linear regression to non-linear random forest to improve accuracy.  
- Exporting a refined dataset for dashboard visualization in Power BI.  

**The dashboard aims to answer practical questions:**

- Which areas in Metro Manila are most vulnerable to flooding?  
- How do elevation, rainfall, and neighborhood characteristics influence flood height?  
- Can we translate predicted flood heights into actionable risk tiers for decision-makers?  

## Pipeline Steps

### 1. Data Ingestion & Validation
- Raw dataset includes latitude, longitude, elevation, rainfall, and recorded flood height.  
- Data checks included:  
  - Missing values: none detected  
  - Duplicate rows: 2 removed  
  - Outlier detection using IQR: 503 elevation points, 62 precipitation points flagged  

### 2. Feature Engineering & Preprocessing
- Binned continuous features (`elevation_bin`, `precip_bin`) for dashboard readability  
- Created a **Flood Risk Index** (scaled) for intuitive risk comparison across areas  
- Applied **spatial clustering** (KMeans, 20 clusters) to capture neighborhood-level risk patterns  
- Developed domain-inspired interaction features:  
  - `elev_precip_interaction`  
  - Flags for `low_elev_high_rain`, `very_low_elev`, and `very_high_rain`  
- Cleaned, processed dataset exported for modeling  

### 3. Predictive Modeling
- Features separated into numeric and categorical for consistent preprocessing  
- Pipelines ensured reproducibility:  
  - Numeric features standardized  
  - Categorical features one-hot encoded  
- Baseline model: **Linear Regression**  
- Performance on test set:  
  - RMSE: 1.870 (average flood height units)  
  - R²: -0.003 (linear model struggled to explain variance, motivating non-linear modeling in next steps)  
- Output included predicted flood heights and derived **risk tiers** for visualization  

### 4. Dashboard Preparation
- Exported dataset contains both observed and predicted flood heights.  
- Key features included for Power BI: location, elevation, rainfall, cluster statistics, interaction features, risk tiers.
- Dashboard-ready structure allows dynamic filtering by cluster, risk level, and rainfall scenarios. 

## Key Insights

- Flood height is not linearly correlated with elevation alone—rainfall and neighborhood context (clusters) matter.  
- Interaction features highlight extreme-risk zones even in areas that appear safe based on elevation. 
- Spatial clustering allows the dashboard to show high-risk neighborhoods without overwhelming detail. 

## Business Takeaway

- Decision-makers can quickly identify areas at risk under different rainfall scenarios.  
- Risk tiers translate numeric predictions into actionable guidance.  
- Dashboard supports urban planning, disaster preparedness, and community alerts.  

## 🤖 Why Power BI?

- Widely used in business intelligence and decision-making environments.  
- Supports geospatial visualization and dynamic filtering out-of-the-box.
- Integrates seamlessly with preprocessed CSV outputs for rapid dashboard development. 

## What I Learned

- Feature engineering is critical: derived indices and interaction features often convey more business value than model accuracy alone.
- Linear models can provide intuition but may underestimate complex flood behaviors, so scaling up or considering non-linear models for development is crucial. 
- Preparing data for dashboards requires balancing interpretability with predictive sophistication.
- Even modest predictive models can power meaningful visual insights if risk tiers and clustering are thoughtfully designed. 

## References

- AEGIS Metro Manila Flood Dataset (sourced online)  
