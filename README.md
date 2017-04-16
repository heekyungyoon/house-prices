# House Price Prediction
![](mix4_ranking.png?raw=true)
캐글 데이터를 이용한 주택 매매 가격 예측
캐글 링크:[house-prices-advanced-regression-techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)

# EXPLORE
관련 코드: explore_data.ipynb
- handling missing values
- handling categorical values with order
- analyzing correlation between target and features
- analyzing correlation between features
- handling outliers
- other patterns

# PREPROCESS
관련 코드: preprocess.ipynb
- Special Treatments
  - delete constant feature: Utility
  - handling categorical features with order
  - binning MSSubClass, Neighbor
- Missing Values
- Outliers
- Handling Categorical Values (Get Dummies)
- Scale

# MODELING
관련코드:
  - modeling_para.ipynb
  - modeling_nonpara_ensemble.ipynb

- Parametric models
    - linear regression
    - linear regression w/ feature selection
    - linear regression w/ interaction
    - linear regression w/ Ridge, Lasso
- Non parametric models
    - Gradient boosting regressor (Sci-kit)
    - Xgboost
- Ensemble(final model)
    - Ridge, Lasso, GBregressor and Xgboost
