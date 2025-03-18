# Introduction
In this repository I will use my skills for a Binary Classification problem.
The data I will work with is a survey from American Airlines, it consist of 21 features (129880 rows) like: age, gender, score from 0-5 for a food on plane, delay, etc. and a review (dissatisfied or satisfied), the review is gonna be what I will try to predict.
To address this problem I will try to use two models: SVM and Random Forest. Before applying them I will do exploration, data pre-processing, cleaning, apply log transformation and remove outliers.
I will also do a model tuning in the process and compare the result in the end.

## Link to a data
https://www.kaggle.com/datasets/johndddddd/customer-satisfaction

## Metrics

To evaluate result for both of the models I will use:
- Precision. Out of all the instances predicted as positive, how many are actually positive? Important when false positives are costly.
- Recall. Out of all the instances that are actually positive, how many did the model correctly predict as positive? Important when missing a positive instance is costly.
- F1-Score. Combining both Precision and Recall to balance the score.
- Macro Average. Calculating the metric independently for each class and then taking the average can help identify poor performance on minority class If data is imbalanced.
- Weighted Average. Calculates the metric independently for each class and then takes the average weighted by the class’s support. Helps to reflect how the model performs across the dataset in proportion to class frequencies.

## Methodology
- Started loading the dataset, looking for and removing missing values.
- Did data exploration, built plots.
- Learned that Flight Distance was heavily right skewed and contained outliers which is not very important for Random Forest model but can heavily impact SVM.
- Applied log transformation to fix skewness and remove outliers, because SVM are quite sensitive to it.
- Encoded the categorical values.
- Standardized Data.
- Created Test/Train splits.
- Created Models.
- Run a few experiments, perform tuning, select different kernels for SVM.
- Performed Feature Selection for Random Forest, found optimal features for the model.
- Compared the results.

## SVM
Support Vector Machines (SVM) are supervised learning algorithms which are used for both classification and regression tasks. SVMs work by finding the optimal hyperplane that best separates the classes in the feature space. For binary classification, this means determining a decision boundary that maximizes the margin—the distance between the hyperplane and the nearest data points from either class.
- In my case SVM uses kernel functions (e.g., RBF, polynomial) to transform the data into a higher-dimensional space where a linear separator can be found. This transformation allows SVM to capture complex patterns without explicitly computing the high-dimensional coordinates.
- The advantage of SVM is that it is highly effective in High Dimensions and the use of kernel functions provides flexibility to model non-linear relationships without significant computational overhead. It is also robust to overfitting when the number of features are large.

## Random Forest
Random Forest is an ensemble learning method that combines multiple decision trees to produce a robust and accurate predictive model. It works by constructing a multitude of decision trees during training and outputting the mode of the classes. This ensemble method reduces variance and improves overall model performance.
- Each tree in the forest is trained on a random subset of the data (with replacement), which is known as bootstrapping. This technique ensures diversity among the trees and helps the model generalize better.
- For classification tasks, the final class prediction is made by majority voting, where each tree casts a vote and the class with the most votes is chosen as the output. For regression, the average of all trees’ outputs is used.
- Advantages of this model that its robustness to overfitting, handling well high-dimensional data and it is not very sensitive to outliers or unbalanced dataset

## Result
Both models are a powerful choice for a binary classification task thats why results were quite similar to each other and we can say both models performed well on this dataset. SVM scored the best with RBF kernel, approximately 0.95 on F1, while Random Forest Model scored the best with feature selection (taking out the last 3 features) and the score was around 0.96. Random Forest performed better slightly better on this dataset. 

