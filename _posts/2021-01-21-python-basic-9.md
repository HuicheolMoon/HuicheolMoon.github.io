---
layout: post
title: "Python Basic : 9. Module and Project"
category: Python
date: 2021-01-21 19:10:00 +0900
---
## Intro
>파이썬 프로젝트의 기본이 되는 모듈과 패키지, 그리고 프로젝트의 개념에 대해서 공부합니다.

## Module
파이썬은 대부분의 라이브러리가 이미 다른 사용자에 의해서 구현되어 있습니다. 그렇기에 내가 코드를 잘 작성하여 사용하는 것도 중요하지만 남이 작성한 코드를 잘 가져와서 사용하는 것 또한 중요합니다. 프로그램에서는 작은 프로그램 조각들, module들을 모아서 하나의 큰 프로그램을 개발합니다. 개발 과정을 module화시키면 다른 프로그램이 사용하기 쉽기 때문입니다. 그리고 이런 module을 모아놓은 단위를 package라고 합니다. 파이썬에서 Module은 다른 py 파일을 의미합니다. 같은 폴더에 Module에 해당하는 .py 파일과 사용하는 .py을 저장한 후 import 문을 사용해서 module을 호출할 수 있습니다. module 안에는 함수와 클래스 등이 존재하는데 이 중 필요한 내용만 골라서 호출하고자 할 때 from과 import 키워드를 사용합니다. 이 방법에는 세 가지가 있습니다.
1. Alias(별명) 설정하기
    ```python
    import fah_converter as fah
    print(fah.covert_c_to_f(41.6))
    ```

2. 모듈에서 특정 함수 또는 클래스만 호출하기
    ```python
    from fah_converter import covert_c_to_f
    print(covert_c_to_f(41.6))
    ```

3. 모듈에서 모든 함수 또는 클래스를 호출하기
    ```python
    from fah_converter import *
    print(covert_c_to_f(41.6))
    ```

파이썬이 기본 제공하는 라이브러리에도 많은 종류가 있습니다.
```python
# 난수
import random
print (random.randint (0,10)) # 0과 10사이의 정수 난수를 생성
print (random.random())       # 일반적인 난수 생성

# 시간
import time
print(time.localtime())       # 현재 시간 출력
```

## Package
Package는 하나의 대형 프로젝트를 만드는 코드의 묶음입니다. 다양한 모듈들의 합이며 이는 폴더로 연결됩니다. __init__ , __main__ 등 키워드 파일명이 사용됩니다. 우리가 알고 있는 다양한 오픈소스들이 모두 패키지로 관리됩니다. 패키지를 만드는 과정은 아래과 같습니다.

1. 기능들을 세부적으로 나눠 폴더로 만든다.

2. 각 폴더별로 필요한 모듈을 구현한다.

3. 폴더별로 __init__.py을 구성한다.

4.  __main__.py 파일을 만든다.

<br/>

### References
1. NAVER Connect Foundation
