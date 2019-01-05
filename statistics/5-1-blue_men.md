[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> How many people are between 5'10" and 6'1"?

```python
import scipy.stats
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)

f510cm = 177.80
f61cm = 185.42
d = dist.cdf(f61cm)-dist.cdf(f510cm)
```

python output: d=0.3427468376314737

Around 34% of the U.S male population are between 5'10" and 6'1".


