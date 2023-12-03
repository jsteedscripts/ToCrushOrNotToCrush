# ToSendOrNotToSend {WIP}
## Project Overview
This project uses different machine learning methods to attempt to predict a rock climber's skill level and maximum grade. The data used to build the models is the [8a.nu dataset](https://www.kaggle.com/datasets/jordizar/climb-dataset) from Kaggle.

## Dataset
Upon inspection of the 8a.nu dataset from Kaggle, it is obvious that most of the data recorded are from professional climbers. This poses issues for maching learning algorithms due to the lack of variance.

The density plot below shows the distributions for each feature. With the exception of grades_count, the feature values are mostly centered about the mean and have little variation. Additionally, the values of grades_max, grades_mean and grades_first are quite similar to one another. This reinforces the suspicion that this data is from professional climbers, because a pro climber's first grade will likely be near their maximum and mean grade due to the high level of skill they are climbing at.

![Density Plot](plots/density_plot.png)

The plot below shows the correlation matrix heatmap for the features. The most heavily correlation features are grades_max vs. grades_mean, grades_max vs. grades_first, grades_first vs grades_mean, height vs weight, and age vs years_climbing.

![Correlation Matrix Heatmap](plots/correlation_matrix_heatmap.png)

## Machine Learning Models
Two different machine learning tasks are defined: classification and regression. The classification task aims to predict the climber's skill level (defined using grades_mean). The regression task aims to predict the climber's grades_max. 

Skill Level Bins:
* Intermediate: grades_mean <= 6b/c (5.12a)
* Advanced: 6b/c (5.12a) < grades_mean <= 7c (5.13c)
* Expert: grades_mean > 7c (5.13c)

### Classification
K-Nearest Neighbors is used for the classification task. Tuning of the feature set (sex, height, weight, age, number of years climbing, number of routes completed, first grade, and maximum grade) and the number of neighbors was also completed.

Feature Set Tuning (vary inclusion of first and max grade due to high correlation with mean grade):
* Both: Sex, height, weight, age, number of years climbing, number of routes completed, first grade, maximum grade
* First: Sex, height, weight, age, number of years climbing, number of routes completed, first grade
* Max: Sex, height, weight, age, number of years climbing, number of routes completed, maximum grade
* Neither: Sex, height, weight, age, number of years climbing, number of routes completed

### Regression
Linear and random forest regressors were trained on features in both independent models and cohesive models (using all features at once) to predict grades_max from sex, height, weight, age, number of years climbing, number of routes completed, first grade, and mean grade. The max_depth random forest hyperparameter was tuned.

## Results

### Classification
The following figure shows the results of the KNN feature set and K hyperparameter tuning.

![KNN Tuning](plots/knn_feature_tuning.png)

As expected, the feature set including both first and maximum grade achieved the highest accuracy. The feature set only including maximum grade did slightly better than the set only including first grade. The set excluding first and maximum grade still achieved reasonably high performance.

### Regression
#### Linear Regression
#### Random Forest Regression
