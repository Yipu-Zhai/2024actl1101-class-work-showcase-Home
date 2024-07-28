## Life Insurance and Life Annuity

There are many types of Life Insurance products (see Sherris Section 8.3), with the most common being:

- **Whole of Life**: Pays a benefit at death, regardless of when death occurs.
- **Term Insurance**: Pays a benefit at death, but only if death occurs in a certain period.
- **Endowment**: Pays a benefit at death if death occurs in a certain period, but also pays the benefit if the life is alive at the end of the period.


## Term Insurance - Claim Payments

- $T(x)$ is the future lifetime (a continuous random variable) for a life $(x)$.
- $X$ is the age-at-death (also a continuous random variable).
  
$$
T(x) = X - x
$$
- Will require probability of this random variable taking values $0,1,\cdots,n-1$.
  - $x+k$ age last birthday, with integer $x+k$.

## Term Insurance - Benefit Payment

Assume the insured life is aged $x$ at purchase, the death benefit is of amount $S$, and it is paid at the end of the year of death, but only if death occurs within $n$ years of purchase.
Assume an annual (effective) rate of interest $i$.
- If death occurs in the first year of the policy, when the life is aged $x$, then the present value of the death benefit would be:

$$
\frac{S}{(1+i)} = Sv
$$
  
- If death occurs when the life is aged $x+1$ then the present value of the benefit would be:
  
$$
\frac{S}{(1+i)^2} = Sv^2
$$

In general, if death occurs when the life is aged $x+k$ last birthday where $k=0,1,2,\ldots n-1$ then the **present value of the benefit payment** at the end of the year of death would be:

$$
\text{PV[Payment]} = 
\begin{cases}
Sv^{k+1} & \text{for } k=0,1,2,\ldots, n-1 \\
0 & \text{for } k \geq n
\end{cases}
$$

## Term Insurance - EPV of Claim Payments

What are the associated probabilities with the values of the present value of the payment?

Let $K(x)$ be the discretized future lifetime random variable for age $x$ (i.e., $K(x) = \lfloor T(x) \rfloor$). Then:

$$
\text{PV}[Payment] = 
\begin{cases}
Sv^{k+1} 	& \text{with probability Pr} [K(x) = k] \\
            & \text{for } k = 1,2,3,\ldots,n-1 \\
0 & \text{with probability Pr} [K(x) \geq n] = ~_{n} p_x
\end{cases}
$$

What is $\Pr[K(x) = k]$?


```math
\Pr[K=k] = \Pr[k \leq T(x) < k+1] = _{k}p_{x}q_{x+k}
```



## Expected Present Value of Benefit Payment

The **Expected Present Value** of the benefit payment for this term insurance is then:

```math
\sum_{k=0}^{n-1} S v^{k+1} \cdot _{k}p_{x}q_{x+k} = S \cdot \sum_{k=0}^{n-1} v^{k+1} \cdot _{k}p_{x}q_{x+k} = S \cdot A_{x:\overline{n}|}^{1}
```

Where $A_{x:\overline{n}\rvert}^{1}$ is standard actuarial notation (for the expected PV of a term life insurance paying a benefit of 1, and covering the next $n$ years of a life aged $x$).

### Example 8.5

Determine the expected present value of the claim payments for a 5-year term insurance on a life aged 20 with a sum insured of $100,000 using the following mortality probabilities and a 6% p.a. effective interest rate.

#### Mortality Probabilities

| Age  | $q_{\text{age}}$      |
|------|----------------------|
| 20   | 0.00192              |
| 21   | 0.00181              |
| 22   | 0.00160              |
| 23   | 0.00138              |
| 24   | 0.00118              |

#### Solution

To calculate the EPV of 1 payable on death within $n$ years:

```math
A_{20:\overline{5}|}^{1} = \sum_{k=0}^{4}v^{k+1}\left( _{k}p_{20}q_{20+k}\right)
```

where:
- $v^{k+1} = \left( \frac{1}{1.06}\right)^{k+1}$
- $\_{k}p_{20}$ is assumed as follows, with $\_{0}p_{20}=1$

#### Detailed Calculations

| Age(x+k) | $q_{x+k}$    | $k$  | $v^{k+1}$ | $\_{k}p_{x}$| $\_{k}p_{x} q_{x+k}$       |
|----------|--------------|------|-----------|-------------|----------------------------|
| 20       | 0.00192      | 0    | 0.94340   | 1.00000     | 0.00192                    |
| 21       | 0.00181      | 1    | 0.89000   | 0.99808     | 0.00181                    |
| 22       | 0.00160      | 2    | 0.83962   | 0.99627     | 0.00159                    |
| 23       | 0.00138      | 3    | 0.79209   | 0.99468     | 0.00137                    |
| 24       | 0.00118      | 4    | 0.74726   | 0.99331     | 0.00117                    |


The EPV of the claim payments for a sum insured of 100,000 is then:

```math
100,000 \cdot A_{20:\overline{5}|}^{1} = 672.06
```

### Life Annuities

- A **life annuity** is a stream of regular payments, paid as long as a life is alive.
- Consider a life aged $x$. Call $P_k$ the payment they receive at time $k$, for $k=0,1,2,\ldots$
- The Expected Present Value of a life annuity due (paid in advance) of 1 per period to this life aged $x$ is:

```math
\ddot{a}_{x} = \mathbb{E} [ \text{PV}(P_0) + \text{PV}(P_1) + \ldots + \text{PV}(P_{\omega-x-1})] = \sum_{k=0}^{\omega-x-1}v^k \cdot _{k}p_{x}
```


Furthermore:

```math
\ddot{a}_{x} = 1 + \sum_{k=1}^{\omega -x-1} v^k \cdot _{k}p_{x} = 1 + \sum_{k=1}^{\omega -x-1} v \cdot v^{k-1} \cdot p_{x} \cdot _{k-1}p_{x+1} = 1 + v \cdot p_{x} \left[ \sum_{k=0}^{\omega -x-2} v^k \cdot _{k}p_{x+1} \right] = 1 + v \cdot p_{x} \cdot \ddot{a}_{x+1}
```

- Note that $\ddot{a}_{x} = 1 + a_x.$ Do you see why?

If the payments are restricted to $n$ payments maximum:

```math
\ddot{a}_{x:\overline{n}|} = \sum_{k=0}^{n-1} v^k \cdot _{k}p_{x} = 1 + a_{x:\overline{n-1}|}
```

### Principle of Equivalence

- The `actuarially fair' **Principle of Equivalence** states that:
  
```math
\text{EPV of premiums} = \text{EPV of claims} + \text{EPV of expenses}
```

- A complication in Life Insurance is that annual premiums $P$ are only paid while a life is alive, so that the expected present value of $n$ premiums $P$, for a life age $x$, is:

```math
P \cdot \sum_{k=0}^{n-1} v^{k} \left( _{k}p_{x} \right) = P \cdot a_{x:\overline{n}|}
```

- Note: premium payments are always made at the beginning of the cover, hence $a\_{x:\overline{n}\|}$

- Present value of the premium due at age $x+k$ is:

```math
\begin{cases}
Pv^{k} & \text{for } k=0,1,2,\ldots n-1 \\
0 & \text{for } k\geq n
\end{cases}
```

- For a life aged $x$, the probability that they will be alive at age $x+k$ and will pay the premium $\_{k}p_{x}$

## Recurrence Relations

Recurrence relations for the expected present value of benefits for an $n$ year term insurance on a life aged $x$. Let $\_{t}B_{x:\overline{n}\|}$ be the expected present value of benefits at age $x+t$:

If the life dies during the year, with probability $q_{x+t}$, then the benefit of $S$ is paid at the end of the year. The expected present value of the benefits will then be equal to $S$ since no future payments are made once the life has died.

- If the life survives to the end of the year, with probability $p_{x+t}$, then the expected present value of the benefits will equal that for a life aged $x+t+1$, this is just $\_{t+1}B\_{x:\overline{n}\|}$.


- EPV at the start of the year - divide the end of year value by $1+i$:

```math
_{t}B_{x:\overline{n}|} = \frac{q_{x+t}S + p_{x+t} \left( _{t+1}B_{x:\overline{n}|} \right)}{1+i}
```

- For the $n$ year term insurance on a life aged $x$, at age $x+n$ the expected value of the benefit will be zero since the benefit is only paid up to age $x+n$.

- At $t=n$ we have $\_{n}B_{x:\overline{n}\|}=0$.

Over the final year of the policy:

```math
_{n-1}B_{x:\overline{n}|} = \frac{q_{x+n-1}S + p_{x+n-1} \cdot 0}{1+i} = \frac{q_{x+n-1}S}{1+i}
```

- Repeating the recurrence:

```math
_{n-2}B_{x:\overline{n}|} = \frac{q_{x+n-2}S + p_{x+n-2} \frac{q_{x+n-1}S}{1+i}}{1+i} = q_{x+n-2} \frac{S}{1+i} + p_{x+n-2} q_{x+n-1} \frac{S}{(1+i)^{2}}
```

- At age $x$ we have:

```math
_{0}B_{x:\overline{n}|} = \frac{q_{x}S + p_{x} \left( _{1}B_{x:\overline{n}|} \right)}{1+i} = S \sum_{k=0}^{n-1} v^k \left( _{k}p_{x} q_{x+k} \right)
```

### Example 8.6 & 8.7

Use the Principle of Equivalence to determine the annual premium for a 5-year term insurance on a 20-year-old male with a sum insured of 100,000 using the following mortality probabilities and a 6% p.a. effective interest rate. Initial expenses are 0.5% of the sum insured and renewal expenses are 100 per premium payment.

| **age** | **$q_{\text{age}}$** |
|---------|----------------------|
| 20      | 0.00192              |
| 21      | 0.00181              |
| 22      | 0.00160              |
| 23      | 0.00138              |
| 24      | 0.00118              |

### Solution

- We must find the EPV of premiums, so we must find:

```math
a_{20:\overline{5}|} = \sum_{k=0}^{n-1} v^k \left( _{k}p_{20} \right)
```


| **age(x+k)** | **$q_{x+k}$** | **k** | **$v^k$** |**$\_{k}p_x$**|
|--------------|---------------|-------|-----------|--------------|
| 20           | 0.00192       | 0     | 1.00000   | 1.00000      |
| 21           | 0.00181       | 1     | 0.94340   | 0.99808      |
| 22           | 0.00160       | 2     | 0.89000   | 0.99627      |
| 23           | 0.00138       | 3     | 0.83962   | 0.99468      |
| 24           | 0.00118       | 4     | 0.79209   | 0.99331      |
      

1. Let $P$ denote the annual premium. EPV is:

```math
P a_{20:\overline{5}|} = P \times 4.45021.
```

2. EPV of the claims payment is:

```math
100000 a_{20:\overline{5}|} = 100000 \times 0.0067206 = 672.06.
```

3. Expected present value of the sum of initial and renewal expenses is:

```math
0.005 \times 100000 + 100 a_{20:\overline{5}|} = 500 + 100 \times 4.45021 = 945.02.
```

- Equating [1] = [2] + [3] (principle of equivalence):

```math
P = \frac{672.06 + 945.02}{4.45021} = 363.37.
```


### Valuation of Policy Liabilities

Policy value of a liability for a life insurance policy is the

```math
\text{EPV of future claims and expenses} - \text{EPV of future premiums}.
```

Denote the value of this reserve by $\_{t}V_{x:\overline{n}|}$ the EPV of the policy liability 
- at age $x+t$ (CONDITIONAL on survival to age $x+t$)
- for the term insurance on a life aged $x$ for a term of $n$ years 
- with sum insured payable at the end of the year of death

### Term life insurance

We have:
```math
{}_{t}V_{x:\overline{n}|} = S \cdot {}_{t+1} A^1_{x+t:\overline{n-t}|} - (P-E) \cdot \ddot{a}_{x+t:\overline{n-t}|}
```
(by definition)

```math
= v \left[ q_{x+t} \cdot S + p_{x+t} \cdot {}_{t+1}V_{x:\overline{n}|} \right] -(P-E)
```
(noting that there are only two possible outcomes over the next year)

Note that we must have:
```math
{}_{0}V_{x:\overline{n}|} = {}_{n}V_{x:\overline{n}|} = 0.
```

### Example 8.10

An insurance company sells 5 year term insurances on 20 year old males with a sum insured of 100,000 for a premium of 363.37. Assume the following mortality probabilities, a 6% p.a. effective interest rate, initial expenses of 0.5% of the sum insured and renewal expenses of 100 per premium payment.

| **Age** | **$q_{x}$** |
|---------|-------------|
| 20      | 0.00192     |
| 21      | 0.00181     |
| 22      | 0.00160     |
| 23      | 0.00138     |
| 24      | 0.00118     |

Determine the expected value of the policy liability for this term insurance as at the end of each year for the five years of the policy term using a recursive formula.

### Solution

The recurrence formula:
```math
{}_{t}V_{x:\overline{n}|} = \frac{q_{x+t} S + p_{x+t} \left[ {}_{t+1}V_{x:\overline{n}|} \right]}{(1+i)} - (P-E)
```

Summarized in the following table:

| **Age** | **k** | **$q_x$** | **$\_{k}V_{x:\overline{n}\|}$** |
|---------|-------|-----------|-------------------------------|
| 20      | 0     | 0.00192   | 0.00                          |
| 21      | 1     | 0.00181   | -443.68                       |
| 22      | 2     | 0.00160   | -372.80                       |
| 23      | 3     | 0.00138   | -276.43                       |
| 24      | 4     | 0.00118   | -152.05                       |
| 25      | 5     | --        | 0.00                          |


### Sign of the Reserves

- In the example, the expected value of the policy liability is **negative**!
  - The liability is effectively an **asset** for the life insurance company (How? Why?)
    - Since initial expenses are effectively loaned to the policyholder, this is like an asset that is repaid from the premium - this makes a policy look like an asset in the early years.
    - Also the probability of death is **decreasing** over this age range - level premiums are **less than** the expected cost of death cover in the early years.
- Example 8.8 has positive reserves for low expenses.
- In general, the magnitude of expenses is small enough that reserves are positive.






## References

### Introduction Level
- **Principles of Actuarial Science** by Michael Sherris. 2010 Edition. Publisher: Cengage Learning. ISBN: 0170188213, APN: 9780170188210. Coverage includes Chapter 8. Ideal for those beginning their journey in actuarial studies.

### Advanced Level
- **Actuarial Mathematics for Life Contingent Risks** by Dickson, C.M.D., Hardy, M.R., Waters, H.R. 2020 Edition. Publisher: Cambridge University Press. ISBN: 978-1-108-47808-3. Covers Chapters 1-8, focusing on deep actuarial methods and applications.


