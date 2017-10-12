A common operation when working with text is to convert a sentence to a list of words. You can use `lookup_ops` from `tensorflow.python.ops` to do that...

Assuming you already have a vocab_file and UNK has `index=0`
```
from tensorflow.python.ops import lookup_ops

vocab_table = lookup_ops.index_table_from_file(vocab_file, default_value=0)

test_sentence = ['hi , how are you doing ?']
sentence = tf.placeholder(tf.string)
words = tf.string_split(sentence)
word_indexes = vocab_table.lookup(words.values)

sess.run(tf.tables_initializer())
wi = sess.run(word_indexes, {sentence: test_sentence})
```
