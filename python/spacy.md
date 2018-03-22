### Install English Model

```
python -m spacy download en
```

### Tokenization

```
nlp = spacy.load('en')
doc = nlp.tokenizer(text)

sentence = ' '.join([token.text for token in doc])
```
