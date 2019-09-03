* Find Large files
```
  find BASE_DIR -xdev -type f -size +100M
```

* rm for a long file list
```bash
find . -name "*.entities.json" -print0 | xargs -0 rm
```
