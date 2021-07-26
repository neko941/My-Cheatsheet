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



# 3. Directory
## 3.1 List in the Current Directory 
```python
import os
 
print("\n".join(os.listdir()))
```
```
1
demo.docx
demo.py
demo.txt
demo.xlsx
```
## 3.2 List in the Current Directory (specific file extenstion)
### 3.2.1
```python
import glob

for file in glob.glob("*.txt"):
    print(file)
```
```
demo.txt
```
### 3.2.2
```python
import os

for file in os.listdir():
    if file.endswith(".txt"):
        print(file)
```
```
demo.txt
```
## 3.3 List in the Current Directory (with full path)
```python
import os

for element in os.listdir():
    files_path = os.path.abspath(element)
    print(files_path)
```
```
C:\Users\nguye\Desktop\Python Test Folder\demo\1
C:\Users\nguye\Desktop\Python Test Folder\demo\demo.docx
C:\Users\nguye\Desktop\Python Test Folder\demo\demo.py
C:\Users\nguye\Desktop\Python Test Folder\demo\demo.txt
C:\Users\nguye\Desktop\Python Test Folder\demo\demo.xlsx
```
## 3.4 List Directory Tree
### 3.4.1
```python
import os

for root, directories, files in os.walk(os.getcwd()):
    for file in files:
        print(f"File: {file}")
        print(f"Directory: {directories}")
        print(f"Path: {file}")
        print(f"Full Path: {os.path.join(root, file)}", end = "\n\n")
```
```
File: demo.docx
Directory: ['1']
Path: demo.docx
Full Path: C:\Users\nguye\Desktop\Python Test Folder\demo\demo.docx

File: demo.py
Directory: ['1']
Path: demo.py
Full Path: C:\Users\nguye\Desktop\Python Test Folder\demo\demo.py

File: demo.txt
Directory: ['1']
Path: demo.txt
Full Path: C:\Users\nguye\Desktop\Python Test Folder\demo\demo.txt

File: demo.xlsx
Directory: ['1']
Path: demo.xlsx
Full Path: C:\Users\nguye\Desktop\Python Test Folder\demo\demo.xlsx

File: 1 - demo.docx
Directory: ['2']
Path: 1 - demo.docx
Full Path: C:\Users\nguye\Desktop\Python Test Folder\demo\1\1 - demo.docx

File: 1 - demo.txt
Directory: ['2']
Path: 1 - demo.txt
Full Path: C:\Users\nguye\Desktop\Python Test Folder\demo\1\1 - demo.txt

File: 1 - demo.xlsx
Directory: ['2']
Path: 1 - demo.xlsx
Full Path: C:\Users\nguye\Desktop\Python Test Folder\demo\1\1 - demo.xlsx

File: 2 - demo.docx
Directory: []
Path: 2 - demo.docx
Full Path: C:\Users\nguye\Desktop\Python Test Folder\demo\1\2\2 - demo.docx

File: 2 - demo.txt
Directory: []
Path: 2 - demo.txt
Full Path: C:\Users\nguye\Desktop\Python Test Folder\demo\1\2\2 - demo.txt

File: 2 - demo.xlsx
Directory: []
Path: 2 - demo.xlsx
Full Path: C:\Users\nguye\Desktop\Python Test Folder\demo\1\2\2 - demo.xlsx
```
### 3.4.2
```python
def print_directory_tree(path, indent):
    for root, directories, files in os.walk(path):
        level = root.replace(path, "").count(os.sep)
        indent = "   " * level
        print(f"{indent}└──{os.path.basename(root)}/")

        subindent = "   " * (level + 1)
        for file in files:
            print(f"{subindent}└──{file}")

print_directory_tree(os.getcwd(), "")
```
```
└──demo/
   └──demo.docx
   └──demo.py
   └──demo.txt
   └──demo.xlsx
   └──1/
      └──1 - demo.docx
      └──1 - demo.txt
      └──1 - demo.xlsx
      └──2/
         └──2 - demo.docx
         └──2 - demo.txt
         └──2 - demo.xlsx
```
### 3.4.3
```python
import os

def print_directory_tree(path, indent, root):
    if root:
        print(f"{indent}└──{os.path.basename(path)}")
        root = False
        indent += "    "
    for elements in os.listdir(path):
        new_path = os.path.join(path, elements)
        if elements == os.listdir(path)[-1]:
            if os.path.isdir(new_path):
                print(f"{indent}└──{elements}")
                print_directory_tree(new_path,indent + "  ", root)
            else:
                print(f"{indent}└──{elements}")
        else:
            if os.path.isdir(new_path):
                print(f"{indent}├──{elements}")
                print_directory_tree(new_path,indent + "│  ", root)
            else:
                print(f"{indent}├──{elements}")
            
print_directory_tree(os.getcwd(), "", True)

```
```
└──demo
    ├──1
    │  ├──1 - demo.docx
    │  ├──1 - demo.txt
    │  ├──1 - demo.xlsx
    │  └──2
    │    ├──2 - demo.docx
    │    ├──2 - demo.txt
    │    └──2 - demo.xlsx
    ├──demo.docx
    ├──demo.py
    ├──demo.txt
    └──demo.xlsx
```
