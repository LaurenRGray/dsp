[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

# Exercise 3.1

**Exercise**: Something like the class size paradox appears if you survey children and ask how many children are in their family. Families with many children are more likely to appear in your sample, and families with no children have no chance to be in the sample.

Use the NSFG respondent variable numkdhh to construct the actual distribution for the number of children under 18 in the respondents' households.

Now compute the biased distribution we would see if we surveyed the children and asked them how many children under 18 (including themselves) are in their household.

Plot the actual and biased distributions, and compute their means.

### Summary of steps to obtain solution:

##### Step 1: imported necessary modules
```python
import nsfg
import thinkstats2
import thinkplot
%matplotlib inline
```

##### Step 2: made frames
```python
resp = nsfg.ReadFemResp()
biased = resp[resp.numkdhh != 0]
```

##### Step 3: computed the actual and biased PMFs for children under 18
```python
actual_pmf = thinkstats2.Pmf(resp.numkdhh, label='actual')
biased_pmf = thinkstats2.Pmf(biased.numkdhh, label='biased')
```

##### Step 4: Plotted the actual and biased pmfs as a histograms and as a step functions, side by side
```python
width=0.45
axis = [-1, 6, 0, 0.5]
thinkplot.PrePlot(2, cols=2)
thinkplot.Hist(actual_pmf, align='right', width=width)
thinkplot.Hist(biased_pmf, align='left', width=width)
thinkplot.Config(xlabel='Children under 18', ylabel='PMF', axis=axis)

thinkplot.PrePlot(2)
thinkplot.SubPlot(2)
thinkplot.Pmfs([actual_pmf, biased_pmf])
thinkplot.Config(xlabel='Children Under 18', axis=axis)
```

##### Step 5: computed the means for the actual and biased distributions
```python
actual_pmf_mean = actual_pmf.Mean()
biased_pmf_mean = biased_pmf.Mean()

print('actual_mean: ', actual_pmf_mean)
print('actual_mean: ', biased_pmf_mean)
```

### Interpretation of results:
The means for the actual and biased pmf distributions show that if you survey a group of children, you would think the average number of children under 18 in a family was bigger than it actually is. This is also apparent in the distributions. The biased distribution shows 0 families with 0 children and overestimates the number of children in families with children under 18. 

### Plots:
[Plots of actual and biased PMF distribution for the number of children under 18 in the respondents' households](https://i.imgur.com/nPfWWwN.png)
