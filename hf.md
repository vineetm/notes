## Setup a tokenizer

tokenizer = AutoTokenizer.from_pretrained(model_name)
tokenizer.pad_token = tokenizer.pad_token or tokenizer.eos_token

## Generation Config
model = AutoModelForCausalLM.from_pretrained(model_name, dtype=torch.bfloat16, device_map='auto')

model.generation_config = GenerationConfig.from_pretrained(model_name)
model.generation_config.pad_token_id = model.generation_config.eos_token_id

