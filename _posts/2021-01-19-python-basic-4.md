---
layout: post
title: "Python Basic : 4. Conditionals and Loops"
category: Python
date: 2021-01-19 19:20:00 +0900
---
## Intro
>프로그래밍을 배울 때 사용되는 논리적인 사고 학습에 핵심이 되는 조건문과 반복문에 대하여 공부합니다.

## 조건문(Condition)
조건문은 조건에 따라 특정한 동작을 하게하는 명령어입니다. 조건문은 조건을 나타내는 기준과 실행해야 할 명령으로 구성됩니다. 그리고 조건의 참, 거짓에 따라 실행해야 할 명령이 수행되거나 되지 않습니다. 파이썬은 조건문으로 if , else , elif 등의 예약어를 사용합니다. 기본적인 조건문은 아래와 같습니다.
```python
if <조건>:            # if를 쓰고 조건 삽입 후 “:” 입력
    <수행 명령1-1>      # 들여쓰기(indentation)후 수행명령 입력
    <수행 명령1-2>      # 같은 조건하에 실행일 경우 들여쓰기 유지
else:                # 조건이 불일치할 경우 수행할 명령 block
    <수행 명령2-1>      # 조건 불일치 시 수행할 명령 입력
    <수행 명령2-2>      # 조건 불일치 시 수행할 명령 들여쓰기 유지
```

조건문을 표현할 때는 주로 비교연산자를 사용합니다. 집합의 논리 키워드를 함께 사용하는 경우도 있습니다.
<p align="center">
  <img src="https://user-images.githubusercontent.com/77161691/107353596-90ec8300-6b10-11eb-9613-c24477d75010.png" alt="comparison operator"/>
   comparison operator
</p>

```python
a = 8
b = 5
if a == 8 and b == 4    # False
if a > 7 or b > 7       # True
if not (a > 7)          # False
```

조건문을 사용하면 참인 경우와 거짓인 경우를 한 줄에 나타낼 수도 있습니다. 이러한 표현법을 삼항 연산자(Ternary operators)라고 부릅니다.
```python
>>> value = 12
>>> is_even = True if value % 2 == 0 else False
>>> print(is_even)
True
```

## 반복문(Loop)
반복문은 정해진 동작을 반복적으로 수행하게 하는 명령문입니다. 반복문은 반복 시작 조건, 종료 조건, 수행 명령으로 구성됩니다. 반복문 역시 들여쓰기와 block으로 구문을 구분합니다. 파이썬은 반복문으로 for, while 등의 명령 키워드를 사용합니다.

### for문
기본적인 for 반복문은 아래와 같습니다.
```python
for looper in [1,2,3,4,5]:
    print ("hello")
for looper in [1,2,3,4,5]:
    print (looper)
```

어떠한 작업을 정해진 횟수만큼 수행할 때 원소의 개수가 작업 횟수인 리스트를 반복 조건에 사용해야 합니다. python에서는 range()를 통해 이를 구현할 수 있습니다.
```python
for looper in [1,2,3,4,5]:
    print ("hello")
for looper in range(5):   # same as previous loop
    print ("hello")
```

반복문은 대부분 0부터 반복을 시작합니다. 이것은 일종의 관례로, 1부터 시작하는 언어도 존재하지만 Python은 기본적으로 0부터 시작하고 2진수도 0부터 시작하기 때문에 0부터 시작하는 걸 권장합니다.

### while문
기본적인 while 반복문은 아래와 같습니다.
```python
i = 1
while i < 10:
    print (i)
    i += 1
```

while문에서는 break와 continue, else 등의 제어 키워드가 사용됩니다.

1. break: 특정 조건에서 반복 종료
    ```python
    for i in range(10):
       if i == 5: break    # i가 5가 되면 반복 종료
       print (i)
    print (“EOP”)          # 반복 종료 후 “EOP” 출력
    ```

2. continue: 특정 조건에서 남은 반복 명령을 skip
    ```python
    for i in range(10):
       if i == 5: continue # i가 5가 되면 i를 출력하지 않음
       print (i)
    print (“EOP”)          # 반복 종료 후 “EOP” 출력
    ```

3. else: 반복 조건이 만족하지 않을 경우 반복 종료 시 1회 수행
    ```python
    i = 0
    while i < 10:
       print (i,)
       i += 1
    else:
       print ("EOP")
    ```
