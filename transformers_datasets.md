### Data Collators
* Used by dataloaders in order to create mini-batches of data
* If all elements of batch are of same length, then use the default data collator `DefaultDataCollator`
* Use `DataCollatorWithPadding` when inputs are not of the same size. This does not work with different length labels: for example for a Seq2Seq task...
* Use `DataCollatorForSeq2Seq` for padding seq2seq inputs. This also sets padded label tokens to -100
