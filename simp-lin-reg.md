# Simple Linear Regression

## Definition

- Simple linear regression uses a single predictor variable *X* to predict a quantitative resposne *Y* and assumes an approximate linear relationship between *X* and *Y*. 
- This can be described mathematically by *regression Y onto X*, as shown below
*<p align = "center"> Y ≈ &beta;<sub>0</sub> + &beta;<sub>1</sub>X  </p>*

- The two parameters, *&beta;<sub>0</sub>* and *&beta;<sub>1</sub>*, describe the *intercept* and the *slope* of the linear model, respectively
	-  *&beta;<sub>0</sub>* indicates the expected value of *Y* when *X = 0*
	-  *&beta;<sub>1</sub>* indicates the average change in *Y* associated with a one-unit increase in *X*
- Since the true values are unknown, the *training data* is used to produce estimates, *&beta;<sub>0</sub>'* and *&beta;<sub>1</sub>'*, as shown below
*<p align = "center"> y' = &beta;<sub>0</sub>' + &beta;<sub>1</sub>'x  </p>*


## Coefficient estimation

- The first step of building a simple linear regression model is to use the *training data* to estimate the *coefficients*, or *parameters*, of the model
- The goal of the estimated coefficients is for the predicted value to be as close to the *training data*, such that for *i = 1, ..., n*
*<p align = "center"> y<sub>i</sub> ≈ &beta;<sub>0</sub>' + &beta;<sub>1</sub>'x<sub>i</sub>  </p>*
- The most common appoach to measuring *closeness* of the predicted data and *training data* is to *minimize the least squares*
	- The *residual sum of squares (RSS)* is defined as
*<p align = "center"> RSS = e<sub>1</sub><sup>2</sup> + e<sub>2</sub><sup>2</sup> + ... + e<sub>n</sub><sup>2</sup>  
RSS = (y<sub>1</sub> - &beta;<sub>0</sub>' - &beta;<sub>1</sub>'x<sub>1</sub>)<sup>2</sup> + (y<sub>2</sub> - &beta;<sub>0</sub>' - &beta;<sub>1</sub>'x<sub>2</sub>)<sup>2</sup> + ... + (y<sub>n</sub> - &beta;<sub>0</sub>' - &beta;<sub>1</sub>'x<sub>n</sub>)<sup>2</sup> </p>*
	- The *least squares* approach chooses &beta;<sub>0</sub>' and &beta;<sub>1</sub>' to minimize the *RSS*, i.e. the *least squares coefficient estimates* for simple linear regression is defined as
	<p align = "center"> <img src="figures/simp-lin-reg-01.png" height="80px"/> </p>
	- In other words, *RSS* is a function of &beta;<sub>0</sub>' and &beta;<sub>1</sub>'. The values where &beta;<sub>0</sub>' and &beta;<sub>1</sub>' can minimize *RSS* is shown above
	- The *least squares regression coefficient estimates*, as shown above, define the *least square line*


- Recall that the true relationship between *X* and *Y* is unknown and there is a mean-zero random error term, &epsilon;, that cannot be reduced
	- Under a linear function, the *population regression line* can be written as
*<p align = "center"> Y = &beta;<sub>0</sub> + &beta;<sub>1</sub>X + &epsilon;  </p>*
	- The error term describes all variations of *Y* that is not captured by the simple linear model, and is assumed to be independent of *X*

## Coefficient estimation assessment

To assess how close the estimated coefficients *&beta;<sub>0</sub>'* and *&beta;<sub>1</sub>'* are to the true value, *standard error*, *confidence interval*, and *hypothesis testing* can be performed

- The *standard error* associated with *&beta;<sub>0</sub>'* and *&beta;<sub>1</sub>'* can be computed with the following
	<p align = "center"> <img src="figures/simp-lin-reg-02.png" height="55px"/> </p>
	- *&sigma;<sup>2</sup>* = Var(&epsilon;), where the errors *&epsilon;<sub>i</sub>* for each observation are uncorrelated with common vriance *&sigma;<sup>2</sup>*
	- Note that *SE(&beta;<sub>1</sub>')* is smaller if *x<sub>i</sub>* are more spread out, meaning that given a wider number of *x<sub>i</sub>*, the dynamic range of the linear model is bigger, and therefore leading to a more stable model
- The *95% confidence interval* is defined as a range of values such that with 95% probability, the range wil lcontain the true unknown value of the parameter
	<p align="center"> *&beta;<sub>0</sub>' ± qt x SE(&beta;<sub>0</sub>')*;  *&beta;<sub>1</sub>' ± qt x SE(&beta;<sub>1</sub>')*</p>
	- *qt* is the quantile of *(100 - 95) / 2* with a *n - 2 degrees of freedom* under a *t-distribution*

- *Hypothesis testing* can also be performed using the *standard errors* of the estimated coefficients. The most common involves testing the *null hypothesis* against the *alternative hypothesis*
	- *Null hypothesis H<sub>0</sub>*: There is no relationship between *X* and *Y* (*&beta;<sub>1</sub> = 0*)
	- *Alternative hypothesis H<sub>a</sub>*: There is some relationship between *X* and *Y* (*&beta;<sub>1</sub> ≠ 0*)
	- The *t-statistic* is used to measure the number of standard deviations that *&beta;<sub>1</sub>'* is away from 0, as denoted by
<p align="center"> *t = (&beta;<sub>1</sub>' - 0) / SE(&beta;<sub>1</sub>')* </p> 
	- The *p-value*, in which the probability of observing any number equal or more extreme than *t* under the *null hypothesis*, can then be calculated. 
	- A small *p-value* indicates that the probability of observing a more extreme *t* assuming that *&beta;<sub>1</sub>' = 0* is less likely, and therefore, the *null hypothesis* is rejected
	- This indicates that it is unlikely to observe such a substantial association between the predictor and the response due to chance

- *p-value* can also be explained as:
	- The probability that under the assumption that the null hypothesis is true, the statistical summary would be more extreme than the observed results
	- The probability that the observation of the data and those more extreme happen purely by change 

## Model assessment

Once the *null hypothesis* is rejected, it is then possible to quantify the extent to which the model fits the data. This can be assessed by calculating the *residual standard error (RSE)* and the *R<sup>2</sup>*

- The *RSE* is an estimate of the standard deviation of *&epsilon;*, and is close to the average amount that the response will deviate from the true regression line, shown as
	<p align = "center"> <img src="figures/simp-lin-reg-03.png" height="70px"/> </p>
	- Even if the model was correct and the true values of the unknown *&beta;<sub>0</sub>* and *&beta;<sub>1</sub>* were known, the deviation of the response from the model is described as *RSE*
	- The *RSE* is a measure of the lack of fit of the model to the data. The smaller the *RSE*, the better the model fits the data
	- The *RSE* is measure in the units of *Y*, so the definition of a *good RSE* varies between the questions being asked

- The *R<sup>2</sup>* measure the proportion of variability in *Y* explained by the model using *X*. It takes the form of
	<p align = "center"> *R<sup>2</sup> = (TSS - RSS) / TSS = 1 - (RSS / TSS)* </p>
	- The *TSS* is the *total sum of squares* that measures the total variance in *Y* before the regression is performed
	- The *RSS* is defined above that measures the variability in *Y* after teh regression is performed
	- *TSS - RSS* measures the variability in *Y* that is explained by the regression model
	- The *R<sup>2</sup>* takes the form of a proportion, and therefore is always between 0 and 1, and is independent of the scale of *Y*
	- A *R<sup>2</sup>* close to 1 indicates that a large proportion of the variability in *Y* can be explained by the regression model
	- In a simple linear regression setting, *R<sup>2</sup> = r<sup>2</sup>*, where *r* is the *correlation* of *X* and *Y*

## References

1. [An Introduction to Statistical Learning](http://www-bcf.usc.edu/~gareth/ISL/)
2. [p-value](https://en.wikipedia.org/wiki/P-value)

