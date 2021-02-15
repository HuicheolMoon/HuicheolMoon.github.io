---
layout: post
title: "Python Basic : 10. Exception / File / Log Handling"
category: Python
date: 2021-01-22 19:00:00 +0900
---
## Intro
>프로그램을 제대로 만들기 위해 알아야 하는 예외 처리와 파일 다루기에 대해서 배웁니다.

## Exception
프로그램을 사용할 때는 다양한 오류들이 발생할 수 있습니다. 주소를 입력하지 않고 배송 요청을 한다던지, 저장도 안 했는데 컴퓨터 전원이 나간다던지 예상치 못한 많은 일(예외)들이 발생합니다. 예외가 발생할 경우에는 후속조치등 대처가 필요합니다. 없는 파일을 호출한 경우에는 파일 없음을 알리고, 게임이 비정상적으로 종료되면 게임 정보를 저장하는 등 모든 잘못된 상황에 대처가 필요합니다. 이를 Exception Handling이라고 합니다. 파이썬에서 예외를 처리하는 도구에는 try ~ except 문법이 있습니다.

```python
try:
    예외 발생 가능 코드
except <Exception Type>:
    예외 발생시 대응하는 코드
else:
    예외가 발생하지 않을 때 동작하는 코드
finally:
    예외 발생 여부와 상관없이 실행됨

# example : 0으로 숫자를 나눌 때 예외 처리하기
for i in range(10):
    try:
        print(10 / i)
    except ZeroDivisionError:
        print("Not divided by 0")
```

파이썬에서 기본적으로 제공하는 예외는 Built-in Exception라고 합니다.

|Exception|내용|
|:---:|:---:|
|IndexError|List의 Index 범위를 넘어갈 때|
|NameError|존재하지 않은 변수를 호출 할 때|
|ZeroDivisionError|0으로 숫자를 나눌 때|
|ValueError|변환할 수 없는 문자/숫자를 변환할 때|
|FileNotFoundError|존재하지 않는 파일을 호출할 때|

필요에 따라 강제로 Exception을 발생시켜야 하는 경우도 있는데 이 때는 raise를 사용합니다.
```python
raise <Exception Type>(예외정보)
```

```python
while True:
    value = input("변환할 정수 값을 입력해주세요")
    for digit in value:
        if digit not in "0123456789":
            raise ValueError("숫자값을 입력하지 않으셨습니다")
    print("정수값으로 변환된 숫자 -", int(value))
```

특정 조건에 만족하지 않을 경우에 예외를 발생시키고 싶은 경우에는 assert를 사용합니다.
```python
def get_binary_nmubmer(decimal_number):
    assert isinstance(decimal_number, int)
    return bin(decimal_number)

print(get_binary_nmubmer(10))
```

## File Handling
파일 시스템은 OS에서 파일을 저장하는 트리구조 저장 체계입니다. 파이썬은 파일 처리를 위해 open 키워드를 사용합니다.
```python
f = open("<파일이름>", "접근 모드")
f.close()
```

|접근 모드|설명|
|:---:|---|
|r|읽기모드 - 파일을 읽기만 할 때 사용|
|w|쓰기모드 - 파일에 내용을 쓸 때 사용|
|a|추가모드 - 파일의 마지막에 새로운 내용을 추가 시킬 때 사용|

## Log Handling
프로그램이 실행되는 동안 일어나는 정보를 기록을 남기는 것을 Log라고 합니다. Log는 유저의 접근, 프로그램의 Exception, 특정 함수의 사용을 포함합니다. Console 화면에 출력, 파일에 남기기, DB에 남기기 등등의 방법을 통해 log를 기록할 수 있으며 기록된 log를 분석하여 의미있는 결과를 도출 할 수 있습니다. 파이썬에서는 logging 모듈로 log 관리를 지원합니다. logging level, 즉 프로그램 진행 상황에 따라 다른 Level의 Log를 출력하여 개발 시점, 운영 시점 마다 다른 Log가 남을 수 있도록 지원합니다.

|Logging Level|설명|예시|
|:---:|---|---|
|DEBUG|개발시 처리 기록을 남겨야하는 로그 정보를 남김|- 다음 함수로 A 를 호출함<br/>- 변수 A 를 무엇으로 변경함|
|INFO|처리가 진행되는 동안의 정보를 알림|- 서버가 시작되었음<br/>- 사용자 A가 프로그램에 접속함<br/>- 서버가 종료됨|
|WARNING|사용자가 잘못 입력한 정보나 처리는 가능하나 원래 개발시 의도치 않는 정보가 들어왔을 때 알림|- Str입력을 기대했으나, Int가 입력됨<br/> -> Str casting으로 처리함<br/>- 함수에 argument로 이차원 리스트를 기대했으나<br/> -> 일차원 리스트가 들어옴, 이차원으로 변환후 처리|
|ERROR|잘못된 처리로 인해 에러가 났으나, 프로그램은 동작할 수 있음을 알림|- 파일에 기록을 해야하는데 파일이 없음<br/> -> Exception 처리후 사용자에게 알림<br/>- 외부서비스와 연결 불가|
|Critical|잘못된 처리로 데이터 손실이나 더이상 프로그램이 동작할 수 없음을 알림|- 잘못된 접근으로 해당 파일이 삭제됨<br/>- 사용자의 의한 강제 종료|
