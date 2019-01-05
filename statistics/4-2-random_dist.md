[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

>> REPLACE THIS TEXT WITH YOUR RESPONSE

```python
import numpy as np
import thinkstats2
import thinkplot

sample = np.random.random(1000)

pmf = thinkstats2.Pmf(sample)
#thinkplot.Pmf(pmf, linewidth=1)
#thinkplot.Pmf(pmf, linewidth=0.5)
thinkplot.Pmf(pmf, linewidth=0.1)
thinkplot.show(xlabel='samples' , ylabel='PMF')

cdf = thinkstats2.Cdf(sample)
thinkplot.Cdf(cdf)
thinkplot.show(xlabel='samples' , ylabel='CDF')
```
Here are the PMF and CDF for the 1000 random numbers generated using the numpy.random.random . 

![PMF(linewid1)](https://github.com/wfl/dsp/tree/master/statistics/plots/p4e2_pmf1.png)
This PMF is hard to read because the linewidth in this plot is thick. So, the linewidth is reduced to 0.5 and 0.1, which are depicted in these 2 PMFs below. 

![PMF(linewid0.5)](https://github.com/wfl/dsp/tree/master/statistics/plots/p4e2_pmf2.png)

![PMF(linewid0.1)](https://github.com/wfl/dsp/tree/master/statistics/plots/p4e2_pmf3.png)

Notice the numbers in the x-axis aren't uniformly distributed within 0 to 1. Certain ranges of the numbers don't have enough samples generated. However, is the distribution correctly represented by this PMF? Let's look at the CDF below.

![CDF](https://github.com/wfl/dsp/tree/master/statistics/plots/p4e2_cdf.png)

The straight line in the CDF plot indicates the distribution is uniform.