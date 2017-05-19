# House Price Prediction

캐글 데이터를 이용한 주택 매매 가격 예측
캐글 링크:[house-prices-advanced-regression-techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)

이 프로젝트의 목적은 주택의 골목 여부, 주택 마감재 종류, 주택 매매시점과 같은 주택 속성에 관련된 데이터를 이용하여 2006-2010 동안 매매가 이루어진 미국 Iowa의 Ames지역 주택 매매 가격을 예측하는 것이다.
데이터는 총 79개의 feature와 1개의 target value, 즉 매매가격으로 이루어져 있다. 79개의 데이터에는 주택을 구성하는 각종 요소, 면적, 마감재, 주택이 지어지거나 리모델링된 시점, 매매시점 등에 대한 다양한 정보가 있다.

이 데이터는 missing value가 많은 데이터로, 이에 대한 처리가 중요하다. 또한, 다수의 데이터가 categorical 변수인 것도 특징이다.
ordinal value의 경우, 각 feature 내의 항목이 각각 dummy 변수로 다루어지면, 각 항목은 완전 별개의 항목으로 다뤄지기 때문에, 서로의 정보를 이용하기 어렵다. 따라서, numeric value로 바꾸는 방법을 채택하였다.
또한 bin의 수가 지나치게 많은 몇몇 항목의 경우, 비슷한 항목끼리 묶어 bin의 개수를 축소하여, 노이즈를 줄이고자 하였다.

본 데이터는 target이 numeric value이기 때문에 regression문제다. 가장 먼저 적용한 모델은  linear regression인데, linear regression 을 쓰기 위해서는 변수가 normal distribution을 따라야 하며, 독립 변수간 correlation이 존재하지 않아야 한다. (multi collinearity 문제) 따라서 이에 대한 검증 과정을 explore 부분에 함께 담았다. 간단히 요약하면, skewness를 보인 sale price는 log를 통해 normal distribution에 가깝게 변환하였고, 독립변수들의 경우 상관관계를 보이는 경우가 다수 있어, linear regression을 이용한 예측에 한계가 있을 것임을 파악하였다.

따라서, 단순 linear regression이외에 non linearity를 설명할 수 있도록, polynomial feature를 통해 상호작용을 설명할 수 있도록 하였고, 한편으로는 non parametric 모델과의 앙상블을 통한 보완이 필요함을 판단하였다.
linear regression의 경우 backward stepwise feature selection 이후에 polynomial term을 추가하여 복잡도를 높이고, 다시 ridge 및 lasso를 통해 복잡도를 완화하는 기법을 사용하였다.
non parametric 모델의 경우 gradient boosting machine을 사용하였다. 앙상블 모형을 보다  robust하게 만들기 위해, sci kit과 xgboost의 모형을 모두 사용하였다.

일련의 과정에서 검증은 cross validation을 사용하였다. 데이터가 크기가 1400건 정도로 아주 많지는 않기 때문에, 보다 안정적으로 예측력을 검증하기 위함이다.




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
modeling_para.ipynb    
modeling_nonpara_ensemble.ipynb

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
