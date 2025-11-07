## Setup a tokenizer

```python
tokenizer = AutoTokenizer.from_pretrained(model_name)
tokenizer.pad_token = tokenizer.pad_token or tokenizer.eos_token
```

## Generation Config
```python
model = AutoModelForCausalLM.from_pretrained(model_name, dtype=torch.bfloat16, device_map='auto')

model.generation_config = GenerationConfig.from_pretrained(model_name)
model.generation_config.pad_token_id = model.generation_config.eos_token_id
````

### Torch inference model
```python
def model_output(prompt, model, tokenizer):

    # Using `inference mode` avoids overhead usually required during training
    # The code still works without `inference mode`, but requires more memory
    with torch.inference_mode():
        ids = tokenizer(prompt, return_tensors='pt').to(model.device)

        outputs = model.generate(
            input_ids=ids['input_ids'],
            attention_mask=ids['attention_mask'],
            max_new_tokens=5)
        decoded = tokenizer.decode(outputs[0], skip_special_tokens=True)
        print(f'Model output: {outputs}')
        print(f'Model decoded output: {decoded}\n')
```
