# Analyzing the Relationship Between Ocean Temperature Anomalies and Coral Bleaching Events

This repository explores the impact of ocean temperature anomalies on coral bleaching events. Leveraging a comprehensive dataset of global coral reef observations, this project examines environmental and geographical factors contributing to coral stress and develops predictive models to assess bleaching severity.


---

## Key Highlights

### 1. **Dataset Overview**
- **Source:** Global observations of coral reefs, covering temperature, environmental stressors, and bleaching percentages.
- **Key Features:**
  - **Environmental:** Sea Surface Temperature (SST), Temperature Stress Anomalies (TSA), Degree Heating Weeks (DHW), Turbidity.
  - **Geographical:** Latitude, Longitude, Depth, Distance to Shore, Exposure.
  - **Temporal:** Date (Year, Month, Day extracted for modeling).
  - **Target Variable:** Percentage of coral bleaching.

---

### 2. **Project Goals**
- **Analysis:** Identify key environmental drivers of coral bleaching.
- **Prediction:** Build a robust machine learning model to forecast bleaching severity.
- **Conservation Impact:** Aid in understanding and mitigating the risks posed by climate change to coral ecosystems.

---

### 3. **Insights from Data**
- **Temperature Stress:** Coral bleaching severity increases significantly when SST exceeds 27°C, indicating a critical threshold.
- **Geographical Vulnerability:** Coral reefs in tropical regions, especially the Caribbean and Indo-Pacific, are highly prone to bleaching.
- **Sustained Stress:** Prolonged exposure to heat (measured by DHW) is strongly associated with severe bleaching.

---

## Methods and Models

### 1. **Data Preprocessing**
- Removed irrelevant columns and addressed missing values.
- Encoded categorical variables (e.g., Ocean Name, Exposure) numerically.
- Normalized numerical features using **PowerTransformer** and **RobustScaler**.
- Engineered features like:
  - Interaction terms (e.g., SST × TSA).
  - Rolling averages for time-series effects.
  - Clusters for geographical and environmental patterns using **K-Means**.

---

### 2. **Exploratory Data Analysis**
- Visualized the relationship between SST, anomalies, and bleaching.
- Analyzed geographical distributions of bleaching events and temperature anomalies.
- Explored temporal trends in coral bleaching across decades.

---

### 3. **Modeling Approach**
- Evaluated multiple regression models:
  - Ridge, Elastic Net, Random Forest, Support Vector Regressor (SVR), Decision Tree, CatBoost, and AdaBoost.
- **Best Model:** Random Forest Regressor, tuned via Random Search.
  - **R² Score (Post-Tuning):** 0.7765
  - **MSE:** 0.0525
  - **MAE:** 0.1574
  - **Hyperparameters:**
    ```python
    {
        'n_estimators': 500,
        'max_depth': 30,
        'min_samples_split': 10,
        'min_samples_leaf': 1,
        'max_features': 'sqrt',
        'bootstrap': False
    }
    ```

---

## Results and Visualizations

- **Key Predictors:** SST, anomalies (SSTA, TSA), DHW, and geographical factors (Depth, Distance to Shore).
- **Geographical Hotspots:** Coral bleaching is most severe in the Caribbean, Southeast Asia, and Red Sea regions.
- **Temporal Trends:** Coral bleaching events peaked in the late 1990s and 2005, corresponding to global thermal stress events.

### Model Performance Metrics:
| Metric         | Initial Model | Tuned Model |
|----------------|---------------|-------------|
| **MSE**        | 0.0685        | 0.0525      |
| **RMSE**       | 0.2618        | 0.2291      |
| **MAE**        | 0.1978        | 0.1574      |
| **R² Score**   | 0.7048        | 0.7765      |

---


