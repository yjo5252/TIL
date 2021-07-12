# PyTorch

### PyTorch dimensionn
* torch.(method)(input, dim)
  * input (Tensor) 
  * dim =    

### argmax method 
* dim = 1,  1차원의 각 텐서에서 최대값의 index를 반환
```python
>>> a = torch.randn(4, 4)
>>> a
tensor([[ 1.3398,  0.2663, -0.2686,  0.2450],
        [-0.7401, -0.8805, -0.3402, -1.1936],
        [ 0.4907, -1.3948, -1.0691, -0.3132],
        [-1.6092,  0.5419, -0.2993,  0.3195]])
>>> torch.argmax(a, dim=1)
tensor([ 0,  2,  0,  1])

```

### stacking methond
* concatentaion (연결) 방법
```python
>>> # (1,2) 사이즈의 텐서 
>>> x = torch.FloatTensor([1, 4])
>>> y = torch.FloatTensor([2, 5])
>>> z = torch.FloatTensor([3, 6])

>>> # 3개의 벡터를 스택킹 (3 x 2) 
>>> print(torch.stack([x, y, z]))
tensor([[1., 4.],
        [2., 5.],
        [3., 6.]])

>>> # 3개의 벡터를 1차원이 증가되게 스택함. (2 x 3)
>>> print(torch.stack([x, y, z], dim=1))
tensor([[1., 2., 3.],
        [4., 5., 6.]])

```

### unsqueeze(0) method
```python
>>> x = torch.tensor([1, 2, 3, 4])
>>> torch.unsqueeze(x, 0)
tensor([[ 1,  2,  3,  4]])
>>> torch.unsqueeze(x, 1)
tensor([[ 1],
        [ 2],
        [ 3],
        [ 4]])

```

### Profiler x Pytorch 
* remember to remove it if you are benchmarking runtimes
* profiler is best used for investigating code 
```python
# Performance debugging using Pytorch 

import torch 
import numpy as np
from torch import nn 
import torch.autograd.profiler as profiler 

class MyModule(nn.Module):
    def __init__(self, in_features: int, out_features: int, bias: bool = True):
        super(MyModule, self).__init__()
        self.linear = nn.Linear(in_features, out_features, bias)

    def forward(self, input, mask):
        with profiler.record_function("LINEAR PASS"):
            out = self.linear(input)
        
        with profiler.record_function(" INDICES"):
            threshold = out.sum(axis=1).mean().item()
            hi_idx = np.argwhere(mask.cpu().numpy() > threshold)
            hi_idx = torch.from_numpy(hi_idx).cuda()

        return out, hi_idx
```
