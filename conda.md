### Notes for managing conda environments

* Creating a new conda environment `py3tf` for python 3.6
  ```bash
  conda create -n py3tf python=3.6
  ```

* Remove an environment

  ```bash
  conda env remove -n py3tf
  ```
* Clone an existing environment

```bash
conda create --name myclone --clone myenv
```
