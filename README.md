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
<img src="https://render.githubusercontent.com/render/math?math=H0: R_{1},R_{2}...R_{n} are Unif(0,1)">

<img src="https://render.githubusercontent.com/render/math?math=\chi_{0}^{2} = \sum_{i=1}^{k}\frac{(O_{i}-E_{i})^2}{E_{i}}">

if <img src="https://render.githubusercontent.com/render/math?math=\chi_{0}^{2}<=\chi_{a,k-1}^{2}">, we fail to reject <img src="https://render.githubusercontent.com/render/math?math=H0">


###
