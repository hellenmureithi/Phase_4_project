# Traffic Crash Cause Prediction
## Project Overview
In a world where traffic crashes takes so many lives and causes billions in economic damage every year, proactive prevention is the key. This innovative project uses machine learning to predict the main cause of traffic crashes, such as distracted driving and bad weather, by analyzing real world data from the City of Chicago.
By combining simple white-box models like "Decision Trees", with black-box models like "XGBoost", we provide not only predictions but also practical insights to help transportation authorities, urban planners and safety organizations.

## Business Statement
### Problem Statement
Traditional crash analysis relied on manual reports and simple statistics. This method overlooks the complex relationships between factors such as driver behavior, vehicle specs and environmental conditions. This usually limits the development of effective safety policies

### Objectives
- *Main*: Build an accurate, interpretable ML model to predict crash causes

- *Specific*:
  1. Predict the primary crash cause
  2. Ensure model transparency with interpretability techniques.
  3. Analyze and identify the key risk factors 
  4. Compare white-boc vs black-box models to evaluate trade-offs between model accuracy and interpretability
  5. Provide insights to inform on safety intervention and targeted strategies.

### Success Criteria
Achieve a macro F1 score >= 0.50 for a balanced performance.
Explainable predictions.
Provide actionable insights from the model findings on the risk factors. 
Compare performance between white and black box models and evaluate trade-offs between accuracy and interpretability.

## Data Understanding
### Dataset Overview
- Source: Traffic crashes dataset from the City of Chicago Police Departmemnt
- Records: 1,024,029 crash events
- Features: 48 columns(categotical, numerical)
- Target: `PRIM_CONTRIBUTORY_CAUSE`

### Key Features

| Feature                  | Description                                      |
|--------------------------|--------------------------------------------------|
| `posted_speed_limit`     | Posted speed limit on the roadway                |
| `traffic_control_device` | Type of control (stop sign, signal, none, etc.)  |
| `device_condition`       | Working status of traffic control device         |
| `weather_condition`      | Weather at time of crash                         |
| `lighting_condition`     | Lighting condition (daylight, dark, dusk, etc.)  |
| `first_crash_type`       | Type of initial collision                        |
| `roadway_surface_cond`   | Road surface condition (dry, wet, ice, etc.)     |

## Data Preparation
- **Libraries**: 

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![pandas](https://img.shields.io/badge/pandas-1.5+-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-1.23+-013243?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.2+-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-1.7+-5A66FF?style=for-the-badge&logoColor=white)](https://xgboost.readthedocs.io/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7+-11557C?style=for-the-badge&logo=matplotlib&logoColor=white)](https://matplotlib.org/)

- **Steps**:
    - Load and inspect the CSV data
    - Handle missing values
    - Encode categorical variables using OneHotEncoder
    - Stratified train-test split
    - Address severe class imbalance in target variable


## Modeling and Evaluation
| Model                | Accuracy | Macro F1 | Notes                                      |
|----------------------|----------|----------|--------------------------------------------|           |
| Logistic Regression  | 0.6083   | 0.4863   | Simple linear model                        |
| Decision Tree        | 0.6144   | 0.4859   | Interpretable, moderate performance        |
| Random Forest        | 0.6120   | 0.4868   | Bagging ensemble                           |
| **XGBoost**          | **0.7609** | **0.5066** | Best balance of accuracy and class performance |

**Best Model**: XGBoost

##  Model Interpretability

**Global Interpretation**
- White-box models: model coefficients (Logistic Regression), decision paths (Decision Tree), These models provide transparency and valuable for policy explanation
- Black-box models: built-in feature importance + **SHAP** values

**Local Interpretation**
- SHAP explanations for individual predictions, useful for case-level analysis and stakeholder trust.

**Key Findings**
- Top predictors: speed limit, lighting condition, roadway surface condition, trafficway type
- Results align with established traffic safety domain knowledge

##  Business Recommendations

1. **Improve infrastructure in high-risk conditions**  
   - Upgrade lighting on high-speed roads  
   - Enhance road surface maintenance in wet/snow-prone areas  
   - Redesign complex intersections

2. **Target driver behavior**  
   - Launch education campaigns and stricter enforcement on speeding and signal violations  
   - Driver error accounts for >70% of crashes

3. **Adopt interpretable analytics for policy**  
   - Use white-box models for transparent policy communication  
   - Leverage black-box models for maximum predictive power when needed


##  Conclusion

- XGBoost delivers the best performance (76% accuracy, 0.51 macro F1)
- Clear trade-off observed: interpretability vs. predictive power
- Key risk factors validated against real-world traffic safety knowledge
- Provides strong foundation for data-driven road safety improvements

##  Next Steps

- Add spatial analysis (hotspot mapping) and temporal modeling
- Experiment with more granular cause categories
- Deploy interactive web app (Streamlit / Flask) with SHAP explanations