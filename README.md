# ToCrushOrNotToCrush
## Project Overview
This project uses different machine learning methods to attempt to predict a rock climber's skill level and maximum grade. The data used to build the models is the [8a.nu dataset](https://www.kaggle.com/datasets/jordizar/climb-dataset) from Kaggle.

## Dataset
Upon inspection of the 8a.nu dataset from Kaggle, it is obvious that most of the data recorded are from professional climbers. This poses issues for maching learning algorithms due to the lack of variance. 

![Density Plot](plots/density_plot.png)

## Machine Learning Models
Two different machine learning tasks are defined: classification and regression. The classification task aims to predict the climber's skill level (defined using grades_mean). The regression task aims to predcit the climber's grades_max. 

### Classification
K-Nearest Neighbors is used for the classification task. Tuning of the feature set and number of neighbors was done.

### Regression
Linear and random forest regressors were trained on features in both independent models and cohesive models (using all features at once).
