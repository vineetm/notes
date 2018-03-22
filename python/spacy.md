### Tokenization

```
nlp = spacy.load('en')
doc = nlp.make_doc(text)

sentence = ' '.join([token.text for token in doc])
```
