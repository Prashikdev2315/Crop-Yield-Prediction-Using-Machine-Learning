# Crop Yield Prediction Using Machine Learning

A machine learning project that predicts crop yield based on various environmental and agricultural factors using Linear Regression and Random Forest models.

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Features & Target Variable](#features--target-variable)
- [Project Workflow](#project-workflow)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Machine Learning Models](#machine-learning-models)
- [Results & Performance](#results--performance)
- [Key Insights](#key-insights)
- [Installation & Usage](#installation--usage)
- [Project Structure](#project-structure)
- [Requirements](#requirements)
- [Future Improvements](#future-improvements)
- [Author](#author)

---

## 📊 Project Overview

This project aims to develop a predictive model for crop yield (measured in hg/ha - hectograms per hectare) using machine learning algorithms. By analyzing historical agricultural data including weather conditions, pesticide usage, and regional factors, the models can estimate expected crop productivity.

**Goal:** Build an accurate predictive model to forecast crop yield across different regions, crops, and years.

**Applications:**
- Agricultural planning and resource allocation
- Yield forecasting for policy makers
- Farmer decision support systems
- Climate impact assessment on agriculture

---

## 📈 Dataset Description

### Data Source
The dataset contains **agricultural records spanning multiple years across various global regions**.

### Dataset Dimensions
- **Total Records:** ~2,245 rows
- **Features:** 6 input features + 1 target variable
- **Missing Values:** None (after data cleaning)
- **Crops Analyzed:** 10 different crop types
- **Geographic Coverage:** Multiple countries/regions

### Key Statistics
- **Year Range:** Historical data spanning multiple years
- **Yield Range (hg/ha):** Varies significantly by crop and region
- **Rainfall:** Measured in mm/year
- **Temperature:** Measured in °C
- **Pesticides:** Measured in tonnes

---

## 🎯 Features & Target Variable

### Input Features (Predictors)

| Feature | Description | Data Type | Units |
|---------|-------------|-----------|-------|
| **Area** | Geographic region/country | Categorical | - |
| **Item** | Type of crop grown | Categorical | - |
| **Year** | Year of harvest | Numeric | Year |
| **average_rain_fall_mm_per_year** | Total annual precipitation | Numeric | mm |
| **pesticides_tonnes** | Amount of pesticides used | Numeric | tonnes |
| **avg_temp** | Average annual temperature | Numeric | °C |

### Target Variable

| Variable | Description | Data Type | Units |
|----------|-------------|-----------|-------|
| **hg/ha_yield** | Crop yield per hectare | Numeric | hg/ha |

**Note:** 1 hg/ha ≈ 0.1 kg/ha. Typical wheat yield ranges from 30,000–50,000 hg/ha.

### Crops Included in Dataset
- Wheat
- Maize (Corn)
- Rice
- Barley
- Oats
- Rye
- Sorghum
- Soybeans
- Potatoes
- Cotton

---

## 🔄 Project Workflow

### 1. **Data Loading & Exploration**
```
├── Load dataset from CSV
├── Check dimensions and structure
├── Examine data types
└── Display first few rows
```

### 2. **Data Cleaning & Preprocessing**
```
├── Handle missing values
│   ├── Numeric columns → Impute with median
│   └── Categorical columns → Impute with mode
├── Enforce correct data types
├── Remove duplicate/unnamed columns
└── Reset index for clean dataset
```

### 3. **Feature Engineering**
```
├── Label Encode categorical variables
│   ├── Area → Numeric mapping
│   └── Item (Crop) → Numeric mapping
└── Prepare feature matrix (X) and target vector (y)
```

### 4. **Exploratory Data Analysis (EDA)**
```
├── Statistical summaries
├── Correlation analysis
├── Univariate visualizations
└── Feature relationships with yield
```

### 5. **Model Development**
```
├── Train-Test Split (80-20%)
├── Train Linear Regression model
├── Train Random Forest Regressor (100 trees)
└── Evaluate both models
```

### 6. **Prediction & Validation**
```
├── Generate predictions on test set
├── Compare model performance metrics
├── Make custom predictions
└── Interpret results
```

---

## 📊 Exploratory Data Analysis (EDA)

### Key Visualizations Included

#### 1. **Correlation Heatmap**
- Shows relationships between all features and yield
- **Insight:** Pesticide usage and Area show the strongest correlation with yield

#### 2. **Rainfall vs Crop Yield**
- Scatter plot with trend line
- **Insight:** No strong linear relationship—yield depends on multiple factors

#### 3. **Temperature vs Crop Yield**
- Scatter plot showing temperature impact
- **Insight:** Higher temperatures show slight negative effect in some regions

#### 4. **Pesticide Usage vs Crop Yield**
- Scatter plot (95th percentile capped for clarity)
- **Insight:** Positive correlation with yield, possibly reflecting intensive farming practices

#### 5. **Crop Distribution**
- Horizontal bar chart showing record count per crop
- **Insight:** All 10 crops are fairly uniformly represented

#### 6. **Top 10 Highest-Yielding Areas**
- Bar chart of areas by average yield
- **Insight:** UK, Belgium, and Denmark rank highest—reflecting optimized agriculture

---

## 🤖 Machine Learning Models

### Model 1: Linear Regression

**Description:** A parametric model that fits a linear relationship between features and target.

**Advantages:**
- Simple and interpretable
- Fast training and prediction
- Good baseline for comparison
- Provides feature coefficients

**Algorithm:**
- Minimizes sum of squared residuals
- No hyperparameters to tune

### Model 2: Random Forest Regressor

**Description:** An ensemble method combining multiple decision trees for robust predictions.

**Hyperparameters Used:**
- `n_estimators=100` (100 trees for balance between accuracy and speed)
- `random_state=42` (for reproducibility)
- `n_jobs=-1` (parallel processing on all CPU cores)

**Advantages:**
- Handles non-linear relationships well
- Robust to outliers
- Captures feature interactions
- Provides feature importance rankings
- Less prone to overfitting than single trees

---

## 📈 Results & Performance

### Model Comparison Metrics

Both models are evaluated on the test set (20% of data) using three key metrics:

#### 1. **Mean Absolute Error (MAE)**
- Average absolute difference between predicted and actual values
- **Unit:** hg/ha
- **Interpretation:** Lower is better

#### 2. **Root Mean Squared Error (RMSE)**
- Penalizes larger errors more heavily
- **Unit:** hg/ha
- **Interpretation:** Lower is better

#### 3. **R² Score (Coefficient of Determination)**
- Proportion of variance explained by the model
- **Range:** 0 to 1 (higher is better)
- **Interpretation:**
  - 0.8-1.0 → Excellent fit
  - 0.6-0.8 → Good fit
  - 0.4-0.6 → Fair fit
  - <0.4 → Poor fit

### Expected Performance Range

Based on the project structure:
- **Linear Regression:** Expected R² around 0.60-0.75 (good for baseline)
- **Random Forest:** Expected R² around 0.75-0.90 (superior performance)

---

## 💡 Key Insights

### 1. **Feature Importance**
- **Pesticide Usage & Area** are the strongest predictors of yield
- **Temperature & Rainfall** have indirect effects through other mechanisms
- **Year** captures temporal trends in agricultural improvements

### 2. **Geographic Variation**
- Significant yield differences across regions
- UK, Belgium, Denmark achieve higher yields (advanced farming techniques)
- Regional factors (soil, infrastructure) are crucial

### 3. **Climate Impact**
- No simple linear relationship between weather and yield
- Crop-specific responses to temperature and rainfall
- Complexity suggests need for crop-specific sub-models

### 4. **Pesticide Correlation**
- Positive correlation with yield likely reflects:
  - Intensive farming in high-yield regions
  - More investment in crop protection
  - Correlation ≠ causation

### 5. **Model Insights**
- Random Forest outperforms Linear Regression
- Indicates non-linear relationships in the data
- Ensemble approach captures complex interactions

---

## 🚀 Installation & Usage

### Prerequisites
- Python 3.7 or higher
- Jupyter Notebook or JupyterLab

### Installation Steps

1. **Clone or download the repository:**
   ```bash
   git clone https://github.com/Prashikdev2315/Crop-Yield-Prediction-Using-Machine-Learning.git
   cd "Crop Yield Prediction Using Machine Learning"
   ```

2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install required packages:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook Crop_Yield_Prediction.ipynb
   ```

### Making Predictions

Edit the sample input section in the notebook:

```python
sample_area       = "Albania"          # Change to any country in dataset
sample_crop       = "Wheat"            # Change to any crop type
sample_rainfall   = 700.0              # mm per year
sample_temperature= 16.5               # °C
sample_pesticides = 121.0              # tonnes
sample_year       = 2010               # Year
```

The notebook will output predictions from both models for your custom input.

---

## 📁 Project Structure

```
Crop Yield Prediction Using Machine Learning/
├── Crop_Yield_Prediction.ipynb          # Main notebook with all analysis
├── Crop Yield Prediction Using Machine Learning.pdf  # Supporting documentation
├── yield_df.csv                         # Dataset (to be loaded)
├── requirements.txt                     # Python package dependencies
└── README.md                            # This file
```

### Notebook Sections

1. **Imports & Configuration** – Load libraries and set up visualization
2. **Data Loading** – Read dataset from CSV
3. **Data Exploration** – Shape, types, statistics, unique values
4. **Data Cleaning** – Handle missing values and ensure correct types
5. **Feature Engineering** – Label encode categorical variables
6. **Exploratory Data Analysis** – Correlation, distributions, relationships
7. **Feature & Target Definition** – Prepare X and y
8. **Train-Test Split** – 80-20 split with stratification
9. **Model Training** – Train Linear Regression and Random Forest
10. **Model Evaluation** – Compare metrics on test set
11. **Custom Predictions** – Make predictions on new data

---

## 📦 Requirements

Create a `requirements.txt` file with the following packages:

```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=0.24.0
jupyter>=1.0.0
```

**Installation:**
```bash
pip install -r requirements.txt
```

---

## 🔮 Future Improvements

### Model Enhancements
- [ ] **Hyperparameter Tuning** – GridSearchCV/RandomizedSearchCV for optimal parameters
- [ ] **Cross-Validation** – K-fold CV for more robust evaluation
- [ ] **Feature Selection** – Identify and remove redundant features
- [ ] **Gradient Boosting Models** – Try XGBoost, LightGBM for better performance
- [ ] **Neural Networks** – Deep learning approaches for complex patterns

### Feature Engineering
- [ ] **Crop-Specific Sub-models** – Separate models for different crop types
- [ ] **Temporal Features** – Extract month, season, or weather trends
- [ ] **Region-Specific Models** – Tailor models to geographic clusters
- [ ] **Interaction Features** – Create polynomial or interaction terms
- [ ] **Domain Features** – Soil quality, irrigation status, etc.

### Data Improvements
- [ ] **Larger Dataset** – Incorporate more recent and comprehensive data
- [ ] **Missing Data Analysis** – Investigate if missing patterns are meaningful
- [ ] **Outlier Detection** – Identify and handle extreme observations
- [ ] **Data Quality Checks** – Validate data consistency and accuracy

### Deployment
- [ ] **Flask/Streamlit Web App** – Interactive UI for predictions
- [ ] **API Development** – RESTful API for model serving
- [ ] **Model Serialization** – Save trained models (pickle/joblib)
- [ ] **Docker Containerization** – Package app with dependencies

### Analysis Expansion
- [ ] **Feature Importance Analysis** – Detailed ranking for Random Forest
- [ ] **Residual Analysis** – Analyze prediction errors
- [ ] **Sensitivity Analysis** – Impact of feature changes on predictions
- [ ] **Seasonal Analysis** – Time-series patterns in yield data

---

## 📚 References & Resources

### Key Concepts
- **Regression Analysis:** Predicting continuous values
- **Ensemble Methods:** Combining multiple models for robustness
- **Feature Engineering:** Creating meaningful input features
- **Cross-validation:** Robust model evaluation techniques

### Libraries Used
- **pandas** – Data manipulation and analysis
- **NumPy** – Numerical computing
- **scikit-learn** – Machine learning algorithms
- **Matplotlib & Seaborn** – Data visualization

### Learning Resources
- [scikit-learn Documentation](https://scikit-learn.org/)
- [Pandas Documentation](https://pandas.pydata.org/)
- [Machine Learning Fundamentals](https://www.coursera.org/learn/machine-learning)

---

## 👨‍💻 Author

**Prashik Dev**

- GitHub: [@Prashikdev2315](https://github.com/Prashikdev2315)
- Repository: [Crop-Yield-Prediction-Using-Machine-Learning](https://github.com/Prashikdev2315/Crop-Yield-Prediction-Using-Machine-Learning)

---

## 📄 License

This project is provided as-is for educational and research purposes.

---

## 🙏 Acknowledgments

- Dataset sourced from agricultural databases
- Built as part of IIT Roper academic initiative
- Machine learning techniques from scikit-learn documentation

---

## 📧 Questions & Feedback

For questions, issues, or suggestions, please open an issue on GitHub or contact the author directly.

---

**Last Updated:** May 2026  
**Version:** 1.0
