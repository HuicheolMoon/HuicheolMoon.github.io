---
layout: post
title: "Python Basic : 7. Pythonic Code"
category: Python
date: 2021-01-20 19:10:00 +0900
---
## Intro
>파이썬 특유 문법을 의미하는 pythonic code에 대해 공부합니다.

## Pythonic code
Pythonic code는 파이썬 스타일의 코딩 기법을 의미합니다. 파이썬 특유의 문법을 활용하여 효율적으로 코드를 표현할 수 있습니다. 그러나 더 이상 파이썬 특유의 기법은 아닙니다. 많은 언어들이 서로의 장점을 채용하여 발전해나가고 있습니다. 고급 코드를 작성하기 위해서는 Pythonic code skill이 필수적입니다. Pythonic code의 장점은 아래 세 가지로 요약할 수 있습니다.

1. 남 코드에 대한 이해도

    많은 개발자들이 python 스타일로 코딩한다.

2. 효율

    단순 for loop append보다 list가 조금 더 빠르다. 익숙해지면 코드도 짧아진다.

3. 간지

    쓰면 왠지 코드 잘 짜는 거처럼 보인다.

## split
split 함수는 string type의 값을 기준값으로 나눠서 list 형태로 변환하는 함수입니다.
```python
>>> items = 'zero one two three'.split()        # 빈칸을 기준으로 문자열 나누기
>>> print (items)
['zero', 'one', 'two', 'three']
>>> example = 'python,java,javascript'          # ","을 기준으로 문자열 나누기
>>> example.split(",")
['python', ‘java', 'javascript']
>>> a, b, c = example.split(",")                # 리스트에 있는 각 값을 a,b,c 변수로 unpacking
>>> example = ‘teamlab.technology.io'
>>> subdomain, domain, tld = example.split('.') # "."을 기준으로 문자열 나누기 → Unpacking
```

## join
join 함수는 string으로 구성된 list를 합쳐 하나의 string으로 반환하는 함수입니다.
```python
>>> colors = ['red', 'blue', 'green', 'yellow']
>>> result = ''.join(colors)
>>> result
'redbluegreenyellow'
>>> result = ' '.join(colors)  # 연결 시 빈칸 1칸으로 연결
>>> result
'red blue green yellow'
>>> result = ', '.join(colors) # 연결 시 ", "으로 연결
>>> result
'red, blue, green, yellow'
>>> result = '-'.join(colors)  # 연결 시 "-"으로 연결
>>> result
'red-blue-green-yellow'
```

## List comprehension
개인적으로 pythonic code의 꽃이라고 생각하는 List comprehension입니다. List comprehension은 기존 List를 사용하여 간단히 다른 List를 만드는 기법입니다. 파이썬에서 가장 많이 사용되는 기법 중 하나이고 일반적으로 for + append 보다 속도가 빠릅니다. 아래에서 for + append 방식과 코드를 비교해보겠습니다.
```python
>>> result = []
>>> for i in range(10):              # for + append
...   result.append(i)
...
>>> result
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```python
>>> result = [i for i in range(10)]  # list comprehension
>>> result
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> result = [i for i in range(10) if i % 2 == 0]
>>> result
[0, 2, 4, 6, 8]
```

## enumerate
enumerate 함수는 list의 element를 추출할 때 번호를 붙여서 추출합니다. 저는 for문에서 element와 index를 둘 다 사용해야 할 때 주로 사용하는 것 같습니다.
```python
>>> mylist = ['a', 'b', 'c', 'd']
>>> list(enumerate(mylist)) # list의 있는 index와 값을 unpacking하여 list로 저장
[(0, 'a'), (1, 'b'), (2, 'c'), (3, 'd')]
```

## zip
zip 함수는 두 list의 값을 병렬적으로 추출합니다.
```python
>>> alist = ['a1', 'a2', 'a3']
>>> blist = ['b1', 'b2', 'b3']
>>> for a, b in zip(alist, blist): # 병렬적으로 값을 추출
...   print (a,b)
...
a1 b1
a2 b2
a3 b3
```

## lambda
lambda는 함수 이름 없이 함수처럼 쓸 수 있는 익명함수입니다. 아래와 같이 사용할 수 있습니다.
```python
def general_function(x, y):
    return x + y
print(f(1, 4))

lambda_function = lambda x, y: x + y
    print(lambda_function(1, 4))
```

lambda는 어려운 문법, 테스트의 어려움, 문서화 docstring 지원 미비, 코드 해석의 어려움, 이름이 존재하지 않는 함수의 출현 등 여러 문제를 가지고 있습니다. PEP8에서는 lambda의 사용을 권장하지 않습니다. 하지만 어쩔 수 없이 사용해야 하는 경우가 존재합니다.

## map
map 함수는 iterable을 함수의 input으로 하여 출력되는 output을 원소로 하는 list를 반환합니다. 실행시점에 값을 생성하기 때문에 메모리를 효율적으로 사용할 수 있습니다.
```python
>>> ex = [1,2,3,4,5]
>>> print(list(map(lambda x: x+x, ex)))
[2, 4, 6, 8, 10]
```

# reduce
reduce 함수는 iterable의 함수의 input으로 하여 출력되는 output을 누계한 결과를 반환합니다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/77161691/107365921-cf8a3980-6b20-11eb-8c7a-24e73026c82b.png" alt="reduce"/>
   reduce
</p>

위 skill들 각각의 용례는 쉬워보이지만 이 skill들을 잘 배합하여 원하는 코드를 작성하는 것은 매우 어려운 일입니다. 모두 숙지하고 자유자재로 활용할 수 있을 만큼 코딩 연습이 필요합니다.

<br/>

### References
1. [Stackoverflow: Queue](https://stackoverflow.com/questions/63113107/queue-enqueue-vs-dequeue-fill-out-table-shift-needed)
