1. rm for a long file list
```bash
find . -name "*.entities.json" -print0 | xargs -0 rm
```
