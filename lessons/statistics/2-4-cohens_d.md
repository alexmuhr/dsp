[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

## Comparing Birth Weights

```python
import numpy as np
import nsfg
import thinkstats2

preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

firsts['totalwgt_lb'].mean() - others['totalwgt_lb'].mean()
```

[Output] -0.12476118453549034

This shows that there is a very small difference between the mean birth weight of first babies vs others.

```python
def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d
    
CohenEffectSize(firsts['totalwgt_lb'], others['totalwgt_lb'])
```

[Output] -0.088672927072602

Here we can see that Cohen's *d* is very small for these two groups. This shows that the difference between the mean weight of two groups is very small compared to their combined standard deviation. We can say that the weight difference between first babies and others is not especially significant.

## Comparing Pregnancy Length

```python
firsts['prglngth'].mean() - others['prglngth'].mean()
```

[Output] 0.07803726677754952

```python
CohenEffectSize(firsts['prglngth'], others['prglngth'])
```

[Output] 0.028879044654449883

Cohen's *d* for pregnancy length is even smaller than for birth weight! For both pregnancy length and birth weight there does not appear to be much difference at all between first babies and others.
