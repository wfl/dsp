[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

>>

```python
import first

live, firsts, others = first.MakeFrames()
dg = CohenEffectSize(firsts.prglngth, others.prglngth)
dw = CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
mean1 = firsts.totalwgt_lb.mean()
meano = others.totalwgt_lb.mean()
med1 = firsts.totalwgt_lb.median()
medo = others.totalwgt_lb.median()
```
Python output: 
mean1, meano, med1, medo  = (7.201094430437772, 7.325855614973262, 7.3125, 7.375)
dg =  0.028879044654449883
dw = -0.088672927072602

The mean and median of the first baby are 7.201 and 7.313 lbs respectively, while for the others, the mean and median are 7.325 and 7.375 lbs respectively. This indicates the first baby is lighter than the others. The negative Cohen's d value, -0.0887 comfirms this conclusion. 

The difference in pregnancy length for the first babies is 0.029 standard deviation, around 4 times lesser than totalwgt_lb's d value. However, that doesn't mean the difference in total weight is more significant than the difference in pregnancy length since both values are less than 0.2, which indicates the effect sizes are very small, according to the table suggested by Cohen and Sawilowsky in [Cohen's d(Wikipedia)](https://en.wikipedia.org/wiki/Effect_size#Cohen's_d). Also note that the positive d that indicates the pregnancy length for the first babies are longer.




