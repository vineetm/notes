Source: [FSDL Lab1](https://github.com/full-stack-deep-learning/fsdl-text-recognizer-2022-labs)

### Use Cross-Entropy from torch stateless functions
```python
import torch.nn.functional as F

loss_func = F.cross_entropy

def accuracy(out: torch.Tensor, yb: torch.Tensor) -> torch.Tensor:
    preds = torch.argmax(out, dim=1)
    return (preds == yb).float().mean()

def model(xb):
    return xb @ weights + bias

print(loss_func(model(xb), yb), accuracy(model(xb), yb))
```