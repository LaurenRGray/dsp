[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

# Exercise 2.4:
Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. Compute Cohen's *d* to quantify the difference between the groups. How does it compare to the difference in pregnancy length?

### Summary of steps to obtain solution:

##### 1. I imported necessary modules
```python

import first
import thinkstats2
```
##### 2. I defined functions
```python
def WeightDifference(live, firsts, others):
    """Explore the difference in weight between first babies and others.

    live: DataFrame of all live births
    firsts: DataFrame of first babies
    others: DataFrame of others
    """
    mean0 = live.totalwgt_lb.mean()
    mean1 = firsts.totalwgt_lb.mean()
    mean2 = others.totalwgt_lb.mean()

    var1 = firsts.totalwgt_lb.var()
    var2 = others.totalwgt_lb.var()
    
    std1 = firsts.totalwgt_lb.std()
    std2 = others.totalwgt_lb.std()

    print('Mean')
    print('First babies', mean1)
    print('Others', mean2)

    print('\nVariance')
    print('First babies', var1)
    print('Others', var2)
    
    print('\nStandard Deviation')
    print('First babies', std1)
    print('Others', std2)

    print('\nDifference in lbs', mean1 - mean2)
    print('Difference in oz', (mean1 - mean2) * 16)

    print('\nDifference relative to mean (%age points)', 
          (mean1 - mean2) / mean0 * 100)

    d = thinkstats2.CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
    print('\nCohen d', d)
```
```python
def PregLengthDifference(live, firsts, others):
    """Explore the difference in pregnancy length between first babies and others.

    live: DataFrame of all live births
    firsts: DataFrame of first babies
    others: DataFrame of others
    """
    mean0 = live.prglngth.mean()
    mean1 = firsts.prglngth.mean()
    mean2 = others.prglngth.mean()

    var1 = firsts.prglngth.var()
    var2 = others.prglngth.var()
    
    std1 = firsts.prglngth.std()
    std2 = others.prglngth.std()

    print('Mean')
    print('First babies', mean1)
    print('Others', mean2)

    print('\nVariance')
    print('First babies', var1)
    print('Others', var2)
    
    print('\nStandard Deviation')
    print('First babies', std1)
    print('Others', std2)

    print('\nDifference in pregnancy length', mean1 - mean2)

    print('\nDifference relative to mean (%age points)', 
          (mean1 - mean2) / mean0 * 100)

    d = thinkstats2.CohenEffectSize(firsts.prglngth, others.prglngth)
    print('\nCohen d', d)
```
##### 3. I made frames
```python
live, firsts, others = first.MakeFrames()
```
##### 4. I computed the weight difference between first babies and others
```python
WeightDifference(live, firsts, others)
```
##### 5. I computed the pregnancy length difference between first babies and others
```python
PregLengthDifference(live, firsts, others)
```

### Interpretation of results:

Based on the above results, the mean weight of first babies and others is approximately 7.20 and 7.33 lbs, respectively. Thus, the mean weight for the others category is approximately 0.13 lbs heavier than first babies. 

Cohen's *d*, which conveys the size of the effect by comparing the difference between groups to the variability within groups, for the difference in birth weight is -0.089. So the difference in means in this example is -0.089 standard deviations. 

Cohen's *d* for the difference in pregnancy length is 0.029. 
