[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters µ = 178 cm and σ = 7.7 cm for men. Let's create a python object to represent a normal distribution with mean 178.0 and sigma 7.7.

## Import Libraries

```python
import scipy.stats
```

## Create Distribution Object

```python
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
```

In order to join Blue Man Group, you have to be male between 5’10” (177.8 cm) and 6’1” (185.42 cm). The percentage of the US male population that falls within this range can be estimated by using the cumulative distribution function (CDF) of our normal distribution. Specifically we need to take the CDF value for 185.42 cm and subtract the CDF value for 177.8 cm.

## Determine Result

```python
dist.cdf(185.42) - dist.cdf(177.8)
```

[Output] 0.3427468376314737

This result tells us that roughly 34% of the US male population is between 5'10" and 6'1" tall.
