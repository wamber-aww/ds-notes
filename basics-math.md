# Fundamental Math and Stats in Machine Learning

Minimal math and statistics concepts behind the basics of machine learning

## Matrix algebra

**Notation**

- **X** is a *n x p* matrix with *n* rows and *p* columns
- *x<sub>i* is the *i*th **row** of the matrix **X**. It is a vector of length *p*, with *p* variables. **Vectors are by default represented as columns** 
- *x<sub>i<sup>T* is then the transposed vector, which is now a row of *p* variables

## Prediction and inference
**Variables**

- Input variables
	- Typically represented as *X<xub>i*
	- Aka predictors, independent variables, features, variables
- Output variables
	- Typically denoted as *Y*
	- Aka response, dependent variables

**Machine learning**

- Refers to a set of approaches to estimate *f* in order to identify the relationship between *X* and *Y*, as shown below
  *<p align="center"> Y = f(X) + &epsilon; </p>*
- Estimating *f* will allow predictions and inference of *Y* with *X*
- Prediction problems emphasize using *X* to identify the value of *Y*
	- Given a set of patient lab reports, predict if the patient will respond well to a treatment
	- Predict if a group of customers will respond well to an ad given their shopping habits
- Inference problems focus on understanding how *Y* changes as a function of *X*
	- Find out how much revenue increase of a product if a company increases TV ads by 5%
	- Determine if there is an association of decreased risk for diabetes if a person exercises three times a week
- Depending on the type of question, different approaches for estimating *f* may be required. 
	- Generally, linear models are better for inference since the relationship of *X* and *Y* is easy to interpret; non-linear models are sometimes better for prediction problems and generates highly accurate predictions for *Y*

**Errors**  

- The goal of machine learning is to estimate *f* to predict or infer *Y*, denoted as
  *<p align="center"> Y' = f'(X) </p>*
- The accuracy of *Y'* depends on the *reducible error* and *irreducible error* 
	- Reducible error is related *f'* and can be minimized by selecting the best algorithms to estimate *f*
	- Irreducible error is also a function of *Y* and is independent of *f*, which is not predicted by *X*. Therefore, the irreducible error introduced by &epsilon; can't be removed

## Basic statistics
**Statistical methods**

- Parametric
	- Makes assumptions about the functional form (or shape) of *f*
	- Reduces estimating *f* to estimating a set of *parameters* that consist *f*
	- Requires less data since only the parameters are being estimated instead of the entire *f* function
	- The estimated *f'* often doesn't fit the true form of *f* due to it's simplicity
- Nonparametric
	- Doesn't make prior assumptions of the shape of *f*
	- Directly uses the observations to estimate *f*, generating a very flexible *f'*
	- Requires a larbe number of observations to obtain an accurate estimate of *f*
	- Generates very accurate predictions but suffers from *overfitting*

## Model assessment

**Mean squared error (MSE): regression**

- *MSE* is used to quantify the difference of predicted response and actual response, denoted as 
  *<p align="center"> MSE = Avg(y<sub>i</sub> - f'(x<sub>i</sub>))<sup>2</sup> </p>*
- *MSE* can be calculated with the training and test data set
	- The *average training MSE* is a function of model (*f'*) flexibility, or *degrees of freedom*
	- A good model is one for which the *test MSE* is smallest
	- The *average test MSE* follows a *U-shape* curve, decreases first as the model becomes more flexible, but quickly increases. The *test MSE* can be written as 
    *<p align="center"> test MSE = Avg(y<sub>0</sub> - f'(x<sub>0</sub>))<sup>2</sup> </p>*
	- Only the *test MSE* is an accurate assessment of whether the model is a good fit, since all methods (algorithms) directly or indirectly minimize the *training MSE*
	- The *test MSE* can be estimated in various ways, including *cross-validation* and *bootstraping*

**The Bayes error rate: classification**

- The *error rate* refers to the proportion of mistakes that are made if *f'* is applied to the observations, denoted as
  *<p align="center"> Avg(I(y<sub>i</sub> ≠ y'<sub>i</sub>)) </p>*
	- I is an *indicator variable* that is 1 if *y<sub>i</sub> ≠ y'<sub>i</sub>* and is 0 if *y<sub>i</sub> = y'<sub>i</sub>*
- The *test error rate* is used to assess model accruacy, which can be written as
  *<p align="center"> Avg(I(y<sub>0</sub> ≠ y'<sub>0</sub>)) </p>*
	- A good classifier is one for which the *test error rate* is smallest
- The *Bayes classifier* predicts the calss for the highest conditional probability of *Y* belonging to class *j*, given the observations *x<sub>0</sub>* shown as
  *<p align="center"> Pr(Y = j | X = x<sub>0</sub>) </p>*
	- The *Bayes classifier* makes its predictions following the *Bayes decision boundary* 
	- The *Bayes error rate* is the lowest possible test error rate produced by the *Bayes classifier*, denoted as
    *<p align="center"> 1 - E(max<sub>j</sub>Pr(Y = j | X = x<sub>0</sub>)) </p>*
	- The *Bayes error rate* is analogous to the *irreproducible error*
- In reality, since the true value of the conditional distribution of *Y* given *X* is unkonwn, the *Bayes classifier* is impossible to compute


**The bias-variance trade-off**

- The expected value of the *test MSE* consists of the *variance of f'(x<sub>0</sub>)*, the *squared bias of f'(x<sub>0</sub>)*, and the *variance of the error &epsilon;*, written as 
  *<p align="center"> E(y<sub>0</sub> - f'(x<sub>0</sub>))<sup>2</sup> = Var(f'(x<sub>0</sub>)) + [Bias(f'(x<sub>0</sub>))]<sup>2</sup> + Var(&epsilon;) </p>*
- Variance refers to the amount by which *f'* changes when a different training data set is used
	- Variance is similar to model *stability*, and the opposite of model *flexibility*
	- Generally, flexibile models have a higher variance
- Bias refers to the error that is introduced by approximating a real-life problem (*f*) with a model (*f'*)
	- Bias is similar to model *complexity* or *flexibility*
	- Generallly, flexibile models have a smaller bias
- The *test MSE* increases or decreases based on the rate of change of variance and bias

## References
1. [An Introduction to Statistical Learning](http://www-bcf.usc.edu/~gareth/ISL/)
2. [Hands-on Machine Learning with Scikit-Learn and TensorFlow](http://shop.oreilly.com/product/0636920052289.do)
