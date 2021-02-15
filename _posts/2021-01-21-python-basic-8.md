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
class User(object):
    def __init__(self, name, location, number):
        self.name = name
        self.location = location
        self.number = number
    def change_number(self, new_number):
        self.number = new_number

Huicheol = User("Huicheol", "Seoul", 1060)
print("현재 이용자의 위치는 :", Huicheol.location)
Huicheol.change_number(1080)
print("현재 유저의 번호는:", Huicheol.number)
```

객체 지향 언어의 큰 특징에는 세 가지가 있습니다.

1. Inheritance(상속)
    상속은 부모 클래스로부터 속성과 Method를 물려받은 자식 클래스를 생성 하는 것입니다.
    ```python
    class Player(User): # 부모 클래스 User로부터 상속
        def __init__(self, name, location, number, level, money):
            super().__init__(name, location, number)
            self.level = level
            self.money = money
        def work(self):
            print("열심히 일합니다.")
    ```

2. Polymorphism(다형성)
    같은 이름을 가진 메소드의 내부 로직을 다르게 작성하는 것입니다. Dynamic Typing 특성으로 인해 파이썬에서는 같은 부모 클래스의 상속에서 주로 발생합니다.
    ```python
    class Animal:
        def __init__(self, name):
            self.name = name
        def talk(self):
            raise NotImplementedError("Subclass must implement abstract method")

    class Cat(Animal):
        def talk(self):
           return '야옹!'

    class Dog(Animal):
        def talk(self):
           return '멍멍!'

    animals = [Cat('고냥이'), Cat('야옹이'), Dog('멍멍이')]
    ```

3. Visibility(가시성)
    가시성은 객체의 정보를 볼 수 있는 레벨을 조절하는 것입니다. 누구나 객체 안에 모든 변수를 볼 필요가 없기 때문에 사용자가 필요 없는 정보에는 접근하지 않아도 되는 것입니다.
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
        print("*" * 10)
        func(*args, **kwargs)
        print("*" * 10)
    return inner
def percent(func):
    def inner(*args, **kwargs):
        print("%" * 10)
        func(*args, **kwargs)
        print("%" * 10)
    return inner

@star
@percent
def printer(msg):
print(msg)
printer("Hello")
```

결과
```python
**********
%%%%%%%%%%
Hello
%%%%%%%%%%
**********
```

<br/>

### References
1. NAVER Connect Foundation: Boostcamp AI Tech
