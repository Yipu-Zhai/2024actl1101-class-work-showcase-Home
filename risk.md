
# Risk and Insurance

## Introduction and Motivation

### Motivation

From the [Actuaries Institute](https://www.actuaries.asn.au/becoming-an-actuary/):

> "Actuaries evaluate risk and opportunity - applying mathematical, statistical, economic, and financial analyses to a wide range of business problems."

A key concept here is **risk**; actuaries must understand the uncertainties and potential losses associated with various events, such as insurance claims, investment returns, and retirement benefits. Understanding the principles of **risk transfer** through insurance is fundamental: transferring a potential loss from the insured to the insurer in exchange for a premium.

### Overview

The principles of risk and insurance are not just theoretical; they are **applied tools** that actuaries use to manage uncertainty and provide financial security. This week covers the basics of **insurance economics**, **risk measurement**, and the **role of variability** in risk assessment. More advanced topics will be covered in later courses, such as ACTL2111: Financial Mathematics and ACTL2131: Stochastic Models.

### Some Applications

1. **Personal Insurance**
   - Health insurance - covering medical expenses
   - Life insurance - providing financial support to beneficiaries

2. **Property and Casualty Insurance**
   - Home insurance - protecting against property damage or theft
   - Auto insurance - covering vehicle damage and liability

3. **Corporate Risk Management**
   - Liability insurance - protecting businesses against legal claims
   - Business interruption insurance - covering loss of income due to disruptions

## Economics of Risk

"Risk comes from not knowing what you're doing." - Warren Buffett

### Definitions

- **Risk** - Future uncertainty that can affect the outcome of an event.
- **Insurance** - A financial arrangement where an insured pays a premium to transfer the risk of a potential loss to an insurer.

### Expected Value and Variability

- **Expected Value (E[X])** - The average outcome of a random variable X over many trials.
- **Variance (Var[X])** - A measure of how much the outcomes of X deviate from the expected value.

### Example: Investment Choices

You have a choice of investing 10,000 in two potential investments:

| Outcome | Probability | Investment A | Investment B |
|---------|-------------|--------------|--------------|
| Good    | 1/10        | 50,000       | 26,000       |
| Middle  | 22/25       | 12,500       | 15,000       |
| Bad     | 1/50        | 0            | 10,000       |


#### Solution

- Expected values:
  
$$
E[A] = \frac{1}{10} \cdot 50,000 + \frac{22}{25} \cdot 12,500 + \frac{1}{50} \cdot 0 = 16,000
$$

$$
E[B] = \frac{1}{10} \cdot 26,000 + \frac{22}{25} \cdot 15,000 + \frac{1}{50} \cdot 10,000 = 16,000
$$

- Variance and standard deviation:

$$
\text{Var}[A] = 131,500,000 \quad \text{and} \quad \sigma_A = 11,467.34
$$

$$
\text{Var}[B] = 11,600,000 \quad \text{and} \quad \sigma_B = 3,405.88
$$


Investment B has lower variability and is usually regarded as less risky.

## Expected Utility and Risk Aversion

### Utility Functions

- **Utility (v(w))** - A measure of satisfaction or value derived from wealth w.
- **Expected Utility** - The average utility over all possible outcomes.

### Risk Aversion

- An individual is **risk averse** if they prefer the expected value of wealth over the random wealth itself:
  
$$
W \prec E[W] \quad \Longleftrightarrow \quad E[v(W)] < v(E[W]).
$$

- **Concave Utility Function** - Indicates risk aversion:
  
$$
\frac{\partial v}{\partial w} > 0  \quad \text{and} \quad \frac{\partial^2 v}{\partial w^2} < 0.
$$


### Insurance Example

- **With Insurance**: Final wealth is $w_0 - k\ell$ with certainty, where $k$ is the premium rate.
- **Without Insurance**: Final wealth is a random variable depending on whether the loss $\ell$ occurs.

The individual chooses insurance if:

$$
v(w_0 - k \ell) > pv( w_0 - \ell) + (1-p)v( w_0 ).
$$

## Risk Pooling for Independent Risks

### Setting and Assumptions

- Assume $n$ individuals each face an independent risk $X_i$ with identical distribution.
- **Risk Pooling**: Individuals agree to pay the actual average loss into a pool, which then covers the losses.

### Expectation and Variance

- **Expectation** of the average loss:
  
$$
E[A] = E\left[ \sum_{i=1}^{n}X_{i} / n \right] = \mu
$$

- **Variance** of the average loss:
  
$$
\text{Var}[A] = \frac{\sigma^2}{n}.
$$

Pooling reduces variability and is beneficial for risk-averse individuals.


## Correlation and Dependence

### Definitions

- **Covariance** - Measure of linear dependence between two variables.
  
$$
Cov(X,Y) = E[(X-E[X])(Y-E[Y])] = E[XY] - E[X]E[Y].
$$

- **Correlation** - Standardized measure of covariance:
  
$$
\rho(X,Y) = \frac{Cov(X,Y)}{\sigma_X \sigma_Y}.
$$

### Pooling of Correlated Risks

- Variance of the average loss for two correlated risks X and Y:
  
$$
Var\left( \frac{X+Y}{2} \right) = \frac{\sigma^2}{2} \left( 1 + \rho \right).
$$

- **Diversification Benefits**: As long as $\rho \neq 1$, pooling reduces risk.


---

**Note**: This content is a simplified representation for educational purposes. Real-world applications involve more complexity and require professional actuarial judgment.
