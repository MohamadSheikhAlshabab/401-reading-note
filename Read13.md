# Read: Class 13 [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read01.md)

## How to run Linear regression in Python scikit-Learn:
 - Scikit-learn is a powerful Python module for machine learning.
 - It contains function for regression, classification, clustering, model selection and dimensionality reduction.
 - Important functions of a linear regression model are:
  - 1 - lm.fit() -> fits a linear model
  - 2 - lm.predict() -> Predict Y using the linear model with estimated coefficients
  - 3 - lm.score() -> Returns the coefficient of determination (R^2). A measure of how well observed outcomes are replicated by the model, as the proportion of total variation of outcomes explained by the model.
  
### Residual Plots: 
 - Residual plots are a good way to visualize the errors in your data. If you have done a good job then your data should be randomly scattered around line zero. 
 - ![img](https://bigdata-madesimple.com/wp-content/uploads/2016/04/Plt-scatter.png)
 - ![img](https://bigdata-madesimple.com/wp-content/uploads/2016/04/Residual-plot.png)
 
### Conclusion:
- 1 - I explored the boston data set and then renamed its column names.
- 2 - I explored the boston data set using .DESCR, my goal was to predict the housing prices using the given features.
- 3 - I used Scikit learn to fit linear regression to the entire data set and calculated the mean squared error.
- 4 - I made a train-test split and calculated the mean squared error for my training data and test data.
- 5 - I then plotted the residuals for my training and test datasets.

----
## Linear Regression in Python:
 - Linear regression is one of the fundamental statistical and machine learning techniques.
 
 ### Regression:
  - Regression analysis is one of the most important fields in statistics and machine learning.
  - There are many regression methods available. Linear regression is one of them.
  - in regression analysis, you usually consider some phenomenon of interest and have a number of observations. 
  - Each observation has two or more features.
  - Following the assumption that (at least) one of the features depends on the others, you try to establish a relation among them.
  - __you need to find a function that maps some features or variables to others sufficiently well.__
  - The dependent features are called __the dependent variables, outputs, or responses__.
  - The independent features are called __the independent variables, inputs, or predictors__.
  
### Linear Regression:
 - __Problem Formulation__: 
  - some dependent variable 𝑦 on the set of independent variables 𝐱 = (𝑥₁, …, 𝑥ᵣ), where 𝑟 is the number of predictors, you assume a linear relationship between 𝑦 and 𝐱: 𝑦 = 𝛽₀ + 𝛽₁𝑥₁ + ⋯ + 𝛽ᵣ𝑥ᵣ + 𝜀.
  - This equation is the regression equation. 𝛽₀, 𝛽₁, …, 𝛽ᵣ are the regression coefficients, and 𝜀 is the random error.
  - calculates the estimators of the regression coefficients or simply the predicted weights, denoted with 𝑏₀, 𝑏₁, …, 𝑏ᵣ. They define the estimated regression function 𝑓(𝐱) = 𝑏₀ + 𝑏₁𝑥₁ + ⋯ + 𝑏ᵣ𝑥ᵣ.
  - The estimated or predicted response, 𝑓(𝐱ᵢ), for each observation 𝑖 = 1, …, 𝑛, should be as close as possible to the corresponding actual response 𝑦ᵢ. 
  - The differences 𝑦ᵢ - 𝑓(𝐱ᵢ) for all observations 𝑖 = 1, …, 𝑛, are called the residuals.
  - Regression is about determining the best predicted weights, that is the weights corresponding to the smallest residuals.
  - To get the best weights, you usually minimize the sum of squared residuals (SSR) for all observations 𝑖 = 1, …, 𝑛: SSR = Σᵢ(𝑦ᵢ - 𝑓(𝐱ᵢ))². This approach is called the method of ordinary least squares.
- __Simple Linear Regression__:
 -  is the simplest case of linear regression with a single independent variable, 𝐱 = 𝑥.
 ![img](https://files.realpython.com/media/fig-lin-reg.a506035b654a.png)
- __Multiple Linear Regression__:
 -  is a case of linear regression with two or more independent variables.
 - The estimated regression function is 𝑓(𝑥₁, …, 𝑥ᵣ) = 𝑏₀ + 𝑏₁𝑥₁ + ⋯ +𝑏ᵣ𝑥ᵣ, and there are 𝑟 + 1 weights to be determined when the number of inputs is 𝑟.
- __Polynomial Regression__:
 - a generalized case of linear regression. 
 - in addition to linear terms like 𝑏₁𝑥₁, your regression function 𝑓 can include non-linear terms such as 𝑏₂𝑥₁², 𝑏₃𝑥₁³, or even 𝑏₄𝑥₁𝑥₂, 𝑏₅𝑥₁²𝑥₂, and so on.
 - The simplest example of polynomial regression has a single independent variable, and the estimated regression function is a polynomial of degree 2: 𝑓(𝑥) = 𝑏₀ + 𝑏₁𝑥 + 𝑏₂𝑥².
 - you can solve __the polynomial regression problem as a linear problem with__ the term 𝑥² regarded as an input variable.
- __Underfitting and Overfitting__:
 -  the choice of the optimal degree of the polynomial regression function:  __underfitting and overfitting__.
 - __Underfitting__ occurs when a model can’t accurately capture the dependencies among data, usually as a consequence of its own simplicity.
  - It often yields a low 𝑅² with known data and bad generalization capabilities when applied with new data.
 - __Overfitting__ happens when a model learns both dependencies among data and random fluctuations.
  - When applied to known data, such models usually yield high 𝑅². However, they often don’t generalize well and have significantly lower 𝑅² when used with new data.
  ![img](https://files.realpython.com/media/poly-reg.5790f47603d8.png) 
---
 ### Types of Linear Regression:
 - 1 - Simple linear regression: 1 dependent variable (interval or ratio), 1 independent variable (interval or ratio or dichotomous)
 - 2 - Multiple linear regression: 1 dependent variable (interval or ratio) , 2+ independent variables (interval or ratio or dichotomous)
 - 3 - Logistic regression: 1 dependent variable (dichotomous), 2+ independent variable(s) (interval or ratio or dichotomous)
 - 4 - Ordinal regression: 1 dependent variable (ordinal), 1+ independent variable(s) (nominal or dichotomous)
 - 5 - Multinomial regression: 1 dependent variable (nominal), 1+ independent variable(s) (interval or ratio or dichotomous)
 - 6 - Discriminant analysis:1 dependent variable (nominal), 1+ independent variable(s) (interval or ratio)

   
