---
layout: post
title: "Python Basic : 11. Python Data Handling"
category: Python
date: 2021-01-22 19:10:00 +0900
---
## Intro
>파이썬에서 다룰 수 있는 CSV, 웹, XML, JSON 네 가지 데이터 타입에 대해서 공부합니다.

## CSV(Comma Separate Value)
CSV는 필드를 쉼표(,)로 구분한 텍스트 파일입니다. 엑셀 양식의 데이터를 프로그램에 상관없이 쓰기 위한 데이터 형식입니다. 탭(TSV), 빈칸(SSV) 등으로 구분해서 만들기도 합니다. 통칭하여 character-separated values(CSV)라고 합니다. 엑셀에서는 '다름 이름 저장' 기능으로 사용 가능합니다.

## Web
World Wide Web(WWW), 줄여서 웹이라고 부릅니다. 우리가 늘 쓰는 인터넷 공간의 정식 명칭입니다. 팀 버너스리에 의해 1989년 처음 제안되었으며, 원래는 물리학자들간 정보 교환을 위해 사용되었습니다. 데이터 송수신을 위한 HTTP 프로토콜 사용하고 데이터를 표시하기 위해 HTML(Hyper Text Markup Language) 형식을 사용합니다. HTML은 웹 상의 정보를 구조적으로 표현하기 위한 언어입니다. 제목, 단락, 링크 등 요소 표시를 위해 Tag를 사용하고 모든 요소들은 '<>' 안에 둘러 쌓여 있습니다. 모든 HTML은 트리 모양의 포함관계를 가지고 일반적으로 웹 페이지의 HTML 소스파일은 컴퓨터가 다운로드 받은 후 웹 브라우저가 해석/표시합니다. 많은 데이터들이 웹을 통해 공유되기 때문에 Web을 알고 다루는 것은 데이터 사이언스에 중요합니다.

## XML
XML은 데이터의 구조와 의미를 설명하는 TAG(MarkUp)를 사용하여 표시하는 언어입니다. TAG와 TAG 사이에 값이 표시되고 구조적인 정보를 표현할 수 있습니다. HTML과 문법이 비슷한 대표적인 데이터 저장 방식입니다. 정보의 구조에 대한 정보인 스키마와 DTD 등으로 메타정보가 표현되며, 용도에 따라 다양한 형태로 변경이 가능합니다. XML은 컴퓨터간에 정보를 주고받기 매우 유용한 저장 방식으로 쓰이고 있습니다.

## JSON
JSON(JavaScript Object Notation)은 원래 웹 언어인 Java Script의 데이터 객체 표현 방식입니다. 간결성으로 기계/인간이 모두 이해하기 편하고 데이터 용량이 적으며 Code로의 전환이 쉽다는 장점이 있습니다. 그렇기에 XML의 대체제로 많이 활용되고 있습니다. 파이썬에서는 json 모듈을 사용하여 쉽게 파싱 및 저장이 가능합니다. 데이터 저장 및 읽기는 dict type과 상호 호환이 가능합니다. 웹에서 제공하는 API는 대부분 정보 교환 시에 JSON을 활용합니다.

<br/>

### References
1. NAVER Connect Foundation: Boostcamp AI Tech
