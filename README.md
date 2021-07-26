# Python
This is my note for Python


## 1. Proccessing Bar
### 1.1 tqdm
### 1.1.1
```python
from time import sleep
from tqdm import tqdm
for i in tqdm(range(100)):
    sleep(1)
```

### 1.1.2
```python
from tqdm.notebook import tqdm
for i in tqdm(range(100)):
    sleep(1)
```
