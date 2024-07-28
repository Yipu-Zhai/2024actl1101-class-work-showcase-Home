# Introduction to Statistical Machine Learning 

## Simple Linear Regression

Simple linear regression is straightforward: it predicts a quantitative response $Y$ based on a single predictor variable $X$. It assumes a linear relationship between $X$ and $Y$:

$$Y \approx \beta_0 + \beta_1X$$

### Usage Example
For instance, if $X$ represents TV advertising budgets and $Y$ represents sales, the model would be:

$$\text{sales} \approx \beta_0 + \beta_1 \times \text{TV}$$

### Coefficients
- $\beta_0$ and $\beta_1$ are the model coefficients.
- Estimates $\hat{\beta}_0$ and $\hat{\beta}_1$ are used for predictions:

$$\hat{Y} = \hat{\beta}_0 + \hat{\beta}_1X$$

### Estimating the Coefficients

To estimate $\beta_0$ and $\beta_1$, you minimize the residual sum of squares (RSS):

$$\text{RSS} = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$

The least squares formula to estimate the coefficients is:

$$\hat{\beta}_1 = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sum (x_i - \bar{x})^2}$$
$$\hat{\beta}_0 = \bar{y} - \hat{\beta}_1\bar{x}$$

Where:
- $\bar{x}$ and $\bar{y}$ are the sample means of $X$ and $Y$ respectively.

### Predictions

Given a new value $x$, the predicted value of $y$ is:

$$\hat{y} = \hat{\beta}_0 + \hat{\beta}_1x$$

This basic framework can be extended to multiple linear regression where more than one predictor variable is used.

### Example: Predicting Sales from TV Advertising

#### Problem Setup

Consider a dataset where the dependent variable is sales (in thousands of units) and the independent variable is the budget for TV advertising (in thousands of dollars). The goal is to understand how changes in the TV advertising budget could affect sales.

#### Regression Equation

The regression model can be expressed in the equation form:

$$Y \approx \beta_0 + \beta_1X$$

Where:
- $Y$ represents sales,
- $X$ represents the TV advertising budget,
- $\beta_0$ is the y-intercept of the regression line,
- $\beta_1$ is the slope of the regression line, indicating the change in sales for each unit change in TV advertising.

#### Estimating the Coefficients

Suppose we fit a simple linear regression model to the data and found the following estimates for the coefficients:

- $\hat{\beta}_0 = 7.03$ (This suggests that if no money is spent on TV advertising, sales would still average 7,030 units.)
- $\hat{\beta}_1 = 0.0475$ (This suggests that for each $1,000 spent on TV advertising, sales increase by approximately 47.5 units.)

These coefficients are estimated using the least squares criterion, aiming to minimize the sum of the squared differences between the observed values and the values predicted by the model.

#### Interpretation

The estimated regression equation would be:

$$\hat{Y} = 7.03 + 0.0475X$$

This equation allows us to predict the sales based on the TV advertising budget. For instance, if $50,000 is spent on TV advertising, the predicted sales would be:

$$\hat{Y} = 7.03 + 0.0475 \times 50 = 9.41 \text{ (in thousands of units, or 9,410 units)}$$

### Model Assessment

To assess the accuracy of the regression model, you might look at metrics like $R^2$, which measures the proportion of variance in the dependent variable that is predictable from the independent variable. Additionally, examining plots of residuals versus predicted values can help validate the assumption of linearity and homoscedasticity.

### Conclusion

This example demonstrates how simple linear regression can be applied to real-world data to make predictions and drive decision-making processes. Understanding the relationship between advertising budgets and sales can help a business allocate its marketing resources more effectively.


### Key Takeaways

- Simple linear regression is used for predicting a quantitative response using a single predictor variable.
- The relationship between the predictor and the response is assumed to be linear.
- Least squares is used to estimate the parameters of the linear model.

---

## Multiple Linear Regression

Multiple linear regression extends simple linear regression to predict a response $Y$ based on multiple predictor variables. It's formulated as:

$$Y = \beta_0 + \beta_1X_1 + \beta_2X_2 + \cdots + \beta_pX_p + \epsilon$$

where $X_j$ represents the $j^{th}$ predictor and $\beta_j$ quantifies the association between that variable and the response.

### Estimating the Regression Coefficients

In multiple linear regression, the coefficients $\beta_0, \beta_1, \ldots, \beta_p$ are unknown and must be estimated. Given estimates $\hat{\beta}_0, \hat{\beta}_1, \ldots, \hat{\beta}_p$, predictions can be made using:

$$\hat{y} = \hat{\beta}_0 + \hat{\beta}_1x_1 + \hat{\beta}_2x_2 + \cdots + \hat{\beta}_px_p$$

The coefficients are estimated using the least squares approach, similar to simple linear regression. The aim is to minimize the sum of squared residuals:

$$\text{RSS} = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$

### Example with Advertising Data

For example, in an advertising dataset where we want to predict sales based on advertising budgets for TV, radio, and newspaper:

$$\text{sales} = \beta_0 + \beta_1 \times \text{TV} + \beta_2 \times \text{radio} + \beta_3 \times \text{newspaper} + \epsilon$$

### Important Questions

When performing multiple linear regression, several key questions typically arise:

1. **Is at least one of the predictors useful in predicting the response?**
2. **Do all the predictors help to explain $Y$, or is only a subset of the predictors useful?**
3. **How well does the model fit the data?**
4. **Given a set of predictor values, what response value should we predict, and how accurate is our prediction?**

These questions are answered using statistical tests such as the F-test, t-tests, and measures like $R^2$.

### Fitting the Model

The model fitting involves:

- **Checking the significance of predictors:** Using t-tests for each predictor.
- **Assessing the overall model fit:** Using an F-test to determine if at least one predictor is significantly related to the response.
- **Determining the goodness of fit:** Using $R^2$, which provides the proportion of variance in the dependent variable that is predictable from the independent variables.

### Example: Detailed Analysis with a Table

Suppose the regression results for the advertising data are as follows:

| Predictor  | Coefficient | Std. Error | t-statistic | p-value |
|------------|-------------|------------|-------------|---------|
| Intercept  | 2.939       | 0.3119     | 9.42        | <0.0001 |
| TV         | 0.046       | 0.0014     | 32.81       | <0.0001 |
| Radio      | 0.189       | 0.0086     | 21.89       | <0.0001 |
| Newspaper  | -0.001      | 0.0059     | -0.18       | 0.8599  |

This table indicates that:

- TV and Radio have significant positive impacts on sales.
- Newspaper advertising does not significantly affect sales, as its p-value is much higher than the typical significance level (0.05).

### Further Considerations

- **Adjustments for multiple testing:** When dealing with multiple predictors, adjusting significance levels or using methods like Bonferroni correction might be necessary to account for the increase in Type I error rate.
- **Collinearity among predictors:** High correlation among predictor variables can affect the stability of coefficient estimates.

