To read a csv file
  ```python
  import csv

  with open('train.csv') as fr:
    reader = csv.reader(fr)
    for row in reader:
      print (row)
  ```

If you want to skip the header, just call iterator once..
```python
import csv

with open('train.csv') as fr:
  reader = csv.reader(fr)
  next(reader)
  for row in reader:
    print (row)
```
