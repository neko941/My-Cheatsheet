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



# 2. List
## 2.1 Print List
### 2.1.1
```python
list = ["N", "e", "k", "o"]

print(list)
```
```
['N', 'e', 'k', 'o']
```
### 2.1.2
```python
list = ["N", "e", "k", "o"]

print("\n".join(list))
```
```
N
e
k
o
```
### 2.1.3
```python
list = ["N", "e", "k", "o"]

for element in list:
    print(element)
```
```
N
e
k
o
```
### 2.1.4
```python
from pprint import pprint

list = ["N", "e", "k", "o"]
pprint(list)

list = list*5
pprint(list)
```
```
['N', 'e', 'k', 'o']
['N',
 'e',
 'k',
 'o',
 'N',
 'e',
 'k',
 'o',
 'N',
 'e',
 'k',
 'o',
 'N',
 'e',
 'k',
 'o',
 'N',
 'e',
 'k',
 'o']
 ```
