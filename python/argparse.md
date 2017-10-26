Powerful commandline parser for Python

Great Tutorial: [https://docs.python.org/2/howto/argparse.html]()

* Basic Setup
  ```python
  import argparse

  parser = argparse.ArgumentParser()
  parser.add_argument('arg1')
  args = parser.parse_args()
  ```

* By default all positional arguments are string

* Handle boolean arguments as follows
  ```
  parser = argparse.ArgumentParser()
  parser.add_argument('-v', action='store_true')
  ```

* Restricting input choices
  ```
  parser.add_argument("-v", "--verbosity", type=int, choices=[0, 1, 2],
                    help="increase output verbosity")
  ```

* Adding mutually exclusive options
  ```
  group = parser.add_mutually_exclusive_group()
  group.add_argument("-v", "--verbose", action="store_true")
  group.add_argument("-q", "--quiet", action="store_true")
  ```
