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
- 