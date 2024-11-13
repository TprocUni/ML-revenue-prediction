# ML-revenue-prediction
Predicting Fortune 500 Revenue with Machine Learning

This analysis focuses on identifying factors that correlate with the revenue of **Fortune 500** companies, utilizing a dataset from 2017. The primary objective is to determine which features, such as industry, sector, or location, are most predictive of revenue. To achieve this, the study employs **machine learning** methodologies: K-means clustering for grouping similar companies, polynomial regression for exploring correlations, and neural networks for predictive modeling.

#### 1. Data Preprocessing

The dataset includes various attributes of Fortune 500 companies, like "Sector," "Industry," "Location," and "Revenue." Before analysis, the data undergoes preprocessing steps:

- **Cleaning**: Missing values ("NaN") are addressed by either removing affected rows or substituting surrogate values, though the latter may complicate model performance.
- **Normalization**: Converting qualitative data (e.g., industry names) into numerical form and removing redundant columns, such as "CEO" and "HQ Address," ensures consistency and relevance.
- **Outlier Removal**: Outliers are filtered out as they may distort model accuracy, though certain outliers can represent genuine variations in the data.

After preprocessing, the data is split into training and testing sets, enabling model evaluation through cross-validation.

#### 2. Clustering - K-means

The **K-means algorithm** groups companies into clusters based on similarities in features. It is an unsupervised technique that optimizes the within-cluster sum of squares, centering each cluster around a centroid.

- **Initialization**: The K-means++ method is used for faster, more accurate clustering.
- **Determining K**: Techniques like the **Elbow method** and **Silhouette method** help identify the optimal number of clusters. However, adjusting for revenue scales (e.g., by applying a scalar factor) is crucial, as unscaled data leads to elongated clusters that fail to capture true relationships.
- **Results**: Clustering reveals that revenue has a strong association with certain sectors (e.g., retailing), aligning with real-world trends. Yet, location-based clustering (e.g., HQ city/state) lacks clear patterns, suggesting that sector is a stronger revenue predictor than geographic location.

#### 3. Regression - Polynomial Regression

**Polynomial regression** models the relationship between revenue and other attributes by fitting a polynomial equation to the data points.

- **Evaluation Metric**: **R-squared error** is calculated to assess model accuracy. This error metric indicates the proportion of variance in revenue explained by other features.
- **Hyperparameter Tuning**: The model tests various polynomial depths to avoid overfitting while maintaining predictive power.
- **Challenges**: Polynomial regression shows limited success due to the complexity of real-world revenue drivers. While some variables show moderate correlations, high R-squared values often lead to overfitting, yielding unrealistic results that do not generalize well. 

#### 4. Classification - Neural Network

A **neural network** (NN) with one input layer, two hidden layers, and one output layer is applied to classify companies based on revenue predictions.

- **Configuration**: The network optimizes hyperparameters like layer size, activation functions, and the number of epochs. After removing outliers and normalizing values, the model undergoes iterative training.
- **Activation Functions**: Various combinations (e.g., "elu," "relu") are tested, with the best performance achieved by specific configurations.
- **Results**: Neural networks outperform other methods, achieving low error margins. However, the model’s accuracy could be further improved with a larger dataset and by refining the input features.

#### 5. Results and Findings

Each method provides insights into the factors that influence company revenue:

- **K-means Clustering**: Confirms that certain industries and sectors correlate with high revenue, such as retailing and technology. However, location-based clustering shows weaker correlations.
- **Polynomial Regression**: Fails to capture a strong predictive relationship, highlighting the challenge of using a single-variable relationship to predict revenue.
- **Neural Networks**: Perform well with a complex data structure, indicating that a multivariable approach is effective for predicting revenue.

#### 6. Discussion

The results underscore the complexity of predicting revenue using limited attributes. While neural networks provide the most accurate predictions, clustering reveals broader insights into sector-based revenue trends. The analysis suggests that companies in specific sectors tend to have higher revenue, which could inform strategic decisions for smaller companies looking to position themselves within lucrative markets.

#### Summary

This study investigates data correlations with Fortune 500 revenue using clustering, regression, and neural network models. K-means clustering identifies sector-related patterns, while polynomial regression reveals limited predictive power. Neural networks, despite high computational demands, show promise in accurately predicting revenue. Further research could enhance model robustness by incorporating more data and exploring additional revenue-influencing factors.


