### Finetuning a flan-t5 model

#### Source inputs needed: `input_ids` and `attention_mask`
Based on Huggingface training T5 [Doc](https://huggingface.co/docs/transformers/model_doc/t5#training)
```python
from transformers import AutoTokenizer, AutoModelforSeq2SeqLM

model_name_or_path = 'google/flan-t5-small'
tokenizer = AutoTokenier.from_pretrained(model_name_or_path)
model = AutoModelforSeq2SeqLM.from_pretrained(model_name_or_path)

# the following 2 hyperparameters are task-specific
max_source_length = 512
max_target_length = 128

# Suppose we have the following 2 training examples:
input_sequence_1 = "Welcome to NYC"
output_sequence_1 = "Bienvenue à NYC"

input_sequence_2 = "HuggingFace is a company"
output_sequence_2 = "HuggingFace est une entreprise"

# encode the inputs
task_prefix = "translate English to French: "
input_sequences = [input_sequence_1, input_sequence_2]

encoding = tokenizer(
    [task_prefix + sequence for sequence in input_sequences],
    padding="longest",
    max_length=max_source_length,
    truncation=True,
    return_tensors="pt",
)
input_ids, attention_mask = encoding.input_ids, encoding.attention_mask
```

* `input_ids` is padded with pad tokens. In this case `token_id=0`. We can find this by checking `tokenizer.pad_token_id`
* `input_ids` always ends with `end` (in this case `token_id=1`)

#### Target inputs needed `labels`
* HF automatically constructs `target_input_ids` from labels
* However, it does not ignore **padded** labels! Why?
* Thus, we need to manually set all padded labels to `-100` which is special ignore index in pytorch (and tensorflow?)

```python
target_encoding = tokenizer(
    [output_sequence_1, output_sequence_2],
    padding="longest",
    max_length=max_target_length,
    truncation=True,
    return_tensors="pt",
)
labels = target_encoding.input_ids
labels[labels == tokenizer.pad_token_id] = -100
```
