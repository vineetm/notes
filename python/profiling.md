```python
import cProfile

with cProfile.Profile() as pr:
    my_fun()

pr.print_stats(sort='cumtime')
```
