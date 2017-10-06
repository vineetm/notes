### Notes on installing tensorflow

* Make sure you have a conda environment with the right python See [conda](../conda.md)

* Activate environment and install ipython
  ```
  source activate py3tf

  (py3tf) $ pip install ipython
  ```

* If on a GPU machine, install `tensorflow-gpu`
  ```
  (py3tf) $ pip install tenorflow-gpu
  ```

* Following this you will also need to setup your `CUDA_HOME`. Put the following in your `~/.bashrc`
  ```
  export CUDA_HOME="/usr/local/cuda"
  ```

* Verify if you are indeed [using GPUs](https://www.tensorflow.org/tutorials/using_gpu)

  ```
  a = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[2, 3], name='a')
  b = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[3, 2], name='b')
  c = tf.matmul(a, b)

  sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))
  print(sess.run(c))
  ```
  You should be able to see that `a` `b` and `c` were indeed created on GPU
