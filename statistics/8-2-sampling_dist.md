[Think Stats Chapter 8 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77) (scoring)

>> REPLACE THIS TEXT WITH YOUR RESPONSE

```python
import thinkstats2
import thinkplot

def Estimate_expDist(lam, n, iters=1000):

    Ls = []
    Lms = []
    for _ in range(iters):
        xs = np.random.exponential(1.0/lam, n)
        L = 1 / np.mean(xs)
        Lm = np.log(2) / thinkstats2.Median(xs)
        Ls.append(L)
        Lms.append(Lm)
    
    return Ls, Lms

lam = 2
n = 10
Ls, Lms = Estimate_expDist(lam, n)
print('stderr L = RMSE L = ', RMSE(Ls, lam))

cdf_L = thinkstats2.Cdf(Ls, label="L")
print('90% CI for L = (', cdf_L.Percentile(5), ', ', cdf_L.Percentile(95), ')')

thinkplot.Cdf(cdf_L)
thinkplot.Show(xlabel="sample L", ylabel="CDF", title="Sampling distribution of the estimate L")
```

The standard error of the estimate L is 0.796, and the 90% confidence interval is (1.297,  3.555). The CDF of the estimated L is shown below:

![CDF Estimate L](https://github.com/wfl/dsp/tree/master/statistics/plots/p8e2_CDF.png)


```python
# Repeat the experiment with a few different values of n and make a plot of standard error versus n
ns = range(5,55,5)
stderr_Ls = []
for n in ns:
    Ls, Lms = Estimate_expDist(lam, n)
    stderr_Ls.append(RMSE(Ls, lam))
    cdf = thinkstats2.Cdf(Ls)
    print('90% CI for n =', n, ' is (', cdf.Percentile(5), ', ', cdf.Percentile(95), ')')
        
thinkplot.Plot(ns, stderr_Ls, '-o')
thinkplot.Show(xlabel="Sample size, n", ylabel="standard error of estimate L")

```
The above experiment is repeated for n ranging from 5 to 50 with increment of 5. The plot of standard error versus n shows the rapid decrease in the standard error as the sample size increases. The decrement of the standard error becomes gradual when the sample size is large, greater than 40. 

![n Vs stderr](https://github.com/wfl/dsp/tree/master/statistics/plots/p8e2_plot.png)

The list of 90% confidence intervals for the sample sizes are presented below. This shows the reduction of the width of the 90% CI is associated with the increase of the sample size, n.

90% CI for n = 5  is ( 1.0924343485462056 ,  5.083494265952607 )
90% CI for n = 10  is ( 1.2767376581057643 ,  3.755328816466468 )
90% CI for n = 15  is ( 1.3757545201991925 ,  3.1537522360029397 )
90% CI for n = 20  is ( 1.4362401227397947 ,  3.0147716170538725 )
90% CI for n = 25  is ( 1.4801540027555267 ,  2.917862926583374 )
90% CI for n = 30  is ( 1.5306606062223416 ,  2.783078745393331 )
90% CI for n = 35  is ( 1.5486397060716104 ,  2.7030668628376144 )
90% CI for n = 40  is ( 1.5693346147840919 ,  2.62043157507916 )
90% CI for n = 45  is ( 1.5895172690101245 ,  2.6002043886442876 )
90% CI for n = 50  is ( 1.597443552831177 ,  2.537593827232144 )

  



