---
layout: post
title: "Python Basic : 6. Data Structure"
category: Python
date: 2021-01-20 19:00:00 +0900
---
## Intro
>파이썬에서 자주 사용되는 자료 구조인 스택과 큐(stack & queue with list), 튜플과 집합(tuple & set), 딕셔너리(dictionary), collections 모듈에 대하여 공부합니다.

## Stack
스택은 나중에 넣은 데이터를 먼저 반환하도록 설계된 메모리 구조입니다. 이 성질을 Last In First Out(LIFO)이라고 부릅니다. 스택에서 Data의 입력을 Push, 출력을 Pop이라고 합니다. 파이썬에서는 리스트를 사용하여 스택 구조를 구현할 수 있습니다. 이 때 push 기능은 append(), pop 기능은 pop()를 사용합니다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/77161691/107361457-c0a08880-6b1a-11eb-85b1-e5bc8126e848.png" alt="stack structure"/>
   stack structure
</p>

```python
>>> a = [1, 2, 3]
>>> a.append(4)
>>> a.append(5)
>>> a.pop()
5
>>> a.pop()
4
```

## Queue
큐는 먼저 넣은 데이터를 먼저 반환하도록 설계된 메모리 구조입니다. 이 성질을 First In First Out(FIFO)이라고 부릅니다. Stack과 반대되는 개념이라고 생각하면 편합니다. 파이썬에서는 큐도 리스트를 사용하여 구현합니다. 이 때 put 기능은 append(), get 기능은 pop(0)를 사용합니다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/77161691/107361673-170dc700-6b1b-11eb-8ba7-97966bb99ce5.png" alt="queue structure"/>
   queue structure
</p>

```python
>>> a = [1,2,3]
>>> a.append(4)
>>> a.append(5)
>>> a.pop(0)
1
>>> a.pop(0)
2
```

## Tuple
튜플은 값의 변경이 불가능한 리스트입니다. 선언 시 '[ ]'(대괄호)가 아닌 '( )'(소괄호)를 사용합니다. 리스트의 연산, 인덱싱, 슬라이싱 등을 아래와 같이 동일하게 사용할 수 있습니다. 원소를 변경하는 작업에 대해서는 error를 발생시킵니다. 그렇기 때문에 프로그램을 작동하는 동안 변경되지 않아야 하는 데이터를 저장하는 데 용이합니다. 또한 함수의 반환 값 등 사용자의 실수에 의한 에러를 사전에 방지할 수 있습니다.
```python
>>> t = (1,2,3)
>>> print (t + t , t * 2)
(1, 2, 3, 1, 2, 3) (1, 2, 3, 1, 2, 3)
>>> len(t)
3
>>> t[1] = 5
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```

## Set
집합은 값을 순서없이 저장하고 중복을 불허하는 자료형입니다. set 객체 선언을 이용하여 객체를 생성할 수 있습니다. 수학에서의 집합과 동일하게 연산할 수 있습니다.
```python
>>> s = set([1,2,3,1,2])
>>> s
{1, 2, 3}
>>> s.add(1)
>>> s
{1, 2, 3}
>>> s.remove(1)
>>> s
{2, 3}
>>> s.update([1,4,5])
>>> s
{1, 2, 3, 4, 5}
>>> s.discard(3)
>>> s
{1, 2, 4, 5}
>>> s.clear()
```

```python
>>> s1 = set([1,2,3,4,5])
>>> s2 = set([3,4,5,6,7])
>>> s1.union(s2)
{1, 2, 3, 4, 5, 6, 7}
>>> s1 | s2
{1, 2, 3, 4, 5, 6, 7}
>>> s1.intersection(s2)
{3, 4, 5}
>>> s1 & s2
{3, 4, 5}
>>> s1.difference(s2)
{1, 2}
>>> s1 - s2
{1, 2}
```

## Dictionary
딕셔너리는 데이터를 저장 할 때 구분 지을 수 있는 값을 함께 저장합니다. 구분을 위한 데이터 고유 값을 Key라고 하고, 해당 Key가 가리키는 데이터 값을 Value라고 합니다. 딕셔너리에서는 key로 value를 검색할 수 있습니다. 딕셔너리라는 이름은 python에서 사용되는 이름으로 다른 언어에서는 Hash Table이라는 용어를 사용합니다.
```python
>>> country_code = {＂America＂: 1, ＂Korea＂: 82, ＂China＂: 86, ＂Japan＂: 81}
>>> country_code
{＇America＇: 1, ＇China＇: 86, ＇Korea＇: 82, ＇Japan＇: 81}
>>> country_code.items()
Dict_items([(＇America＇, 1), (＇China＇, 86), (＇Korea＇, 82), (＇Japan＇, 81)])
>>> country_code.keys()
Dict_keys(["America", "China", "Korea", "Japan"])
>>> country_code["German"]= 49
>>> country_code
{'America': 1, 'German': 49, 'China': 86, 'Korea': 82, 'Japan': 81}
>>> country_code.values()
dict_values([1, 49, 86, 82, 81])
>>> "Korea" in country_code.keys() # Key값에 "Korea"가 있는지 확인
True
>>> 82 in country_code.values()    # Value값에 82가 있는지 확인
True
```

# collections
collections는 List, Tuple, Dict에 대한 Python module입니다.

1. Deque
    deque는 Stack과 Queue 를 지원하는 모듈입니다. 기존 List에 비해 빠른 자료 저장 방식을 지원합니다. deque는 rotate, reverse등 Linked List의 특성을 가지고 있습니다.
    ```python
    from collections import deque
    deque_list = deque()
    for i in range(10):
        deque_list.append(i)
    print(deque_list)
    ```

2. Counter
    Counter는 Sequence type의 data element들의 갯수를 dict 형태로 반환합니다.
    ```python
    >>> from collections import Counter
    >>> c = Counter('learning')
    >>> print(c)
    Counter({'n': 2, 'l': 1, 'e': 1, 'a': 1, 'r': 1, 'i': 1, 'g': 1})
    ```

<br/>

### References
1. NAVER Connect Foundation: Boostcamp AI Tech
2. [Stackoverflow: Queue](https://stackoverflow.com/questions/63113107/queue-enqueue-vs-dequeue-fill-out-table-shift-needed)
