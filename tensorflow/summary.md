* Create a summary writer as follows:
  ```python
  summary_writer = tf.summary.FileWriter(os.path.join(hparams.out_dir, 'train_log'), train_model.graph)
  ```

  This will create a directory `train_log` inside `out_dir` and start putting events there

* Let us say you want to monitor training loss

  ```python
  self.train_summary = tf.summary.scalar('train_loss', self.train_loss)
  ```

* Finally you can dump summary using
  ```python
  summary_writer.add_summary(train_summary, step)
  ```
