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

## Background

### Numpy BitGenerator (PCG64)
This is the default RNG used in Python's numpy module. It is a PCG, which is short for permuted congruential generator. Developed in 2014, essentially it follows a linear congruential generator as a state-transition function, then uses permutation function as an output function.

### Randu
Randu is a linear congruential pseudorandom number generator of the Park–Miller type, and was developed in the 1960s. As mentioned in the course, drawbacks of the generator include correlation between points. In fact, each point lies in one of a set of 15 parallel planes 2^31 apart.

V_{j+1} = 65539\cdot V_j\, \bmod\, 2^{31}

X_j = \frac{V_{j}}{2^{31}}

### Middle Squares
The midsquares method was developed by Von Neumann in 1949. It is an arithmetic method that takes a seed number and generates the next number by taking the middle n digits of the seed number, and squaring it. In this case, we use n=4. Example:

If n=4:
X0 = 6100, X0^2 = 37*2100*00
X1 = 2100, X1^2 = 04*4100*00
and so on..

R_{i}=X_{i}/1000

## Statistical Tests used.
