* Gradient clipping is a useful trick for training RNNs

* First compute the trainable variables
  ```python
  params = tf.trainable_variables()
  ```

* Next, compute the gradients
  ```python
  gradients = tf.gradients(loss, params)
  ```

* Next, clip the gradients
  ```python
  clipped_gradients, gradient_norm = tf.clip_by_global_norm(gradients, max_gradient_norm)
  ```

* Next apply clipped_gradients
  ```python
  opt = tf.train.GradientDescentOptimizer(lr)
  update_step = opt.apply_gradients(zip(clipped_gradients, params))
