
# Introduction to Probability 

## Motivation

### What is Probability?

Probability is the branch of mathematics that studies the possible outcomes of given events together with the outcomes' relative likelihoods and distributions. In common usage, the word "probability" is used to mean the chance that a particular event (or set of events) will occur expressed on a linear scale from 0 (impossibility) to 1 (certainty), also expressed as a percentage between 0 and 100%. [More about Probability](https://mathworld.wolfram.com/Probability.html)

### Why Do We Need Probability in Actuarial Science?

The work of actuaries is intrinsically related to **uncertainty**. Consider questions such as:
- Will life expectancy improve in the next decade?
- At what age are people most likely to retire?
- How many insurance claims will we have this month? How big will they be?
- How much money can we expect to gain (or lose) from our investments in the stock market?

A good understanding of Probability (and Statistics) is necessary to tackle these types of questions.

## Sample Space & Events

### Sample Space and Events

A **random experiment** is an experiment whose outcome is not known in advance with certainty. Example: tossing a dice and recording the result.

The **sample space** of a random experiment (often denoted $\Omega$) is the set of all possible outcomes. In the dice tossing example, $\Omega = \\{1,2,3,4,5,6\\}$.

Any subset $A$ of the sample space is called an **event**. Example: $A = \\{1,3,5\\}$ ('obtaining an odd number') is an event in $\Omega$. $B= \\{1\\}$ ('obtaining 1') is also an event in $\Omega$.

Given a context, we want to determine the probabilities that certain events occur.

## Elementary Rules of Probability

There are a few elementary rules everyone should know. Let $A$ and $B$ be events in the same sample space, then:

- $0 \\leq \\Pr[A] \\leq 1$
- $\\Pr[A] = 1 - \\Pr[A^{\\text{c}}]$
- $\\Pr[A \\cup B] = \\Pr[A] + \\Pr[B] - \\Pr[A \\cap B]$

Where $A^{\\text{c}}$ means not $A$, $A \\cup B$ means $A$ or $B$, while $A \\cap B$ means $A$ and $B$.

## Determining Probabilities

If all outcomes of an experiment are equally likely, a useful formula to determine the probability of an event \(A\) is given by:

$$
\Pr[A] = \frac{\text{number of favourable cases to } A}{\text{number of total cases}}
$$

Example: What is the probability of getting an odd number upon rolling a fair dice?

$$
\frac{\text{number of favourable cases}}{\text{number of total cases}} = \frac{3}{6} = \frac{1}{2}.
$$


## Permutations & Combinations

## Permutations

Given Given a list of **distinct** objects, any **distinct arrangement** of them is called a **permutation**. For example, given the three letters _abc_, the possible permutations are: _abc, acb, bac, bca, cab, cba_.

In general, the number of possible permutations for $n$ different objects is:

$$
n! = n \cdot (n-1) \cdot (n-2) \cdot \ldots \cdot 2 \cdot 1
$$

**Proof**: Consider this as allocating $n$ objects within $n$ 'spots'. Then:

- The first spot has $n$ options.
- The second spot has $n-1$ options, as one object is already placed in the first 'spot'.
- ...
- The last spot has only 1 option.

## Combinations

Given a list of **distinct** objects, a selection of them for which **the order of the selected items does not matter**, is called a **combination**.

Given $n$ distinct objects, the number of ways to select $k$ (where $k \leq n$) of them (where the order of selection does not matter) is:

$$
{n \choose k} = \frac{n!}{k!(n-k)!}
$$

**Example**: If there are initially 49 participants at _The Voice_, and Delta Goodrem needs to create a team of 10, how many different teams can she possibly create?

**Solution**: Delta can choose from 49 distinct people, but the order in which she chooses does not influence the team. Hence, the answer is:

$$
{49 \choose 10} \approx 8.2 \text{ billions}
$$

## Random Variables

A **random variable** $X$ is a function that assigns values to the possible outcomes of a random experiment. For example, in the experiment of tossing two dice, a random variable $X$ could represent the sum of both dice. Another random variable $Y$ could represent the minimum of the two dice, etc.

**Discrete random variables**: These are variables where the number of possible values is finite or countably infinite.

**Continuous random variables**: These variables have possible values that appear on a continuous spectrum (hence are uncountably infinite).

## Random Variables: Examples in Actuarial Studies

### Discrete Random Variables
- Number of motor vehicle accidents occurring during a particular month.
- Number of lives lost to cancer during a particular time period.

### Continuous Random Variables
- Time until the first accident on a car insurance policy.
- Claim payment for a fire insurance policy.

## Probability Mass Function (PMF)

For a **discrete random variable** $X$, the PMF $p(x)$ is the probability that $X$ takes a particular value $x$:

$$
p(x) = \Pr(X = x),
$$

with

$$
p(x) \geq 0,
$$

and

$$
\sum_{\text{all } x} p(x) = 1.
$$

## Probability Density Function (PDF)

For a **continuous random variable** $X$, the PDF $f(x)$ is defined such that:

$$
\Pr(a \leq X \leq b) = \int_{a}^{b} f(x) dx,
$$

with

$$
f(x) \geq 0 \text{ for } -\infty < x < \infty,
$$

and

$$
\int_{-\infty}^{\infty} f(t)  dt = 1.
$$

## Cumulative Distribution Function (CDF)

For **any** random variable $X$, the CDF, denoted $F(x)$, is defined as:
$$F(x) = \Pr(X \leq x).$$
It gives the probability that a random variable $X$ is **less than or equal to** a specified value $x$. The CDF always satisfies:
$$F(-\infty) = 0,$$
and
$$F(\infty) = 1.$$

### CDF: Discrete vs Continuous Case

For a **discrete random variable** $X$, the CDF of $X$ can be computed as:

$$
F(x) = \Pr(X \leq x) = \sum_{k \leq x} p(k).
$$

For a **continuous random variable** $X$, the CDF of $X$ can be computed as:

$$
F(x) = \Pr(X \leq x) = \int_{-\infty}^{x} f(t) dt,
$$

and we also have:

$$
f(x) = \frac{d}{dx} F(x).
$$

## Expectation

The **expectation** (or **expected value**) of a random variable $X$, denoted $E[X]$ (and sometimes $\mu$), is the weighted average of all possible values $X$ can take, each value being weighted by the probability that $X$ assumes it. For discrete random variables:

$$
E[X] = \mu = \sum_{\text{all } x} x p(x)
$$

For continuous random variables:

$$
E[X] = \mu = \int_{-\infty}^{\infty} x f(x) dx
$$

## Expectation of a Function of $X$

It is often useful to compute the expectation of a **function of** a random variable, $g(X)$:
- For discrete random variables:
  
$$
E[g(X)] = \sum_{\text{all } x} g(x) p(x)
$$

- For continuous random variables:
  
$$
E[g(X)] = \int_{-\infty}^{\infty} g(x) f(x) dx
$$

- Moments (about the origin) of a random variable are given by:
  
$$
E[X^r] \text{ for } r=1,2,3,\ldots
$$

## Law of Total Expectation

For two random variables $X$ and $Y$, we have the so-called **Law of Total Expectation**:

$$
\mathbb{E}[X] = \mathbb{E}[\mathbb{E}[X|Y]].
$$

A consequence of this result is that for events $A_1, \ldots, A_n$ forming a partition of a sample space $\Omega$, we have:

$$
\mathbb{E}[X] = \sum_{i=1}^n \mathbb{E}[X|A_i] \Pr[A_i].
$$

(events $A_i$ form a **partition** if they are all mutually exclusive and $\cup_{i=1}^n A_i = \Omega$.)


## Law of Total Expectation: Example

**Question**: Let $Y$ be the number of drinks Josephine has the night before an exam, and let $X$ be her result in said exam (out of 100), with

$$
\Pr[Y=0] = 0.5, \quad \Pr[Y=i] = 0.1 \text{ for } i \in \{1,2,3,4,5\}
$$

$$
\mathbb{E}[X|Y] = 90 - 2Y^2.
$$

What is the expectation of her result in this exam?

**Answer**:

$$
\mathbb{E}[X] = \mathbb{E}[\mathbb{E}[X|Y]] = \mathbb{E}[90 - 2Y^2] = 90 \cdot 0.5  + (88 + 82 + 72 + 58 + 40) \cdot 0.1 = 79.
$$


## Variance

The **variance**, denoted $\mathbb{V}[X]$ (or $\sigma^2$), is another key property of a random variable $X$. It is defined as

$$
\mathbb{V}[X] = \sigma^2 = \mathbb{E}[(X - \mu)^2] = \mathbb{E}[X^2] - (\mathbb{E}[X])^2
$$

The variance measures the 'dispersion', 'spread', or 'volatility' of a random variable. We call **standard deviation** the square root of the variance, denoted $\sigma$.

## Properties of the Expectation and Variance

For $X$ a random variable and $a, b$ two constants:

$$
\mathbb{E}[aX + b] = a \mathbb{E}[X] + b
$$

$$
\mathbb{V}[aX + b] = a^2 \mathbb{V}[X]
$$

For many random variables $X_1, X_2, \ldots, X_n$, we have:

$$
\mathbb{E}[X_1 + \ldots + X_n] = \mathbb{E}[X_1] + \ldots + \mathbb{E}[X_n]
$$

If the random variables $X_1, X_2, \ldots, X_n$ are **independent**, then:

$$
\mathbb{E}[X_1 \times \ldots \times X_n] = \mathbb{E}[X_1] \times \ldots \times \mathbb{E}[X_n]
$$

$$
\mathbb{V}[X_1 + \ldots + X_n] = \mathbb{V}[X_1] + \ldots + \mathbb{V}[X_n]
$$

## Common Probability Distributions in Actuarial Studies

### Discrete Distributions
- **Poisson**: Often used to model the probability of occurrence of rare events such as insurance claims, catastrophes.
- **Binomial**: Used for the probability that a number of lives in a group with the same chance of dying will die, assuming independence between the lives.

### Continuous Distributions
- **Exponential and Gamma**: Used for the probability distribution of time until an event occurs.
- **Normal and Log-Normal**: Often used to model continuous data that follows a symmetric distribution around the mean.

We will mainly use the Poisson, Binomial, Normal, and Log-normal distributions.

## Poisson Distribution

A Poisson Distribution is defined as $X \sim \text{Poisson}(\lambda)$ with the probability: 

$$
\Pr(X=x) = \frac{e^{-\lambda} \lambda^x}{x!}, \quad x=0,1,2\ldots
$$ 

$$
\mathbb{E}[X] = \lambda
$$ 

$$
\mathbb{V}[X] = \lambda
$$

## Poisson Distribution - Example

Assume the probability of an insurance claim on a particular policy during a year is Poisson distributed with $\lambda = \frac{1}{100}$. Calculate the probability that there will be no claims during the year: 

$$
\Pr(X = 0) = e^{-\frac{1}{100}} \approx 0.99005
$$

## Binomial Distribution

A Binomial Distribution is described as $X \sim \text{Binomial}(n, p)$ and is used to determine the probability of exactly $x$ successes in $n$ independent trials: 

$$
\Pr(X=x) = \binom{n}{x} p^x (1-p)^{n-x}, \quad x=0,1,2\ldots
$$ 

$$
\mathbb{E}[X] = np$$ $$\mathbb{V}[X] = np(1-p)
$$

## Binomial Distribution - Example

What is the probability that exactly 3 ones appear when 6 dice are thrown? 

$$
X \sim \text{Binomial}(6, \frac{1}{6})
$$ 

$$
\Pr(X = 3) = \binom{6}{3} \left(\frac{1}{6}\right)^3 \left(\frac{5}{6}\right)^3
$$

## Exponential Distribution

The Exponential Distribution is often used to model the lifetimes, like that of light bulbs. The probability density function is defined for $X \sim \text{Exponential}(\theta)$ as: 

$$
f(x) = \begin{cases} 
\frac{e^{-\frac{x}{\theta}}}{\theta} & \text{if } x \geq 0 \\
0 & \text{if } x < 0
\end{cases}
$$

$$
F(x) = \begin{cases}
1 - e^{-\frac{x}{\theta}} & \text{if } x \geq 0 \\
0 & \text{if } x < 0
\end{cases}
$$

$$
\mathbb{E}[X] = \theta
$$ 

$$
\mathbb{V}[X] = \theta^2
$$

## Exponential Distribution - Example

Assume the survival time of an individual is exponentially distributed with $\theta = 50$ years. Calculate the probability that the individual will live more than 10 years: $$1 - F(10) = 1 - (1 - e^{-\frac{10}{50}}) \approx 0.81873$$

## Normal Distribution

The Normal Distribution is defined as $X \sim \text{Normal}(\mu, \sigma)$, or $X \sim N(\mu, \sigma^2)$ with the probability density function:

$$
f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{1}{2} \left(\frac{x - \mu}{\sigma}\right)^2}, \quad -\infty < x < \infty
$$

Expected value and variance are given by:

$$
\mathbb{E}[X] = \mu
$$

$$
\mathbb{V}[X] = \sigma^2
$$

- The normal distribution is the "bell" shaped symmetric distribution that typically results from the accumulation of a large number of independent random events.
- Often used for probabilities since values of cumulative normal are tabulated and tools like Excel (and other packages - R, SAS, MATLAB, Python) can calculate Normal probabilities.

## Standard Normal Distribution

- The case of Normal distribution where $\mu = 0$ and $\sigma = 1$ is known as the standard Normal distribution.
- Tables of the Cumulative Standard Normal Distribution are available and easy to use. The cumulative distribution function is defined as:
  
$$
\Phi[x] = \int_{-\infty}^x \frac{1}{\sqrt{2\pi}} e^{-\frac{1}{2} s^2} ds
$$

- If $X$ is a standard normal random variable, then:

$$
Y := \mu + \sigma X
$$

follows $N(\mu, \sigma^2)$.

## Link between Binomial and Normal

For large values of $n$, the Binomial distribution:

$$
\text{Binomial}(n, p)
$$

is well approximated by the Normal distribution:

$$
\text{Normal}\left(np, \sqrt{np(1-p)}\right)
$$

or $N(np, npq)$.

## Transforming the Normal Distribution

- In actuarial applications, we are interested in modeling survival times (of people, companies) and insurance claim amounts (losses).
- These are positive valued random variables.
- The normal distribution is a symmetric distribution that can take negative values.
- Survival times and losses are always positive and the distribution is not symmetric - usually positively skewed to the higher positive values.

## Log-Normal Distribution

- The exponential of a $\text{Normal}(\mu, \sigma)$ random variable follows a:
  
$$
\text{Log-normal}(\mu, \sigma)
$$

distribution, which is only defined for positive values.
- If $Z$ is a Normal random variable, then $X = e^Z$ is Log-normal.

### Log-Normal Distribution Continued

$$
X \sim \text{Log-normal}(\mu, \sigma)
$$

The probability density function for $X$ is:

$$
f(x) = \begin{cases}
\frac{1}{\sigma x \sqrt{2\pi}} e^{-\frac{1}{2} \left(\frac{\ln x - \mu}{\sigma}\right)^2}, & x > 0 \\
0, & x \leq 0
\end{cases}
$$

Expected value and variance are:

$$
\mathbb{E}[X] = e^{\mu + \frac{1}{2} \sigma^2}
$$

$$
\mathbb{V}[X] = e^{2\mu + \sigma^2} (e^{\sigma^2} - 1)
$$

Expected value of $X^k$:

$$
\mathbb{E}[X^k] = e^{k\mu + \frac{1}{2} k^2 \sigma^2}
$$

## References

### Introduction Level
- **Principles of Actuarial Science** by Michael Sherris, Cengage Learning, Paperback, 2010 Edition, APN: 9780170188210, ISBN: 0170188213. Chapters 2.2, 2.3. Ideal for those beginning their journey in actuarial studies.

### Advanced Level
- **A First Course in Probability** (Tenth Edition), 2019, by Sheldon M. Ross. Pearson. ISBN: 978-0134753119. This text covers Chapters 1-8 and is suited for in-depth study of advanced probability concepts.

## [Return Home](https://2024actl1101.github.io/Home/)
