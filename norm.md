### Normal distribution
* We need only two things to plot a normal distribtion in 1 dimension: mean and standard deviation

```python
from scipy.stats import norm

mu = np.mean(x) # mean
var = np.var(x) # variance
std = np.sqrt(var) # standard deviation
    
x_axis = np.linspace(mu - 3*std, mu + 3*std, 1000)
plt.plot(x_axis, norm.pdf(x_axis, mu, std), 'r', lw=2)
```
