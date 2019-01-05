[Think Stats Chapter 8 Exercise 3](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77)

---

>>

```python
import random

import thinkstats2
import thinkplot

# The function SimulateGame() was written by Allen B. Downey
def SimulateGame(lam):
    """Simulates a game and returns the estimated goal-scoring rate.

    lam: actual goal scoring rate in goals per game
    """
    goals = 0
    t = 0
    while True:
        time_between_goals = random.expovariate(lam)
        t += time_between_goals
        if t > 1:
            break
        goals += 1

    # estimated goal-scoring rate is the actual number of goals scored
    L = goals
    return L
```

```python
def SimManyGames(lam, ngames):
    Ls = []
    for _ in range(ngames):
        L = SimulateGame(lam)
        Ls.append(L)
    
    return Ls

lam = 2
Ls1 = SimManyGames(lam, ngames=10000)
print("Mean Error (10000 simulations) = ", MeanError(Ls1, lam))
print('stderr (10000 simulations) = ', RMSE(Ls1, lam))

Ls2 = SimManyGames(lam, ngames=100000)
print("Mean Error (100000 simulations) = ", MeanError(Ls2, lam))
print('stderr (100000 simulations) = ', RMSE(Ls2, lam))

Ls3 = SimManyGames(lam, ngames=1000000)
print("Mean Error (1000000 simulations) = ", MeanError(Ls3, lam))
print('stderr (1000000 simulations) = ', RMSE(Ls3, lam))

pmf1 = thinkstats2.Pmf(Ls1, label="10000 sim")
pmf2 = thinkstats2.Pmf(Ls2, label="100000 sim")
pmf3 = thinkstats2.Pmf(Ls3, label="1000000 sim")
thinkplot.PrePlot(3)
thinkplot.Pmfs([pmf1, pmf2, pmf3])
thinkplot.Show(xlabel="Number of goal scored", ylabel="PMF")
```

The game is simulated 10000, 100000, and 1000000 times seperately. For each round, the mean error and standard error of the estimated number of goals scored is calculated (see Python output below). As the number of simulations increases the mean error decreases and it is almost close to zero for 1000000 simulations. However, it isn't the case for standard error, which increases gradually. The PMF plot shows the distributions of the estimate for the 3 simulation runs. 

Mean Error (10000 simulations) =  -0.0064
stderr (10000 simulations) =  1.4050622761998843

Mean Error (100000 simulations) =  -0.00547
stderr (100000 simulations) =  1.4087405722843365

Mean Error (1000000 simulations) =  -0.001209
stderr (1000000 simulations) =  1.4134719664712136

![Figure 1 - PMF](https://github.com/wfl/dsp/tree/master/statistics/plots/p8e3_PMF.png)
