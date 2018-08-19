# Fundamentals of Machine Learning

Basic concepts and important nemonclature of machine learning categories

## Definition

Machine learning is the science that uses statistical techniques to allow computers to learn from data, without being explicitly programmed. It is great for

- Simpliying problems for which existing solutions require a lot of hand-tuning or long lon ists of rules
- Complex problems for traditional approaches or have no known algorithm
- Fluctuating environments where adaptation to new data is required
- Getting insights about complex problems and large data sets

## Categories

**Supervision**

- Supervised
	- Building a statistical model for predicting or estimating an output based on one or more inputs; the *training data* includes the *labels*
	- Based on the type of *label*, can be further divided into *regression* or *classification* (see **Data type**)
	- Common algorithms include regression, k-nearest neighbors, support vector machines (SVM), decisions trees and random forests
	- E.g. predict if a patient will develop adverse reactions to a treatment

- Unsupervised
	- Inputs are used to discover relationships and structure from the data, but no supervising output exists; the *training data* is not labeled   
	- Common algorithms include 
		- Clustering: to identify similarities and differences (*anomaly detection*) within the subgroups of the input data. E.g. k-means, hierarchical cluster analysis (HCA), expectation maximization 
		- Dimention reduction: to simplify the data without losing too much information by *feature extraction*. E.g. principal component analysis (PCA), kernal PCA, t-distributed stochastic neighbor embedding (t-SNE), locally-linear embedding (LLE)
		- Association rule learning: to identify relations between attributes from large data sets. E.g. apriori, eclat
	- E.g. identify groups of customers that buy similar clothes
	- E.g. find groups of gene expression patterns

- Semi-supervised
	- Only part of the output exist for the input data
	- E.g. photo-hosting services can automatically tag pictures once the first couple of pictures are labeled with names

- Reinforcement learning
	- The learning system (*agent*) observes the environment, select and perform actions, and get *rewards* or *penalties* based on the actions. It then derives the best strategy (*policy*) to get the most reward over time
	- E.g. AlphaGo analyzed millions of games and played many games against itself to derive a policy 

**Data type**

- Regression
	- Predicting a continuous or quantitative output value
	- Techniqes include least squre linear regression
	- E.g. wage, housing prices
- Classification
	- Predicting a non-numerical value
	- Techniques include logistic regression
	- E.g. gender, diagnosis (disases or not)
- Notes
	- K-nearest neighbors and boosting can be used in both cases
	- The response type (quantitative of qualitative) is important for determining the model, but the predictors are less important and should be coded prior to fitting a model

**Learning process**

- Batch learning (offline learning)
	- The system must be trained with all available data and cannot learn incrementally. Once new data exists, the system has to be trained from scratch with the full data set
	- Requires a lot of computing resources 
	
- Online learning (out-of-core learning)
	- The system can be trained incremetally by feeding data sequentially or with small groups of data (*mini-batches*)
	- The *learning rate* determines the speed of the system to adapt to changing data. However, a system with a high learning rate also tend to quickly forget the old data
	- If bad data is fed to the system, performance can gradually decline

**Data generalization**

- Instance-based learning
	- The system learns examples by heart, then generalizes to new cases using a similarity measure
	- E.g. Spam filter flag emails that are very similar to known spam emails

- Model-based learning
	- The system builds a model of all the labeled data, and uses the model to make predictions
	- E.g. Building a linear regression model to predict housing prices 


## Model evaluation

**Training and test set**

- Split the data into training set (80%) and test set (20%); only use the train set to train the model
- Calculate *out-of-sample error* with the testing data; a low *training error* but high *testing error* indicates *overfitting* the training data

**Validation set**

- Acts as a second holdout set to allow comparison of multiple trained models with various hyperparameters using the training set. The model that performs best on the validation set can then be selected, and a single final *out-of-sample error* can be calculated using the test set
- *Cross validation* allows splitting the training set into complementary subsets, in which differenct combinations can be used to train models, while the remaining can be used for validation. This again allows comparison of different models without wasting too much training data in validation sets

**No free lunch theorem**

Introdcued by David Wolperts in 1996. There is no model that is *a priori* better than the rest. To know what model is better, assumptions of the data must first be made to select a couple of models in order to identify the one(s) that works the best. 

## Common problems

**Data quality and quantity**

- Insufficient quality of training data
- Nonrepresentative training data: sampling bias
- Poor-quality data: garbage in, garbage out
- Irrelevant features: *feature engineering* helps select relevant features from the training data to train the algorithms
	- *Feature selection*
	- *Feature extraction* to combine existing features to produce a more useful one
	- Creating new features by gathering new data

**Overfitting**

- The model overgeneralizes and thus performs well on the training data, but does not predict well on new data
- Happens when the model is too complex relative to the amount and noisiness of the training data
- Solutions include
	- Simplify the model by selecting fewer parameters
	- Reducing the number of attributes in the training data
	- *Regularization*: constraining the model with a *hyperparameter* to control the amount of regularization applied during learning


**Underfitting**

- The model is too simple to learn the underlying structure of the data
- Solutions include
	- Selecting a more complex mdoel with more parameters
	- *Feature engineering*: selecting better features to the learning algorithm
	- Reducing the regularization hyperparameter: reducing the constraints on the model

## References
1. [An Introduction to Statistical Learning](http://www-bcf.usc.edu/~gareth/ISL/)
2. [Hands-on Machine Learning with Scikit-Learn and TensorFlow](http://shop.oreilly.com/product/0636920052289.do)
