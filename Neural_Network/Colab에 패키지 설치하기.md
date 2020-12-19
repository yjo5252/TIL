# Colab에 파이썬 패키지 설치하기 

참고한 링크: [Google Colab에서 python 패키지를 영구적으로 설치하는 방법](https://teddylee777.github.io/colab/colab%EC%97%90%EC%84%9C-python%ED%8C%A8%ED%82%A4%EC%A7%80%EB%A5%BC-permanently-%EC%9D%B8%EC%8A%A4%ED%86%A8%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95)

```python

import os, sys
from google.colab import drive

drive.mount('/content/drive')

my_path='/content/notebooks'

os.symlink('/content/drive/MyDrive/Colab NoteBooks/my_env', my_path)

sys.path.insert(0, my_path)

import pip

!pip install --target=$my_path scikit-learn 

```



#### * Colab 파이썬 버전 확인 
```python
import sys
sys.version_info

# sys.version_info(major=3, minor=6, micro=9, releaselevel='final', serial=0)
```

#### * 리눅스 버전 확인 
```python
import platform 
platform.platform()
# Linux-4.19.112+-x86_64-with-Ubuntu-18.04-bionic

```

#### * 








