# Project 2 - Huang, Justin

## Problem Statement
How do we know if a random number generator (RNG) is 'good'? In this project we test a number of Unif(0,1) generators. We evaluate these RNG with formal statistical tests. The RNGs we will explore include:

* Numpy BitGenerator (PCG64)
* RANDU
* Middle Squares

The statistical tests we will use are:

* Chi Squared for goodness of fit (Uniforms)
* Means run test for independence
* Autocorrelation test for independence

In addition sometimes a simple eye test can give a lot of insight! 

## Background - Random Number Generators

### Numpy BitGenerator (PCG64)
This is the default RNG used in Python's numpy module. It is a PCG, which is short for permuted congruential generator. Developed in 2014, essentially it follows a linear congruential generator as a state-transition function, then uses permutation function as an output function.

### Randu
Randu is a linear congruential pseudorandom number generator of the Park–Miller type, and was developed in the 1960s. As mentioned in the course, drawbacks of the generator include correlation between points. In fact, each point lies in one of a set of 15 parallel planes 2^31 apart.

<img src="https://render.githubusercontent.com/render/math?math=V_{j+1} = 65539\cdot V_j\, \bmod\, 2^{31}">
<img src="https://render.githubusercontent.com/render/math?math=X_j = \frac{V_{j}}{2^{31}}">

### Middle Squares
The midsquares method was developed by Von Neumann in 1949. It is an arithmetic method that takes a seed number and generates the next number by taking the middle n digits of the seed number, and squaring it. In this case, we use n=4. Example (if n=4:

<img src="https://render.githubusercontent.com/render/math?math=X0 = 6100, X0^2 = 37*2100*00">
<img src="https://render.githubusercontent.com/render/math?math=X1 = 2100, X1^2 = 04*4100*00">
<img src="https://render.githubusercontent.com/render/math?math=R_{i}=\frac{X_{i}}{1000}">

and so on..

## Background - Statistical Tests

### Chi-Squared Goodness of Fit Test for Correlation
In this test we begin with a hypothesis that the numbers are uniform. The test statistic is chi squared0 which is calculated by dividing the numbers into n bins and counting how many numbers fall into the individual bins and comparing these to the expected amount in each bin. This chi squared0 is compared to the chi squared, which can be determined by the significance and degree of freedoms. From this we can determine if there is evidence that supports that the numbers are uniform.
<img src="https://render.githubusercontent.com/render/math?math=H0: R_{1},R_{2}...R_{n} "> are Unif(0,1)

<img src="https://render.githubusercontent.com/render/math?math=\chi_{0}^{2} = \sum_{i=1}^{k}\frac{(O_{i}-E_{i})^2}{E_{i}}">

if <img src="https://render.githubusercontent.com/render/math?math=\chi_{0}^{2}<=\chi_{a,k-1}^{2}">, we fail to reject <img src="https://render.githubusercontent.com/render/math?math=H0">


### Runs Test Means
In this test we begin with a hypothesis that the numbers are independent. The test statistic is Z0 which is calculated by the number of runs above and below the mean. This Z0 is compared to the z value, which can be determined by the significance level and the normal distribution. From this we can determine if there is evidence that supports that the numbers are independent.

<img src="https://render.githubusercontent.com/render/math?math=H0: R_{1},R_{2}...R_{n} "> are independent.

<img src="https://render.githubusercontent.com/render/math?math=E[B]=\frac{2*n1n2}{2} + 0.5">
<img src="https://render.githubusercontent.com/render/math?math=Var[B]=\frac{2*n1n2(2*n1n2-n}{n^{2}(n-1)}">
<img src="https://render.githubusercontent.com/render/math?math=Z0=\frac{B-E[B]}{\sqrt{Var(B)}}">

if <img src="https://render.githubusercontent.com/render/math?math=|Z0|<=z_{a/2}">, we fail to reject <img src="https://render.githubusercontent.com/render/math?math=H0">

### Autocorrelation
This test provides another way to determine independence by looking at correlation between consecutive numbers.

<img src="https://render.githubusercontent.com/render/math?math=H0: R_{1},R_{2}...R_{n} "> are independent.

<img src="https://render.githubusercontent.com/render/math?math=\rho=(\frac{12}{n-1}\sum_{k=1}^{n-1}R_{k}R_{1+k})-3">

<img src="https://render.githubusercontent.com/render/math?math=Z0=\frac{\rho}{\sqrt{Var(\rho)}}">

if <img src="https://render.githubusercontent.com/render/math?math=|Z0|<=z_{a/2}">, we fail to reject <img src="https://render.githubusercontent.com/render/math?math=H0">.




