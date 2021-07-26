# Python
This is my note for Python


# 1. Proccessing Bar
## 1.1 [tqdm](https://github.com/tqdm/tqdm)
### 1.1.1
```python
import time
from tqdm import tqdm

for i in tqdm(range(100)):
    time.sleep(.01)
```

### 1.1.2
```python
import time
from tqdm.notebook import tqdm

for i in tqdm(range(100)):
    time.sleep(.01)
```

## 1.2 [alive_progress](https://github.com/rsalmei/alive-progress)
```python
import time
from alive_progress import alive_bar

with alive_bar(100) as bar:
    for i in range(100):
        time.sleep(.01)
        bar()
```
