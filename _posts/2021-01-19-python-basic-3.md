---
layout: post
title: "Python Basic : 3. Function and Console I/O"
category: Python
date: 2021-01-19 19:10:00 +0900
---
## Intro
>함수란 프로그램을 개발할 때 사용되는 코드의 논리적 단위입니다.콘솔은 터미널이라고 불리는 컴퓨터 프로그램입니다. 이번에는 함수와 콘솔 인/아웃에 대해서 배웁니다.

## 함수(Function)
함수는 어떤 일을 수행하는 코드의 덩어리라고 할 수 있습니다. 함수는 반복적인 수행을 1회만 작성 후 호출할 수 있으며 코드를 논리적인 단위로 분리할 수 있기 때문에 코드 작성에 편의를 가져다줍니다. 이는 인터페이스만 알면 타인의 코드도 쉽게 사용할 수 있게 만들어줍니다. 이러한 경향을 캡슐화라고 합니다.

함수를 선언하기 위해서는 함수의 이름과 parameter가 필요합니다. return value와 indentation 도 함수 구성 요소에 포함됩니다. (optional)
```python
def 함수 이름 (parmaeter #1,…,):
    수행문 #1(statements)
    수행문 #2(statements)
    return <반환값>

# 사각형의 넓이를 구하는 함수 예시
def calculate_rectangle_area (x , y):
    return x * y # 가로, 세로를 곱해서 반환
```

컴퓨터는 코드 내에서 함수를 제외한 메인 프로그램부터 실행을 시작합니다. 그리고 메인 프로그램에서 함수가 호출되는 경우 함수 부분으로 돌아가서 함수를 실행한 후 다시 되돌아오는 방식을 취합니다.

프로그래밍에서의 함수에서 parameter와 argument는 혼동될 수 있는 개념입니다. parameter는 함수의 input interface이고 argument는 parameter에 대입된 실제 값을 말합니다.
```python
def f(x):           # x -> parameter
return 2 * x + 7
```
```python
>>> print(f(2))     # 2 -> argument
11
```

함수는 parameter와 return value의 유무에 따라 4가지 형태를 가지고 있습니다.

<p align="center">
  <img src="https://user-images.githubusercontent.com/77161691/107351760-55e95000-6b0e-11eb-8fcf-b138dd0c1f16.png" alt="function class"/>
   function class
</p>

## Console in/out
input()함수는 콘솔창에서 문자열을 입력 받는 함수입니다.
```python
# console_test.py
print ("Enter your name:")
somebody = input() # 콘솔창에서 입력한 값을 somebody에 저장
print ("Hi", somebody, "How are you today?")
```
```python
python console_test.py
Enter your name:
Huichoel Moon
Hi Huichoel Moon How are you today?
```

콤마(,)를 사용할 경우에는 print 문이 연결됩니다.
```python
>>> print ("Hello World!", "Hello Again!!!")    # , 사용
Hello World! Hello Again!!!                     # 실행 시 두 문장이 연결 돼서 출력됨
```

```python
temperature = float(input("온도를 입력하세요 :")) # 입력 시 바로 형 변환 하기
print(temperature)
```

```python
python temperature.py
온도를 입력하세요 : 103
103.0
```

어떤 경우에는 형식에 맞춰서 출력해야 할 때가 있습니다. 이 경우에는 세 가지 종류의 결과 formatting을 통해 print문을 구성할 수 있습니다.
```python
print(1,2,3)
print("a" + " " + "b" + " " + "c")
print("%d %d %d" % (1,2,3))             # (1) % string
print("{} {} {}".format("a","b","c"))   # (2) format 함수
print(f"value is {value}")              # (3) fstring
```

최근에는(python 3.6 이후) PEP498에 근거한 fstring 방식을 선호하는 추세입니다.
