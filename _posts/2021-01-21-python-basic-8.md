---
layout: post
title: "Python Basic : 8. Object Oriented Programming"
category: Python
date: 2021-01-21 19:00:00 +0900
---
## Intro
>객체 지향 프로그래밍 언어, Object Oriented Programming(OOP)에 대하여 공부합니다.

## 객체 지향 프로그래밍 언어(Object Oriented Programming, OOP)
객체는 실생활에서 일종의 물건이라고 생각할 수 있습니다. 각 객체는 속성(Attribute)과 행동(Action)을 가지고 있습니다. OOP는 이러한 객체 개념을 프로그램으로 표현하여 속성은 변수(variable), 행동은 함수(method)로 표현합니다. 파이썬 또한 객체 지향 프로그래밍 언어입니다. OOP는 설계도에 해당하는 클래스(class)와 실제 구현체인 인스턴스(instance)로 나뉩니다. 파이썬에서 객체를 Class로 구현하는 코드 예시는 아래와 같습니다.

```python
class SoccerPlayer(object):
    def __init__(self, name, position, back_number):
        self.name = name
        self.position = position
        self.back_number = back_number
    def change_back_number(self, new_number):
        print("선수의 등번호를 변경합니다 : From %d to %d" % (self.back_number, new_number))
        self.back_number = new_number

jinhyun = SoccerPlayer("Jinhyun", "MF", 10)
print("현재 선수의 등번호는 :", jinhyun.back_number)
jinhyun.change_back_number(5)
print("현재 선수의 등번호는 :", jinhyun.back_number)
```

class 선언은 ```class SoccerPlayer(object):``` 과 같이 할 수 있습니다. Object는 python3에서 자동 상속받습니다. 변수와 Class명, 함수명은 짓는 방식이 존재합니다. 파이썬 함수/변수명은 주로 띄어쓰기 부분에 “_” 를 추가하는 snake_case를 사용하고 Class명은 주로 띄어쓰기 부분에 대문자를 사용하는 CamelCase를 사용합니다. Attribute 추가는 __init___ , self을 이용하여 다음과 같이 할 수 있습니다. ```def __init__(self, name, position, back_number):``` __init__은 객체 초기화 예약 함수입니다. method(Action) 추가는 기존 함수와 같으나, 반드시 self를 추가해야만 class 함수로 인정됩니다. 추가하는 문법은 다음과 같습니다. ```def change_back_number(self, new_number):```

만들어둔 class를 이용하여 object를 생성하기 위해서는 Object 이름 선언과 함께 초기값 입력이 필요합니다. ```jinhyun = SoccerPlayer("Jinhyun", "MF", 10)``` object의 method를 이용하는 문법은 다음과 같습니다. ```jinhyun.change_back_number(5)```

객체 지향 언어의 큰 특징에는 세 가지가 있습다.

1. Inheritance(상속)
    상속은 부모 클래스로부터 속성과 Method를 물려받은 자식 클래스를 생성 하는 것입니다.
    ```python
    class Employee(Person): # 부모 클래스 Person으로 부터 상속
        def __init__(self, name, age, gender, salary, hire_date):
            super().__init__(name, age, gender) # 부모객체 사용
            self.salary = salary
            self.hire_date = hire_date # 속성값 추가
        def do_work(self): # 새로운 메서드 추가
            print("열심히 일을 합니다.")
        def about_me(self): # 부모 클래스 함수 재정의
            super().about_me() # 부모 클래스 함수 사용
            print("제 급여는 ", self.salary, "원 이구요, 제 입사일은 ", self.hire_date, " 입니다.")
    ```

2. Polymorphism(다형성)
    같은 이름을 가진 메소드의 내부 로직을 다르게 작성하는 것입니다. Dynamic Typing 특성으로 인해 파이썬에서는 같은 부모 클래스의 상속에서 주로 발생합니다.
    ```python
    class Animal:
        def __init__(self, name): # Constructor of the class
            self.name = name
        def talk(self): # Abstract method, defined by convention only
            raise NotImplementedError("Subclass must implement abstract method")

    class Cat(Animal):
        def talk(self):
           return 'Meow!'

    class Dog(Animal):
        def talk(self):
           return 'Woof! Woof!'

    animals = [Cat('Missy'), Cat('Mr. Mistoffelees'), Dog('Lassie')]
    for animal in animals:
       print(animal.name + ': ' + animal.talk())
    ```

3. Visibility(가시성)
    가시성은 객체의 정보를 볼 수 있는 레벨을 조절하는 것입니다. 누구나 객체 안에 모든 변수를 볼 필요가 없기 때문에 객체를 사용하는 사용자가 필요 없는 정보에는 접근 하지 않아도 되게 하는 것입니다.
    ```python
    class Product(object):
        pass
    class Inventory(object):
        def __init__(self):
           self.__items = []
        def add_new_item(self, product):
           if type(product) == Product:
               self.__items.append(product)
               print("new item added")
           else:
               raise ValueError("Invalid Item")
        def get_number_of_items(self):
           return len(self.__items)

    my_inventory = Inventory()
    my_inventory.add_new_item(Product())
    my_inventory.add_new_item(Product())
    print(my_inventory.get_number_of_items())

    print(my_inventory.__items)
    my_inventory.add_new_item(object)
    ```

## Decorate
Decorate는 함수를 parameter로 받는 경우에 대해 표기의 간편성을 위하여 '@'를 사용하는 방법입니다.
```python
def star(func):
    def inner(*args, **kwargs):
        print("*" * 30)
        func(*args, **kwargs)
        print("*" * 30)
    return inner
def percent(func):
    def inner(*args, **kwargs):
        print("%" * 30)
        func(*args, **kwargs)
        print("%" * 30)
    return inner

@star
@percent
def printer(msg):
print(msg)
printer("Hello")
```

결과
```python
******************************
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Hello
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
******************************
```
