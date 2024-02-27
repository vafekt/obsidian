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
3. Decision Trees
- The basic intuition behind a decision tree is to map out all possible decision paths in the form of a tree
- Decision trees are built by splitting the training set into distinct nodes
![[Pasted image 20240226210437.png]]
	- Internal node: a test
	- Branch: a result of the test
	- Leaf node assigns a patient to a class
- Steps
	- Choose an attribute from your dataset
	- Calculate the significance of attribute in splitting of data
	- Split the data based on the value of the best attribute
	- Go to step 1 and repeat
- First find which attribute is the best
	- Choose the highest node based on the label associated with it. Pick the highest rate = certainty
	![[Pasted image 20240226211627.png]]
	- The best feature is the one to decrease the impurity of patients in the leaves the best = more predictiveness = lower entropy
		- **The minimum value of zero corresponds to a node containing the elements of the same class**. In case this occurs, the node is called pure. **The maximum value of 0.5 corresponds to the highest impurity of a node**.
		![[Pasted image 20240226212142.png]]
		- A node is called pure if 100% falls into a specific category of the target field
		![[Pasted image 20240226212320.png]]
		- At each step, we minimize the impurity. Impurity of nodes is calculated by entropy of data in the node
- Entropy
	- First, understand entropy: (suppose that we have only 2 classes)
		- It gives the measure of impurity or randomness in the data. 
		![[Pasted image 20240226214827.png]]
		- It is given by: Entropy= — P(class 1) x Log(P(class 1)) — P(class 2) x Log(P(class 2))
	- The entropy will be high if we have impure or mixed class labels in a dataset. Class = Label
		- If there are two classes, class 1 and class 2, of equal numbers, i.e, the number of entries of class 1 is equal to the number of entries of class 2, and we randomly select an entry, it will belong to any class 1 or 2 with a 50% probability each. In such cases, the entropy will be high.
		- If a certain dataset has all data belonging to either class 1 or class 2, the entropy obtained is 0
	- 2 approaches
		- **Information Gain:** The information gain is the decrease in the entropy after the dataset is split on the basis of an attribute. Constructing a decision tree depends on finding the attribute that returns the highest information gain. It helps in choosing which feature or attribute will be used to create the deciding internal node at a particular point.
			- Information gain=Entropy(s) — [(Weighted average) x (Entropy of each feature)]
		- Gini impurity
- Steps
	![[Pasted image 20240226215751.png]]
	- Choosing the feature to be the root node. It is based on the amount of information gain
		![[Pasted image 20240226220006.png]]
		![[Pasted image 20240226220019.png]]
		![[Pasted image 20240226220036.png]]
		![[Pasted image 20240226220048.png]]
		- The one with the highest information gain is chosen. In this case, feature 1 is chosen.
	- Now, from feature 1, we need to set the branches that
		- But others have impurity so we need further splitting a attain greater purity
		- Or we can leave all options in a feature, and repeat the process of finding the best node with information gain
- Process with gini impurity. When a decision tree predicts numeric values, we have regression tree
	![[Pasted image 20240226224530.png]]
	- First, deciding whether Loves Popcorn, Loves Soda or Age should be the top of the tree
		- we have to test all features.
		- For Loves Popcorn: Gini Impurity = 1 - (Probability of Yes)^2 - (Probability of No)^2
			- In first branch, gini impurity = 0.375
			- In second branch, gini impurity = 0.444
			- Total gini impurity = (3+1)/(3+1+2+1) * 0.375 + (2+1)/(3+1+2+1) * 0.444 = 0.405
		![[Pasted image 20240226224832.png]]
		- For Loves Soda
			- Total gini impurity = 0.214
		![[Pasted image 20240226224946.png]]
		- For age, it is more difficult because we have numeric values
			- So, firstly, we need to sort the value from the lowest to the highest
			- Then we calculate the average age for all adjacent people
				![[Pasted image 20240226225632.png]]
			- Now we iteratively put all values as the condition. For example:
				![[Pasted image 20240226225738.png]]
				- Now compute total gini impurity = 0.429
			- We have values for others
				![[Pasted image 20240226225844.png]]
				- Choose the lowest 0.343. Because there are two candidates, pick either one. I pick 15.
		- Now Loves Soda = 0.214 (lowest), it is chosen to be the root. Now adding branches
			![[Pasted image 20240226230121.png]]
			- Choose between Popcorn and age
				- Popcorn now has impurity = 0.25 based on the new dataset. Age < 12.5 has impurity = 0 (the best), so don't need to check other ages
				![[Pasted image 20240226230319.png]]
				- So we choose ages to split node into leaves (left-hand). The right-hand already has the classification.
					![[Pasted image 20240226230454.png]]
			- Now, at the branch of age, there is also full classification. Loves Popcorn is deleted. The Gini Index or Impurity measures the probability for a random instance being misclassified when chosen randomly => The lower, the better
- Regression tree
	- The basic idea behind regression trees is to split our data into groups based on features, like in classification, and return a prediction that is the average across the data we have already seen.
	- Consider the housing data below, where we are using the ‘Age’ to predict the ‘Price’ of a house
	![[Pasted image 20240226232227.png]]
	![[Pasted image 20240226232337.png]]
	- The way the trees are built are similar to classification, but instead of using the entropy criterion. In Classification Trees, we choose features that increase the information gain. In Regression Trees, we choose features that minimize the error. (MAE, MSE)
	- Steps:
		![[Pasted image 20240226232616.png]]
		- the first step is to decide what the first decision is. We will do this by using the criterion and checking every single feature in the dataset to see which one produces the minimal error.
			- Now, take Near Water feature as an example:
			![[Pasted image 20240226232838.png]]
			![[Pasted image 20240226232829.png]]
				- MAE = Sum of all average errors / number
			- But what about the feature with a lot of values (not just Yes and No)? For example, Age feature
				- We do this by creating a boundary between each point, then we calculate the error
				- For example, first we create the boundary between the first two data points, which are (0, 260831.34) and (5, 347982.98), so we create a boundary of x = 2.5 (The midpoint between the x component of the first two data points). We now find the average price of the houses on the left and right sides of this boundary and use it to calculate the MAE.
				![[Pasted image 20240226234518.png]]
				![[Pasted image 20240226234605.png]]
				- Now repeat the process for each pair of consecutive points. Choose the lowest MAE for the boundary point
			- Since the whole MAE of Age is smaller than Near Water, Age is chosen. 
				![[Pasted image 20240226234838.png]]
				- With the regression tree above, we have two options, we can either stop here and use the average value of the ‘Yes’ (left) and ‘No’ (right) to predict the house prices, or we can continue to add more decisions to either branch. There are a few conditions that are commonly used to stop growing regression trees:
					- Tree depth
					- Number of remaining samples on a branch
					- Number of samples on each branch if another decision is made
				- If we want to have more depth in age, the next node need to compare with Near Water again
					![[Pasted image 20240226235049.png]]
4. Logistic regression
- It is classification algorithm for categorical variables
![[Pasted image 20240227151847.png]]
- Even though having the name Regression, it cannot be used for predicting continuous values (price of the house). But it is used for predicting binary label (Yes-No). But the independent variables can be continuous or categorical
- Application
	- Predicting the probability of a person having a heart attack
	- Predicting the likelihood of a customer to purchase a product
- When is logistic regression suitable?
	- If your data is binary
		- 0/1
	- If you need probabilistic results, the logistic regression returns the probability between 0 and 1.
	- When our data is linearly separated. So line, plane or hyperplane can be applied.
	![[Pasted image 20240227153717.png]]
- Logistic regression vs linear regression. Linear regression is actually usable even in the case of logistic regression, but not ideal.
	- If we use linear regression for classification, we have to set the threshold for deciding whether result is 0 or 1. But if we have a big value, the line is shifted very much (from 0.5 to 0.8 easily). So sigmoid function is better (logistic regression)
	![[Pasted image 20240227160442.png]]
	- Sigmoid solves the problem with very big or very small values
	![[Pasted image 20240227160558.png]]
	![[Pasted image 20240227160706.png]]
- The training process
	![[Pasted image 20240227160851.png]]
	- Initialize theta
	- Calculate predicted y
	- Compare with the actual output (True or False)
	- Calculate the error for all input. The lower the cost is, the better the model is. Change the theta to reduce the cost, then calculate predicted y again (Back propagation with gradient descent)
- General cost function
	- Theta is also called weight. We need to change the weight so that the cost is reduced
	![[Pasted image 20240227162738.png]]
	- It is then converted into:
	![[Pasted image 20240227162853.png]]
	- We use gradient descent to minimize the cost
	![[Pasted image 20240227163135.png]]
	- Gradient is the derivative of cost function
5. Support vector machine
- SVM is a supervised algorithm that classifies cases by finding a separator
	- First, it maps data to a high-dimensional feature space
	- Finding a separator (hyperplane). Even though the values of dataset are not linearly separated
	![[Pasted image 20240227165246.png]]
- Data transformation
	![[Pasted image 20240227165426.png]]
	- The way we map data into a higher-dimensional space is called kernelling
		- Linear / Polynomial / RBF / Sigmoid
		- Converting nonlinear separability into linear separability
- How to find the best hyperplane to separate the data
	- Choose the hyperplane with the biggest margin as much as possible
	![[Pasted image 20240227170112.png]]
	- Gradient descent can be applied to find the best line
- Application
	- Image recognition
	- Detecting spam
- 