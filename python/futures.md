```python
import concurrent
import time

def do_something(sec):
  print(f'Sleeping for {sec} s')
  time.sleep(sec)
  print(f'Done Sleeping for {sec} s')
  
  
secs = [5, 4, 3, 1, 2]

with concurrent.futures.ProcessPoolExecutor() as executor:
  results = [
    executor.submit(do_something, sec)
    for sec in secs
  ]

  for f in concurrent.futures.as_completed(results):
    print(f.result())
    
 ```
