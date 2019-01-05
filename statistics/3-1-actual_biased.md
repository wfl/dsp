[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>>

```python
import nsfg
import thinkstats2
import thinkplot

resp = nsfg.ReadFemResp()
pmf = thinkstats2.Pmf(resp.numkdhh, 'actual')
biased_pmf = BiasPmf(pmf, label='biased')
print('Mean (actual)', pmf.Mean())
print('Mean (biased)', biased_pmf.Mean())

thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased_pmf])
thinkplot.show(xlabel='number of children under 18 in the respondents households', ylabel='PMF')
```
python output: 
Mean (actual) 1.024205155043831
Mean (biased) 2.403679100664282

![PMF(biased)](https://github.com/wfl/dsp/tree/master/statistics/plots/p3e1_pmf2.png)

In the biased distribution, the respondents' households without children have zero probability, indicating they are excluded from the survey. Additionally, the portion of the biased distribution that has larger probabilities are associated with households with 2 or more children. This yields a mean of 2.404, which is at least 50% larger than the mean of the actual distribution (1.024).  


