## Histogram

Let us say you want to look at how your data is distributed. One of the first things to do that would be draw a histogram

```python
%matplotlib inline
import matplotlib.pyplot as plt
plt.hist(x, density=True)
```

Note that this could create some bars which are > 1. and they definitely don't sum to 1! Why is that?

This is because the x-axis dispalys absolute values and not the bin width!
See details [here](https://github.com/matplotlib/matplotlib/issues/10398/)


We can check how this indeed integrates to 1
```
hist, bin_edges = np.histogram(x, density=True)
np.sum(hist * np.diff(bin_edges))
```
