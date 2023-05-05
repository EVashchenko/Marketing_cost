# Marketing_cost
Submission for the Kaggle competition 'Regression with a Tabular Media Campaign Cost Dataset' (https://www.kaggle.com/competitions/playground-series-s3e11/overview/description)

### Summary:
This is a Jupyter notebook containing my submission for the Kaggle playground competition 'Regression with a Tabular Media Campaign Cost Dataset' (https://www.kaggle.com/competitions/playground-series-s3e11/overview/description). The submission ranked in the top 14% (127th of 952 teams). The contents of the notebook include exploratory data analysis, comparison of multiple models using default parameters, feature selection for the primary models - CatBoost and XGBoost, and  ensembling of the primary models. As a result of these efforts, it was found that the XGBoost model performed the best.

### About the task:
The task is to develop a model that can predict the marketing campaign cost for a chain of convenience stores in the United States. The provided dataset includes store features that describe the customers, the range of products offered, and the physical characteristics of the store. The model needs to forecast the cost of acquiring a customer (in dollars).

The competition's train and test datasets are synthetically generated from the original dataset, which can also be used for training the models. The metric used to evaluate the results is the Root Mean Squared Log Error.

The notebook is divided into five parts: exploratory data analysis, training of baseline models, tuning of target model parameters and feature selection, ensemble of target models, and submission.

Features description:
* store_sales(in millions) - store_sales(in million dollars)
* unit_sales(in millions) - unit_sales(in millions) in stores quantity
* Total_children - total children in home
avg_cars_at home(approx) - avg_cars_at home(approx)
* Num_children_at_home - num_children_at_home as per customers filled details
* Gross_weight - gross_weight of item
* Recyclable_package - food item is recyclable_package
* Low_fat - low_fat food item is low fat
* Units_per_case - units/case units available in each store shelves
* Store_sqft - store area available in sqft
* Coffee_bar - coffee bar available in store
* Video_store - video store/gaming store available
* Salad_bar - salad bar available in store
* Prepared_food - food prepared available in store
* Florist - flower shelves available in store
* Cost - cost on acquiring a customers in dollars

### Notebook summary:
* EDA: The dataset consists of 15 features, all of which are described. 13 are categorical, and among them, 7 are Boolean. The Boolean features are highly correlated, which indicates the need for feature selection. Since the target value has 328 values for 360,000 cases (rows in the train dataset), it is debatable whether it is a regression or multiclassification problem. However, I treated it as a regression problem. There are no null values in any of the datasets, and there are no duplicates in the train and test datasets. The original dataset had duplicates that were removed.
* As the majority of features are categorical, it is suggested to start with RandomForest, CatBoost, and XGBoost. From the analysis of models with default parameters, CatBoost and XGBoost are the models to proceed with.
* The CatBoost and XGBoost parameters are tuned using the Optuna package, and a set of features is selected for each model based on feature importance (the gain of each feature in the loss function).
* The ensemble of CatBoost and XGBoost models is tested with selected weights.
* The submission file is generated.
