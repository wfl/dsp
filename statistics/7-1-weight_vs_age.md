[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

>> REPLACE THIS TEXT WITH YOUR RESPONSE

```python
import first

import thinkstats2
import thinkplot

live, firsts, others = first.MakeFrames()
live = live.dropna(subset=['agepreg', 'totalwgt_lb'])

thinkplot.Scatter(live.agepreg, live.totalwgt_lb)
thinkplot.Show(xlabel="mother's age (years)", ylabel="total birth weight (lbs)", legend=False )

bins = np.arange(15, 48, 3)
indices = np.digitize(live.agepreg, bins)
groups = live.groupby(indices)

ages = [group.agepreg.mean() for i, group in groups]
cdfs = [thinkstats2.Cdf(group.totalwgt_lb) for i, group in groups]

for percent in [75, 50, 25]:
    weights = [cdf.Percentile(percent) for cdf in cdfs]
    label = '%dth' % percent
    thinkplot.Plot(ages, weights, label=label)

thinkplot.Show(xlabel="mother's age (years)", ylabel="total birth weight (lbs)")

Pearson_corr = thinkstats2.Corr(live.agepreg, live.totalwgt_lb)
Spearman_corr = thinkstats2.SpearmanCorr(live.agepreg, live.totalwgt_lb)
```

![age Vs weight scatterplot](https://github.com/wfl/dsp/tree/master/statistics/plots/p7e1_scatter.png)

The points in the scatter plot are aligned horizontaly, indicating a weak relationship between the birth weight and mother’s age.

![age Vs weight percentile](https://github.com/wfl/dsp/tree/master/statistics/plots/p7e1_percentile.png)

The plot shows that there is a positive linear relationship for mother's age ranging around 16 to 35 years old. There is a sign of negative relationship between these variables after the mother's age is greater than 35 years old. 

The Pearson's and Spearman's rank correlations are calculated to be 0.069 and 0.095. The low correlation verifies the weak linear relationship between the birth weight and mother’s age.