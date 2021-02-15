---
layout: post
title: "Python Basic : 5. String and Advanced Function Concept"
category: Python
date: 2021-01-19 19:30:00 +0900
---
## Intro
>문자열 자료형과 함수의 조금 더 높은 난이도의 개념을 공부합니다.

## 문자열(String)
문자열은 시퀀스 자료형으로 문자형 data를 메모리에 저장합니다. 영문자 한 글자는 1byte의 메모리 공간을 사용합니다. 문자열 자료형이 가지는 특성들은 아래와 같습니다.

1. 인덱싱 (Indexing)
    문자열의 각 문자는 개별 주소(offset)를 가집니다. 이 주소를 사용해 할당된 값을 가져오는 것이 인덱싱입니다. 리스트와 같은 형태로 데이터를 처리한다고도 볼 수 있습니다.
    ```python
    >>> a = "abcde"
    >>> print (a[0], a[4])     # a 변수의 0번째, 4번째 주소에 있는 값
    a e
    >>> print (a[-1], a[-5])   # a 변수의 오른쪽에서 0번째, 4번째 주소에 있는 값
    e a
    ```

    리스트와 동일하게 문자열의 offset은 왼쪽에서는 0부터, 오른쪽에서는 -1부터 시작합니다.
    ```python
    H  e  l  l  o
    0  1  2  3  4
   -5 -4 -3 -2 -1
    ```

2. 슬라이싱 (Slicing)
    슬라이싱은 문자열의 주소값을 기반으로 문자열의 부분값을 반환하는 것입니다.
    ```python
    >>> a = "Deep Learning"
    >>> print (a[0:2], " AND ", a[-3:])
    Dee AND ing
    >>> print (a[:])
    Deep Learning
    >>> print (a[-50:50])
    Deep Learning
    ```

Python은 문자열 자료형에 대해 다양한 내장 함수들을 지원합니다.

```python
>>> a = "Deep Learning"
>>> a.upper()
'DEEP LEARNING'
>>> a.lower()
'deep learning'
>>> a.split(" ")
['Deep', 'Learning']
>>> a.isdigit()
False
>>> a.count("a")
1
>>> a.split(" ")
['Deep', 'Learning']
```

문자열을 선언할 때 여러가지 난관에 부딪힐 수 있습니다.

1. '나 "를 문자열 안에 포함시키고 싶을 때
2. 두 줄 이상의 문자열을 하나의 변수 안에 저장하고 싶을 때

이러한 케이스를 위하여 python은 백슬래시(\)를 통한 문자 표현을 지원합니다. 이를 이스케이프 시퀀스(Escape Sequence)라고 합니다.

## Call by Object Reference
프로그래밍 언어의 함수에서 parameter를 전달하는 방식에는 아래의 세 가지가 있습니다.

1. 값에 의한 호출(Call by Value)
    Call by Value 방식은 함수에 parameter를 넘길때 value만 넘깁니다. 그렇기 때문에 함수 내에 parameter value가 변경되어도 호출자에게는 영향을 주지 않습니다.

2. 참조의 의한 호출(Call by Reference)
    Call by Reference 방식은 함수에 parameter를 넘길때 메모리 주소를 넘깁니다. 함수 내에 parameter value가 변경되면 호출자에게 영향을 줍니다.

3. 객체 참조에 의한 호출(Call by Object Reference)
    Python은 Call by Object Reference 방식을 사용하고 있습니다. Call by Object Reference는 객체의 주소가 함수로 전달되는 방식입니다. 전달된 객체를 참조하여 변경 시 호출자에게 영향을 주나, 새로운 객체를 만들 경우에는 호출자에게 영향을 주지 않습니다.

## Recursive Function
재귀함수는 자기자신을 호출하는 함수입니다. 주로 점화식과 같은 재귀적 수학 모형을 표현할 때 사용됩니다. 재귀 종료 조건이 존재하고 종료 조건까지 함수 호출을 반복하게 됩니다.
```python
def factorial(n):
    if n == 1:
        return 1
    else:
        return n + factorial(n - 1)

print(factorial(int(input("팩토리얼 계산을 위한 숫자를 입력하세요: "))))
```

## Type hints for function
앞서 배운 파이썬의 특징 중 하나가 파이썬은 dynamic typing language라는 것입니다. 이는 코드 작성에는 편의를 제공하지만 처음 함수를 사용하는 사용자가 interface를 알기 어렵다는 단점이 있습니다. 이를 해결하기 위해 python 3.5 버전 이후로는 PEP 484에 기반하여 type hints 기능을 제공하고 있습니다. type hints는 함수의 parameter와 return value의 자료형을 미리 지정하는 기능입니다.
```python
def type_function(var_name: var_type) -> return_type:
    pass
```

type hints는 사용자에게 인터페이스를 명확히 알려줄 수 있고, 함수의 문서화시 parameter에 대한 정보를 명확히 알 수 있다는 장점이 있습니다. 또한 mypy 또는 IDE, linter 등을 통해 코드의 발생 가능한 오류를 사전에 확인할 수 있기 때문에 시스템 전체적인 안정성을 확보할 수 있습니다. 현업에서도 거의 필수적으로 사용되는 기능이기 때문에 습관화를 시키는 것이 중요하다고 생각합니다.

## Docstring
docstring은 파이썬 함수에 대한 상세스펙을 사전에 작성하여 함수 사용자의 이행도를 증진시키는 기능입니다. 함수명 아래에 세개의 따옴표로 docstring 영역을 표시하여 docstring을 작성할 수 있습니다. 예시는 아래와 같습니다.

```python
def is_help_command(user_input: str) -> bool:
    """
    Input:
        - user_input : 문자열값으로 사용자가 입력하는 문자
    Output:
        - 입력한 값이 대소문자 구분없이 "H" 또는 "HELP"일 경우 True,
          그렇지 않을 경우 False를 반환함
    """
    return True if user_input.upper() in ["H", "HELP"] else False
```

## Coding convention
거의 모든 코딩 작업은 팀워크로 이루어집니다. 각자 서로의 코드를 작성하고 공유하여 결과물을 내놓기 위해서는 사람의 이해를 돕기 위한 코딩 작성 규약이 필요합니다. 이를 코딩 컨벤션이라고 합니다. 사실 코딩 컨벤션에 명확한 규칙은 없습니다. 때로는 팀마다, 프로젝트마다 다른 규약을 사용할 수도 있습니다. 제일 중요한 것은 일관성입니다. 한 그룹 내에서는 그룹에서 지정한 규약을 모두 지키면서 코딩해야 최대의 작업 효율을 보여줄 수 있습니다. 그래도 보편적으로 사용되는 코딩 컨벤션은 아래와 같습니다.

1. 4 space 권장

    코딩 컨벤션에 관련된 이슈 중 Tab vs 4 Space 논쟁이 있습니다. code의 indentation을 구성할 때 tab을 사용하느냐 4 space를 사용하느냐의 문제는 사실 어느 것이 우월하다기 보다는 혼합하지 않으면 됩니다. (사실 일반적으로 4 space를 권장하기는 하지만 저는 tab을 사용하고 있습니다. 최신 editor는 모두 tab을 자동으로 4 space로 변환하는 기능을 가지고 있기 때문에 큰 문제는 되지 않습니다.)

2. 한 줄은 최대 79자까지
3. 불필요한 공백은 피함
4. = 연산자는 1칸 이상 안 띄움
5. 코드의 마지막에는 항상 한 줄 추가
6. 함수명은 소문자로 구성, 필요하면 밑줄로 나눔

파이썬 코딩 컨벤션의 기준으로 PEP8이라는 규약이 존재합니다. flake8 module을 통해 자동으로 코드가 PEP8 기준에 부합하는지 검사할 수 있습니다.

<br/>

### References
1. NAVER Connect Foundation
