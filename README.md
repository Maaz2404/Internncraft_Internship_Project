# House Price Prediction: Project Report

## 1. Data Exploration

### Data Overview:
The dataset comprises house listings with key attributes such as number of bedrooms, bathrooms, area in marlas, and various categorical attributes like property type, city, and agency.

### Key Insights from Data Visualizations:
The initial exploration involved visualizing the distribution of house prices, showing a heavy-tailed distribution with many outliers (extremely high-priced houses). Most houses fall in the mid-to-lower price range, while certain areas like Karachi show consistently higher prices.

### Visualizations Included:
- Price distribution (histogram)
- Categorical distribution of city, property type, etc., as pie charts
- Scatter plots showing relationships between area, bedrooms, and price

## 2. Feature Engineering Techniques

### Created Features:
- **Capping Outlier Prices:** Capped prices values above the 95th percentile to greatly improve the performance of the models.
- **Rooms per Marla Ratio:** A derived feature representing the ratio of rooms to the area, helping capture house compactness.
- **Uniform Area Size Metric:** Combined ‘Marla’ and ‘Kanal’ columns to make a uniform metric.

These features aim to enhance the model’s ability to predict price by providing more detailed metrics related to house space.

## 3. Outlier Analysis

### Identification of Outliers:
Outliers were identified in the price column using the interquartile range (IQR) method, with thresholds set at the 5th and 95th percentiles. These were filtered to separate houses with extreme prices into a new outlier dataset.

### Outlier vs Non-Outlier Comparison:
A comparison between the two subsets was made using pie charts, demonstrating differences in categorical features like city and property_type. For instance, high-priced outliers were more likely to be found in luxury cities, have agencies, and specific property types.

### Pie Chart Comparison:
- Pie charts comparing the share of values in different categories for outliers vs. non-outliers.

## 4. Model Selection and Evaluation

### XGBoost Model:
A XGBoost Regressor model was selected for predicting house prices. A pipeline was constructed to preprocess numerical and categorical features, standardize numerical features, and apply one-hot encoding for categorical variables.

### Hyperparameter Tuning:
Used iterative trial and error to optimize the XGBoost model parameters, focusing on max depth and the number of estimators.

### Best RMSE Values:
- **Training RMSE:** 5,599,300.57
- **Validation RMSE:** 6,109,551.70

These values indicate reasonable predictive performance, though improvements could be made.

## 5. Future Price Prediction Examples

```python
user_input = {
    'bedrooms': 3,
    'baths': 2,
    'Area(Marlas)': 10,
    'rooms_per_marla': 0.3,  
    'total_rooms': 5,
    'property_type': 'House',
    'city': 'Lahore',
    'purpose': 'For Sale',
    'agency': 'Has agent'
}
```

### Predicted House Price: 16,575,392.00 PKR

## 6. Recommendations for Further Analysis

### More Features:
Adding more features to the dataset could improve model performance, such as:

- **Property Age:** Older houses may have lower values or require more repairs.
- **Proximity to Amenities:** Distance to schools, parks, and public transport could influence prices.
- **Economic Factors:** Incorporating local economic indicators like interest rates and inflation would add valuable predictive power.

### Data Collection:
- **Expand the Time Range:** Collecting a larger dataset covering multiple years could reveal trends over time.
- **Focus on Specific Regions:** Focusing on certain high-demand areas like Karachi or Lahore could yield more detailed insights into price determinants for those regions.

---
