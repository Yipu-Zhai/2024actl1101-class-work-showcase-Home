# Introduction to General Insurance

## Motivation

### General Insurance

- **General Insurance**, also referred to as Property and Casualty Insurance (U.S.), or `Non-Life Insurance`, has many features which make it distinct (conceptually & mathematically) from Life Insurance.
- **Property insurance** covers the **loss** arising from damage to property such as buildings, contents, motor vehicles, aircraft and cargo.
- **Casualty insurance**: covers the **liability** to provide compensation to another party when the insured is at fault (negligent acts) or where compensation is required by law (can include liability for damage to property and injury to persons).

### Main Features of General Insurance Products

- **Shorter coverage periods** than for life insurance contracts (usually one year coverage).
- **Longer settlement**: payment of claims can extend over many years into the future for *long tail* classes such as liability or worker's compensation.
- **Random frequencies and severities**: insured can claim more than once, and amount of claims is (highly) variable.
- **No (or very high) upper bounds for outcomes**.
- **Risk of large claims** arising from one rare/unpredictable event, e.g. cyclone, fire, or earthquake: **catastrophe risk**.

## Actuarial Modelling: Frequency and Severity

### Frequency (or Occurrence)

On a general insurance policy, it is often possible to claim more than once. We call **frequency** the number of claims. Typical models (distributions) for frequency include:
- **Binomial**: variance smaller than the expectation: $\textcolor{blue}{npq} < np$
- **Poisson**: variance equals the expectation: $\textcolor{blue}{Var[X]}=E[X]=\lambda$
- **Negative Binomial**: variance can be bigger than the expectation: $r(1-p)/p^2 > r/p$ for $p<1/2$.

### Example 9.1

Using the following claims data, estimate the Poisson parameter $\lambda$.

| **Number of claims** | **Number of drivers** |
|----------------------|-----------------------|
| 0                    | 89,235                |
| 1                    | 2,321                 |
| 2                    | 300                   |
| 3                    | 0                     |
| 4                    | 2                     |
| 5                    | 1                     |
| 6 or more            | 0                     |

### Solution

Remember from Week 2, a good estimator for $\lambda$ is $\widehat{\lambda} = \bar{X}$. Here the total number of claims is:

$$
89235 \times 0 + 2321 \times 1 + 300 \times 2 + 0 \times 3 + 2 \times 4 + 1 \times 5 = 2934
$$

The total number of drivers is 91,859, so that the sample mean $\bar{X}$ (of number of claims per driver) is:

$$
\bar{X} = \frac{2934}{91859} = 0.03194
$$

And this is our estimate:

$$
\lambda^* = 0.03194
$$

## Poisson Process

- There is a neat link between the Exponential($\lambda$) and Poisson($\lambda$) distributions.
- Consider that in a given period of time, certain events (e.g. insurance claims) can occur.
- If the time between any two events has an Exponential($\lambda$) distribution (with mean $1/\lambda$), and if events arise independently of each other, then: the number of events per $t$ unit(s) of time has a Poisson $(t\lambda)$ distribution.
- When this is the case, we say that those events (e.g. insurance claims) arise according to a **Poisson Process**.


### Example 9.2

You just made a claim on your motor vehicle insurance policy. The claims you make per year arise as a Poisson Process with $\lambda = 0.5$. Determine the expected time to the next claim and the probability that you will have a claim in the next 6 months.

#### Solution

- Expected time to the next claim is:
  
$$
\frac{1}{0.5} = 2 \text{ years}
$$

- Probability that you will have at least one claim in the next 6 months is:
  
$$
1 - e^{-0.5 \times 0.5} = 0.2212
$$

## Actuarial Modelling of Severity

- **Severity** refers to the **size** of claims. Some common choices include distributions we have seen before: Log-Normal, Gamma and Weibull.
- Often in GI one uses **Generalised Linear Models (GLMs)** because they allow for the easy inclusion of risk factors in the modelling. Such models encompass many distributions, continuous and discrete: Normal, Gamma, inverse Gaussian, Poisson, Binomial, and others.
- Often, the probability of no claim is high, so that these distributions describe the cost of a claim, *given* a claim occurred (or given its cost was strictly positive).

## Combining Frequency and Severity

- Denote the number of claims by $N$ (a random variable) and the loss random variable for the $i^{th}$ claim by $X_{i}$ (assumed independent, and independent of $N$), for $i=1,2,\ldots, N$.
- This is new for us: we have a series of random variables $X_1, X_2, \ldots, X_N$, where their number $N$ is itself random!
- The **total** claim payments is denoted by $S$ (often called the *aggregate loss*):
  
$$
S = X_{1} + X_{2} + \ldots + X_{N} = \sum_{i=1}^{N} X_{i}
$$

### Aggregate loss: $E[S]$ and $\text{Var}[S]$

- For two random variables $S, N$, we have:
  
$$
E[S] = E[E[S | N]], \qquad \text{Var}[S] = E[\text{Var}[S|N]] + \text{Var}[E[S|N]]
$$

- We then have:
  
$$
E[S] = E\left[\sum_{i=1}^{N} X_{i}\right] = E \left[ E\left[\sum_{i=1}^{N} X_{i} \Big{|} N\right] \right] = E[N \cdot E[X_i]] = E[N] \cdot E[X_i]
$$

$$
\text{Var}[S] = E[\text{Var}[S|N]] + \text{Var}[E[S|N]] = E[N \cdot \text{Var}[X_i]] + \text{Var}[N \cdot E[X_i]] = E[N] \text{Var}[X_i] + \text{Var}[N] (E[X_i])^2
$$


## Deductibles

### What is a Deductible?

- Many insurance policies have a **deductible**: the policyholder must pay the first part of any loss (up to a fixed amount $d$).
- If $S$ is the total loss, this means the **insured** will pay:
  
$$
\begin{cases}
S, & \text{for } S \leq d \\
d, & \text{for } S > d
\end{cases}
$$

- The **insurer** will pay the rest:
  
$$
Y = \begin{cases}
0, & \text{for } S \leq d \\
S - d, & \text{for } S > d
\end{cases}
$$

- We are interested in $E(Y)$.

### Pricing with a Deductible

- Assume $S \geq 0$ is a continuous random variable. Then:
  
$$
\Pr[Y = 0] = \Pr[S \le d], \text{ and} \\
f_Y(y) = f_S(y + d) \text{ for } y > 0.
$$

- Hence:
  
$$
E[Y] = 0 \cdot \Pr[Y = 0] + \int_0^\infty y f_Y(y) dy = \int_0^\infty y f_S(y + d) dy
$$

### Example

- If you don't like having $f_S(y + d)$, by a change of variable:
  
$$
y + d = s \quad \iff \quad y = s - d
$$

$$
E[Y] = \int_{d}^{\infty} (s - d) f_{S}(s) ds = \int_{d}^{\infty} s f_{S}(s) ds - d \int_{d}^{\infty} f_{S}(s) ds = \int_{d}^{\infty} s f_{S}(s) ds - d (1 - F_{S}(d))
$$

### Example

- Let $S \sim$ Exponential($\beta$), then:
  
$$
E[Y] = \int_0^\infty y f_S(y + d) dy = \int_{0}^{\infty} y \beta e^{-\beta y} e^{-\beta d} dy = e^{-\beta d} \int_{0}^{\infty} y \beta e^{-\beta y} dy = e^{-\beta d} \frac{1}{\beta}
$$

- Does this formula make sense?

## Premium Rating

### Principle of Equivalence

- The **Principle of Equivalence** is also relevant in General Insurance, although its implementation is different. Recall:
  
$$
\textbf{EPV of premiums} = \textbf{EPV of claims + EPV of expenses}
$$

- Many assumptions must be made to compute the EPV of the claims (see CAS ratemaking principles for general guidelines).

### Premium Rating: Example 9.4

- Number of claims (per year) on an insurance policy has a $\text{Poisson}(0.1)$ distribution and the size of the claims have a $\text{Log-normal}(\mu=7.5, \sigma=0.06)$ distribution.
- Claims occurring during the policy year are assumed settled and paid exactly one year from the date the policy is sold (this is a customary assumption).
- Initial expenses are \$100.
- Interest rate is 7\% p.a.

Under the Principle of Equivalence, what is the premium for this policy?

### Solution

- Let $r$ denote the annual effective interest rate, and let $C$ denote the expenses. Based on the Principle of Equivalence, the premium is:
  
$$
P = \frac{E\left[ S \right]}{\left( 1 + r \right)} + C = \frac{E\left[ X \right] E\left[ N \right]}{\left( 1 + r \right)} + C
$$

- The expectations of the frequency and severity are:
  
$$
E\left[ N \right] = 0.1, \text{ and } E\left[ X \right] = e^{7.5 + \frac{1}{2} 0.06^{2}} = 1811.3
$$

- The premium including expenses will then be:
  
$$
\frac{0.1 \times 1811.3}{1.07} + 100 = \$269.3
$$


### CAS ratemaking principles

Taken from [CAS ratemaking principles](https://www.casact.org/sites/default/files/2021-05/Statement-Of-Principles-Ratemaking.pdf):

- **Principle 1**: A rate is an estimate of the expected value of **future** costs.

  (Ratemaking is prospective because the property and casualty insurance rate must be developed prior to the transfer of risk.)

- **Principle 2**: A rate provides for **all** costs associated with the transfer of risk.

  (Ratemaking should provide for all costs so that the insurance system is financially sound.)

- **Principle 3**: A rate provides for the costs associated with an **individual** risk transfer.

  (Ratemaking should provide for the costs of an individual risk transfer so that equity among insureds is maintained. When the experience of an individual risk does not provide a credible basis for estimating these costs, it is appropriate to consider the aggregate experience of similar risks. A rate estimated from such experience is an estimate of the costs of the risk transfer for each individual in the class.)

- **Principle 4**: A rate is reasonable and not excessive, inadequate, or unfairly discriminatory if it is an actuarially sound estimate of the expected value of all future costs associated with an individual risk transfer.

  (Ratemaking produces cost estimates that are actuarially sound if the estimation is based on Principles 1, 2, and 3. Such rates comply with four criteria commonly used by actuaries: reasonable, not excessive, not inadequate, and not unfairly discriminatory.)

## Unearned Premiums

### Unearned Premiums

- Premium is revenue only once coverage has been provided.
- Amount of the premium covering the policy year that occurs after the end of the accounting period (for future coverage) is called the **unearned premium**.
- A provision for unearned premium is made in the balance sheet (liability).
- Premiums taken into profit are the premiums received minus the change in the unearned premium provision - these are the **earned premiums**, corresponding to coverage actually provided during that accounting year.

### Calculations

$$
\text{Earned premium} = \text{Premiums Received} + \text{Unearned Premium at the Start} - \text{Unearned Premium Provision at the End}
$$

- Nowadays, actual premium policy dates are known and can easily be processed by computers, so calculations of unearned premiums can be done in an exact way.
- Sometimes (especially in the past), only aggregate data is available. In this case, approximations are required.

### Example 9.5

Annual premiums received by month for a class of insurance business during the year are listed as follows:

| **Month** | **Premiums received** |
|-----------|-----------------------|
| January   | \$112,234             |
| February  | \$60,345              |
| March     | \$54,780              |
| April     | \$115,200             |
| May       | \$80,900              |
| June      | \$150,755             |
| July      | \$16,340              |
| August    | \$50,234              |
| September | \$112,600             |
| October   | \$90,765              |
| November  | \$112,400             |
| December  | \$212,000             |

- The company has a 31 December financial year.
- Assume that premiums were paid on average at the mid-point of each month.
- Determine the unearned premium provision at the end of the financial year.

### Unearned Premiums - Solution

| **Month**   | **Premiums** | **Unearned Fraction as 24ths** | **Unearned Premium** |
|-------------|--------------|--------------------------------|----------------------|
| January     | \$112,234    | 1                              | \$4,676              |
| February    | \$60,345     | 3                              | \$7,543              |
| March       | \$54,780     | 5                              | \$11,413             |
| April       | \$115,200    | 7                              | \$33,600             |
| May         | \$80,900     | 9                              | \$30,338             |
| June        | \$150,755    | 11                             | \$69,096             |
| July        | \$16,340     | 13                             | \$8,851              |
| August      | \$50,234     | 15                             | \$31,396             |
| September   | \$112,600    | 17                             | \$79,758             |
| October     | \$90,765     | 19                             | \$71,856             |
| November    | \$112,400    | 21                             | \$98,350             |
| December    | \$212,000    | 23                             | \$203,167            |
| **Total**   |              |                                | \$650,043            |

## Outstanding Claims

### Outstanding Claims

- The settlement of claims is much more complicated in GI than in Life Insurance. All sorts of delays can occur:
  - between **occurrence** (of the insurance event) and **reporting** to the insurance company,
  - between **reporting** and **payment(s)**,
  - more generally, between **occurrence** and **settlement** (this may take years or even decades for long-tail classes).

- At the end of a coverage period, a big portion of the payments are **yet to be made**. Money must be set aside for those: **reserves for outstanding claims liabilities**.

### Run-Off triangle example

Example 9.6: **Run-off triangle actual claim payments** (Hossack et al., 1999 - Table 10.2.1 p208)

| **Accident Year** | 1   | 2   | 3   | 4   | 5  | 6  |
|-------------------|-----|-----|-----|-----|----|----|
| 2015              | 90  | 120 | 100 | 110 | 80 | 0  |
| 2016              | 130 | 150 | 80  | 100 | 140|    |
| 2017              | 140 | 150 | 150 | 160 |    |    |
| 2018              | 160 | 80  | 180 |     |    |    |
| 2019              | 120 | 140 |     |     |    |    |
| 2020              | 110 |     |     |     |    |    |


- Each year of new business is referred to as **accident year** (year of origin). For each accident year, claims are settled in future **development years**.
- Estimating outstanding claims liabilities: **completing the triangle into a rectangle**.

### Outstanding claims liabilities

- Many methods exist, here we briefly introduce the common **Chain-Ladder** method.
- Define the Run-Off triangle of **cumulative claims**:
  
| **Accident Year** | 1   | 2   | 3   | 4   | 5  | 6  |
|-------------------|-----|-----|-----|-----|----|----|
| 2015              | 90  | 210 | 310 | 420 | 500| 500|
| 2016              | 130 | 280 | 360 | 460 | 600|    |
| 2017              | 140 | 290 | 440 | 600 |    |    |
| 2018              | 160 | 240 | 420 |     |    |    |
| 2019              | 120 | 260 |     |     |    |    |
| 2020              | 110 |     |     |     |    |    |



### The Chain Ladder method

The central idea is that we assume a regular development pattern:

$$
C_{i,j} \times f_{j} \approx C_{i, j+1}
$$

- $i$ is the accident year, $j$ is the development year.
- $C_{i,j}$ are the cumulative payments for accident year $i$ and development year $j$: in the top left triangle these are actual payments; in the bottom right triangle these are projections.
- $f_{j}$ are the development factors (from year $j$ to year $j+1$), which **do not depend on the accident year**.

### The Chain Ladder method (cont'd)

- It is based on strong assumptions:
  - the development pattern must be identical across accident years (but: legal changes, coverage changes, evolution of risks/consumer behaviour, etc.),
  - the speed of settlement must be constant (but: IT systems updates, catastrophic events, etc.).

- In its most basic form (covered here) this model is `rough`, but over time actuaries developed many extensions to improve it.

### Estimation of $f_j$, denoted $\hat{f}_j^{CL}$

One can calculate empirical factors from the cumulative triangle:

| **Accident Year** | 1       | 2     | 3     | 4     | 5   | 6  |
|-------------------|---------|-------|-------|-------|-----|----|
| 2015              | 2.333   | 1.476 | 1.355 | 1.190 | 1.000|    |
| 2016              | 2.154   | 1.286 | 1.278 | 1.304 |     |    |
| 2017              | 2.071   | 1.517 | 1.364 |       |     |    |
| 2018              | 1.500   | 1.750 |       |       |     |    |
| 2019              | 2.167   |       |       |       |     |    |
| 2020              |         |       |       |       |     |    |
| **Simple Avg**    | 2.045   | 1.507 | 1.332 | 1.247 | 1.000|    |
| **Weighted Avg**  | 2       | 1.5   | 1.333 | 1.25  | 1   |    |


- **Weighted averages** are preferred, but they are often judgmentally chosen/adjusted by the actuary.

### Example

Develop the cumulative triangle:

| **Accident Year** | 1   | 2   | 3   | 4   | 5  | 6  |
|-------------------|-----|-----|-----|-----|----|----|
| 2015              | 90  | 210 | 310 | 420 | 500| 500|
| 2016              | 130 | 280 | 360 | 460 | 600| 600|
| 2017              | 140 | 290 | 440 | 600 | 750| 750|
| 2018              | 160 | 240 | 420 | 560 | 700| 700|
| 2019              | 120 | 260 | 390 | 520 | 650| 650|
| 2020              | 110 | 220 | 330 | 440 | 550| 550|


### Example (cont'd)

From the cumulative triangle, find the incremental claims:

| **Accident Year** | 1   | 2   | 3   | 4   | 5  | 6  | **Total** |
|-------------------|-----|-----|-----|-----|----|----|----------|
| 2015              | 90  | 120 | 100 | 110 | 80 | 0  | -        |
| 2016              | 130 | 150 | 80  | 100 | 140| 0  | 0        |
| 2017              | 140 | 150 | 150 | 160 | 150| 0  | 150      |
| 2018              | 160 | 80  | 180 | 140 | 140| 0  | 280      |
| 2019              | 120 | 140 | 130 | 130 | 130| 0  | 390      |
| 2020              | 110 | 110 | 110 | 110 | 110| 0  | 440      |


- So in this case, the total reserves are $0 + 150 + 280 + 390 + 440 = 1260$.

## To discount or not to discount?

- In Australia, discounting is allowed, but regulation around the world often does not allow discounting in calculating the reserves, and for a number of reasons.
- **Bad risk incentive**: discounting implies `earning interest` on the reserves; there could then be an incentive to assume interest rates that are too high (in order to minimize reserves), followed by unreasonable risk-taking to achieve this return.
- **Accounting**: interest on reserves is income that is not insurance-related, but is financial. One could argue this (expected) income should appear elsewhere, and not be mixed with the insurance accounting.

### Reserves Discounting: Example

- Assume the same Run-Off Triangle as previously used.
- Assume a fixed interest rate of 5.0\% per year, effective.
- As at 31st December 2020, determine the discounted outstanding claims provision (reserves) assuming claim payments are made on average in the middle of the year of payment.
- Compare those reserves to the `not-discounted` amount.

### Reserves Discounting: Solution

- The present value of the expected outstanding claim payments that will be made in 2021 (middle of the year) is:
  
$$
\frac{110 + 130 + 140 + 150}{\left( 1.05 \right)^{0.5}} = 517.23
$$

- In 2022: $(110 + 130 + 140)/(1.05)^{1.5} = 353.18$
- In 2023: $(110 + 130)/(1.05^{2.5}) = 212.44$
- In 2024: $110/(1.05)^{3.5} = 92.73$

- The sum is: $1,175.58$, of course lower than without discounting.

## Example 9.7

Run-off triangle as at 31 December 1999 shows estimates of the expected value of outstanding claims. All claims are settled by the end of development year 4.

| **Year of Origin** | 0     | 1      | 2      | 3      | 4      |
|--------------------|-------|--------|--------|--------|--------|
| 1995               | 580,222 | 466,679 | 240,001 | 133,601 | 54,912 |
| 1996               | 494,534 | 499,293 | 192,227 | 159,007 | **67,185** |
| 1997               | 551,136 | 509,075 | 238,245 | **196,972** | **82,060** |
| 1998               | 648,031 | 664,188 | **309,630** | **240,582** | **100,229** |
| 1999               | 746,003 | **778,777** | **378,183** | **293,848** | **122,420** |


- Different numbering convention for the development years.

The following interest rates are used to discount the expected value of outstanding claims in order to determine the outstanding claims provision as at 31 December 1999.

| **Time to payment (years)** | **Effective interest rate p.a.** |
|-----------------------------|----------------------------------|
| 0.5                         | 5.00\%                           |
| 1.5                         | 5.50\%                           |
| 2.5                         | 5.90\%                           |
| 3.5                         | 6.50\%                           |

- Determine the discounted outstanding claims provision assuming claim payments are made on average in the middle of the year of payment, i.e. 30 June.

### Solution

- For year of origin 1996 the present value of the expected outstanding claim payments is:
  
$$
\frac{67,185}{\left( 1.05 \right)^{0.5}} = 65,566
$$

- For year of origin 1997 the present value of the expected outstanding claim payments is:
  
$$
\frac{196,972}{\left( 1.05 \right)^{0.5}} + \frac{82,060}{\left( 1.055 \right)^{1.5}} = 267,952
$$

- For year of origin 1998 the present value of the expected outstanding claim payments is:
  
$$
\frac{309,630}{\left( 1.05 \right)^{0.5}} + \frac{240,582}{\left( 1.055 \right)^{1.5}} + \frac{100,229}{\left( 1.059 \right)^{2.5}} = 611,031
$$

- For the final year of origin, 1999, the present value of the expected outstanding claim payments is:
  
$$
\frac{778,777}{\left( 1.05 \right)^{0.5}} + \frac{378,183}{\left( 1.055 \right)^{1.5}} + \frac{293,848}{\left( 1.059 \right)^{2.5}} + \frac{122,420}{\left( 1.065 \right)^{3.5}} = 1,461,824
$$

- The value of the discounted outstanding claims is the sum of the present values of the expected outstanding claim payments in the four years of origin:
  
$$
65,566 + 267,952 + 611,031 + 1,461,824 = 2,406,375
$$

