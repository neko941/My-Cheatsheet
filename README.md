# Python
This is my note for Python


# 1. Proccessing Bar
## 1.1 [tqdm](https://github.com/tqdm/tqdm)
### 1.1.1
```python
from time import sleep
from tqdm import tqdm

for i in tqdm(range(100)):
    sleep(1)
```
![image](https://user-images.githubusercontent.com/42170045/126926960-b69c2cf3-094f-47bd-a19f-0eb7f9464d78.png)

### 1.1.2
```python
from time import sleep
from tqdm.notebook import tqdm

for i in tqdm(range(100)):
    sleep(1)
```
![image](https://user-images.githubusercontent.com/42170045/126926975-7854c192-750a-49e5-bbc4-ad9e1e2bb34c.png)

## 1.2 [alive_progress](https://github.com/rsalmei/alive-progress)
from time import sleep
from alive_progress import alive_bar

with alive_bar(100) as bar:
    for i in range(100):
        sleep(.01)
        bar()
