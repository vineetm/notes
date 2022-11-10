Source [FSDL Lab 1](https://fullstackdeeplearning.com/course/2022/labs-1-3-cnns-transformers-pytorch-lightning/)

### Linear Layer `@` operator
@ operator does matrix multiplication

```python
def linear(x: torch.Tensor) -> torch.Tensor:
    return x @ weights + bias
````


### Getting Log probabilties
1. Apply log to the exact equation, you get ride of torch.exp(x)
2. Convert the sum to 2D by doing [:, None]
```python
def log_softmax(x: torch.Tensor) -> torch.Tensor:
    return x - torch.log(torch.sum(torch.exp(x), axis=1))[:, None]
```
### Cross-Entropy trick
1. range gives the first index, target second index....
```python
def cross_entropy(output: torch.Tensor, target: torch.Tensor) -> torch.Tensor:
    return -output[range(target.shape[0]), target].mean()
```
