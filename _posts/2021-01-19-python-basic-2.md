---
layout: post
title: "Python Basic : 2. Variables"
category: Python
date: 2021-01-19 19:00:00 +0900
---
## Intro
>프로그래밍의 기초인 변수와 메모리에 대하여 공부합니다.

## Variable & Memory
변수는 가장 기초적인 프로그래밍 문법 개념입니다. 우리가 알던 수학에서의 변수와는 개념이 약간 다릅니다. 프로그래밍에서는 데이터를 저장하기 위한 메모리 공간의 이름을 변수라고 합니다. 파이썬에서는 모든 객체를 변수라고 생각할 수 있습니다. 변수의 개념을 이해하기 위해 컴퓨터로 1과 2를 더하는 과정을 살펴보겠습니다. 아래와 같이 기초적인 연산을 수행했을 때 컴퓨터 내부에서는 어떤 일이 일어날까요?

    >>> a = 1
    >>> b = 2
    >>> a + b
    3

우선 컴퓨터는 1의 값을 가지는 숫자 자료형이 자동으로 메모리에 생성됩니다. 그리고 변수 a는 값 1이 저장된 메모리 주소를 가리키게 됩니다. 다음 줄도 마찬가지로 2의 값을 가지는 숫자 자료형이 메모리에 생성되고, 변수 b는 값 2가 저장된 메모리 주소를 가리킵니다. 다음 줄에서는 변수 a가 가리키는 메모리 주소에 있는 값 1과 변수 b가 가리키는 메모리 주소에 있는 값 2를 합한 값 3을 출력하게 됩니다.

이런 처리과정은 현대 컴퓨터의 근간이 되는 폰 노이만 구조(Von Neumann architecture)에서 기인합니다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/77161691/107206334-3b49a500-6a42-11eb-9927-49872debd6a4.png" alt="Von Neumann architecture"/>
   Von Neumann architecture
</p>

폰 노이만 구조에서는 사용자가 컴퓨터에 값을 입력하거나 프로그램을 실행할 경우 그 정보를 먼저 메모리에 저장시키고 CPU가 순차적으로 그 정보를 해석하고 계산하여 사용자에게 결과값을 전달하기 때문입니다. 그러므로 위에서 ```a = 1```과 ```b = 2```의 의미는 "a와 b는 각각 1과 2다"가 아닌 "a와 b라는 이름을 가진 메모리 주소에 각각 1과 2를 저장한다"입니다.

이렇듯 변수를 선언하는 것은 프로그래밍에서 매우 중요한 과정입니다. 변수를 올바르게 선언하기 위해 보편적으로 사용되는 변수 작명법이 존재합니다. 아래의 규칙들은 꼭 기억할 필요가 있습니다.

1. 알파벳, 숫자, 언더스코어(_) 로 선언 가능

    ex) result = 0, _count = 2, _word = 'afdf’

2. 변수명은 의미 있는 단어로 표기하는 것이 좋다

    ex) student_name = 'Hucheol Moon’

3. 변수명은 대소문자가 구분된다.

    ex) ABC와 abc는 같지 않다

4. 특별한 의미가 있는 예약어는 쓰지 않는다. (예약어는 이미 의미와 용법이 지정되어 사용되는 단어를 말합니다.)

    ex) for, if, else 등

## Data Type
파이썬이 처리할 수 있는 데이터 유형을 자료형이라고 합니다. 주로 사용되는 자료형은 아래와 같습니다.

|자료형|설명|예시|
|---|---|---|
|정수형(integer)|음의 정수, 0, 양의 정수|-17, 0, 4|
|실수형(float)|소수점이 포함된 실수|3.1415|
|문자형(string)|따옴표로 감싸져있는 문자|abcd|
|불(boolean)|참거짓|True, False|

자료형들의 사용 예시는 아래와 같습니다.
```python
>>> a = 1 # integer
>>> print (a)
1
>>> b = 3.14 # float
>>> print (b)
3.14
>>> c = "abcs" # string
>>> print (c)
abcd
>>> d = True # boolean
>>> print (d)
True
```

### 데이터 형 변환
각 변수들은 데이터 변환 함수를 통해 자료형이 변환될 수 있습니다.
```python
>>> a = 1
>>> print (a)
1
>>> a = float(1)
>>> print (a)
1.0
>>> b = 3
>>> print (a / b)
0.33333333333
```

이렇게 변환된 변수의 자료형은 type() 함수를 통해 알 수 있습니다.
```python
>>> a = int(3.14)
>>> b = float(3.14)
>>> c = str(3.14)
>>> type(a)
<class 'int'>
>>> type(b)
<class 'float'>
>>> type(c)
<class 'str'>
```

## 리스트(List)
데이터가 한 개가 아니라 여러 개일 경우에는 여러 데이터들의 집합을 한 번에 관리할 필요가 있습니다. 이러한 자료형을 리스트라고 합니다. 리스트 안에는 정수, 실수, 리스트 등 다양한 데이터 타입이 포함될 수 있습니다. 리스트의 성질들은 아래와 같습니다.

1. 인덱싱(Indexing)
    리스트에 있는 값들은 주소(offset)를 가지고, 주소를 사용해 할당된 값을 호출합니다.
    ```python
    colors = ['red', 'green', 'blue', 'yellow', 'purple']
    print (colors[0])      # red
    print (colors[-1])     # purple
    print (len(colors))    # 5
    ```

2. 슬라이싱(Slicing)
    리스트의 값들을 잘라서 쓰는 것이 슬라이싱입니다. 리스트의 주소 값을 기반으로 부분 값을 반환합니다.
    ```python
    colors = ['red', 'green', 'blue', 'yellow', 'purple']
    print (colors[0:3])        # 0부터 2까지
    print (colors[:])          # 처음부터 끝까지
    print (colors[::2])        # 2칸 단위로 슬라이싱
    ```

3. 리스트의 연산
    ```python
    >>> color1 = ['red', 'green', 'blue']
    >>> color2 = ['orange', 'black', 'white']
    >>> print (color1 + color2)            # 두 리스트 합치기
    >>> len(color1)                        # 리스트 길이
    >>> color1[0] = 'yellow'               # 0번째 리스트의 값을 변경
    >>> print (color1 * 2)                 # color 리스트 2회 반복
    >>> 'blue' in color2                   # 문자열 ‘blue‘가 color2 존재 여부 반환
    >>> total_color = color1 + color2
    >>> color1.append("white")              # 리스트에 “white” 추가
    >>> color1.extend(["black","purple"])   # 리스트에 새로운 리스트 추가
    >>> color1.insert(0,"orange")           # 0번째 주소에 “orange” 추가
    >>> print (color1)
    ['orange', 'red', 'green', 'blue', 'white', 'black', 'purple']
    >>> color.remove("white")              # 리스트에 “white” 삭제
    >>> del color[0]                       # 0번째 주소 리스트 객체 삭제
    >>> print (color)
    ['red', 'green', 'blue', 'black', 'purple']
    ```

4. 리스트 메모리 저장 방식
    리스트를 다룰 때 주의할 점은 리스트 변수는 리스트의 주소값이 저장되기 때문에 아래와 같은 상황이 발생할 수 있습니다.
    ```python
    >>> a = [3, 2, 1]
    >>> b = [1, 2, 3]
    >>> b = a
    >>> print (b)
    [3, 2, 1]
    >>> a.sort()
    >>> print (b)
    [1, 2, 3]
    >>> b = [4, 5, 6]
    >>> print (a, b)
    [1, 2, 3] [4, 5, 6]
    ```

    이를 해결하기 위해서는 deep copy가 필요합니다.

5. 패킹과 언패킹
    패킹은 한 변수에 여러 개의 데이터를 넣는 것입니다. 반대로 언패킹은 한 변수의 데이터를 각각의 변수로 반환하는 것입니다.
    ```python
    >>> t = [1, 2, 3]
    >>> a , b , c = t
    >>> print(t, a, b, c)  # [1, 2, 3] 1 2 3
    ```

<br/>

### References
1. NAVER Connect Foundation
2. [Wikipedia: Von Neumann architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture)
