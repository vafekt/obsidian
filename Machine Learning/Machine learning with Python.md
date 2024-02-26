1. Machine learning algorithms
- Regression to predict the trend in the future for continuous values
	- Simple linear regression
	- Multiple linear regression
	- Regression trees
- Classification for predicting the item class/category of a case
	- Logistic regression
	- KNN
	- SVM
	- Multiclass prediction
	- Decision trees
- Clustering to segment data set into groups with similar characteristics
	- K-means
2. Applications
- Use ML to make predictions (benign or malignant)
- Using different Python libraries such as numpy, scikit-learn
- For example, doctor sees the X-ray image of a cell and want to find out if this is a benign or malignant cell? Based on the attributes
![[Pasted image 20240224121807.png]]
3. What is the machine learning
- Machine learning is a subfield of computer science that gives computers the ability to learn without being explicitly programmed.
![[Pasted image 20240224123524.png]]
4. What about Python libraries
![[Pasted image 20240224124050.png]]
5. Supervised vs unsupervised
- Supervised model
	- We need to teach the model first, but how?
		- By training it with some data from labeled dataset
		![[Pasted image 20240224125214.png]]
	- 2 types of supervised learning technique
		- Classification
		- Regression
- Unsupervised learning
	- We do not teach the model, without labeled data
	- It is header than supervised learning, so we need more difficult algorithm and techniques
		- Dimension reduction: Removing redundant features to make the classification easier
		- Density estimation: to find structure within the data
		- Marker basket analysis: if you buy a group of items, you are likely to buy another group of items
		- Clustering: the most popular technique. To find the similar structure, anomaly detection
6. Linear Regression
- Process of predicting a continuous value
	- 1 dependent variable (Y): that is the value we need to predict (target)
	- 1 or more independent variables (X): the value we have (costs of state)
	![[Pasted image 20240224154951.png]]
- Types of regression model
	- Simple regression: One independent variable is used to estimate a dependent variable (linear function or non-linear fucntion, but only one variable)
		- Simple linear regression
		- Simple non-linear regression
	- Multiple regression: More than one independent variables to estimate 1 dependent variable
		- Multiple linear regression
		- Multiple non-linear regression
- Applications of regression
	- Sale forecasting
	- Satisfaction analysis
	- Price estimation
- Algorithms
	- Ordinal regression
	- Poisson regression
	- Fast forest quantile regression
	- Linear, Polynomial, Lasso, Stepwise, Ridge regression
	- Bayesian linear regression
	- Neural network regression
	- Decision forest regression
	- Boosted decision tree regression
	- KNN (K-nearest neighbors)
- Simple linear regression
	- Problem we have: Predict the CO2 emissions. The dependent variable must be continuous, but the independent variables can be categorical or continuous
	![[Pasted image 20240224160113.png]]
	![[Pasted image 20240224160218.png]]
- For the case of simple linear regression, we only take the engine size as variable x. Now we have to find the best intercept and slope (gradient) - theta 0 and theta 1.
![[Pasted image 20240224160425.png]]
- How to find the best fit?
	- Predict the response variable based on the line, then compute the residual error (predicted value and actual value y). We can use MSE.
	![[Pasted image 20240224160810.png]]
	- But we still do not estimate the value theta? This is the formula
	![[Pasted image 20240224161011.png]]
	- First, we have to predict the estimated x and y. Usually the average. Then theta 1 is computed. Then we find the line y = 125.74 + 39x
- Pros
	- Fast
	- No parameter tuning
- But we usually don't use the whole data set for training, but dividing into several parts
![[Pasted image 20240224162222.png]]
	- Finally we compute the error between the actual values and predicted values
	![[Pasted image 20240224162356.png]]
- Training & out-of-sample accuracy
	- Training accuracy
		- High training accuracy is not necessarily a good thing
		- Can be a result of over-fitting, and produce a non-generalized model
	- Out-of-sample accuracy
		- Should be high. But how can we improve. Using train/test split
		![[Pasted image 20240224162804.png]]
- K-fold cross-validation
![[Pasted image 20240224163103.png]]
![[Pasted image 20240224163129.png]]
- Evaluation metrics in regression models
	- Compare actual values and predicted values (error)
		- MAE
		- MSE
		- RMSE
		![[Pasted image 20240224172115.png]]
- Multiple linear regression
	![[Pasted image 20240225095431.png]]
	- So now we have to find a lot of theta, defined by a matrix.
		![[Pasted image 20240225095529.png]]
	- In multiple linear regression we want to estimate theta so that we can achieve the minimum of MSE.
		![[Pasted image 20240225101643.png]]
		- Using ordinary least squares with linear algebra operations to find the best value. But it takes a long time for large datasets
		- An optimization algorithm
			- Gradient Descent
	- After having theta, we draw the graph and compute the error
	- When to use the multiple linear regression against the simple
		- When there are a lot of independent variables
		- But we need to check the linear relationships between dependent and independent variables, we need to switch to non-linear regression
			- Checking by scattering plot
2. K-Nearest Neighbors
- Belongs to the classification approach (supervised learning). It determines the class label for an unlabeled test case
	- If we have a lot of features, and multiple labels for classifying, it will be called multi-class classification.
	![[Pasted image 20240226185905.png]]
	- Algorithms
		- Decision Trees
		- Naïve Bayes
		- Linear Discriminant Analysis
		- K-Nearest Neighbor
		- Logistic Regression
		- Neural networks
		- SVM
	![[Pasted image 20240226190429.png]]
- Intuition behind K-Nearest Neighbors algorithm
	- We want to specify which label is the category at row 8. So we suppose that this category depends on several nearest neighbor categories (5, in this case). Then we choose the label based on the majority of one label (3) to assign to row 8.
	- Takes a bunch of labeled points and uses them to learn how to label other points
		- based on similarity
- How to calculate the similarity
	- Euclidean distance
	![[Pasted image 20240226190913.png]]
	- Example of calculating distance in 1-dimensional space
	![[Pasted image 20240226191025.png]]
	- In 2-dimensional space
	![[Pasted image 20240226191428.png]]
- How to choose the best value of K
	- Small value of K can lead to over-fitting
	- Very large number can lead to over-generalized
- Can be used for regression
	- For example, assume that you are predicting the price of a home based on its feature set, such as number of rooms, square footage, the year it was built, and so on. You can easily find the three nearest neighbor houses of course not only based on distance but also based on all the attributes and then predict the price of the house as the medium of neighbors.
- Evaluation metrics in classification
	- Several methods
		- Jaccard index
		- F1-score
		- Log loss
	- Jaccard index
	![[Pasted image 20240226192109.png]]
	- F1-score (based on the confusion matrix )
	![[Pasted image 20240226193451.png]]
	![[Pasted image 20240226193809.png]]
		- Now we have to calculate the precision and recall of each label
			- Precision: A measure of accuracy, provided that a class label has been predicted
				- precision = TP / (TP + FP)
			- Recall is the true positive rate
				- recall = TP / (TP + FN)
			- F1-score = 2*(Precision * Recall) / (Precision + Recall)
				- Express the average accuracy
	- Log loss
		- When the output is not a label, but it is the probability of the category
		![[Pasted image 20240226194410.png]]
		![[Pasted image 20240226194518.png]]
		- We can calculate the log loss for each row using the log loss equation, which measures how far each prediction is, from the actual label.
		- Then we calculate the average log loss across all rows of the test set. The ideal classifier has small value of log loss.
		![[Pasted image 20240226194718.png]]
		- 
