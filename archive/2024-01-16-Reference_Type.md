---
title:  "[Java] Primitive vs Reference"
excerpt: ""

categories:
  - Spring
tags:
  - [spring, java]

breadcrumb: true
toc: true
toc_sticky: true
 
date: 2024-01-16
last_modified_at: 2024-01-17
---

## Primitive Type
- int, long, short, byte, char, float, double, boolean 총 8개의 type을 가진다<br>
- 변수에 사용할 값을 직접 넣어 저장하는 data type<br>
- Stack 영역에 저장된다<br>
- null 값을 가질 수 없다<br>
- long 형의 경우 8byte의 정수 데이터임을 알려주기 위해 숫자 뒤에 `L`을 붙인다. 만약 붙이지 않고 2^31 이상인 값을 넣게 되면, int형으로 인식하여 컴파일 에러가 발생한다.<br>
- 
```java
int a = 1;
long l = 2147483648L;
float f = 2.1F;
double d = 2.1;
```


## Reference Type
- class type, interface type, array type, enum type 등이 있다.<br>
- 
```java
TwoNumber twonumber
int[] a;
String s;
```

### String
String은 값을 직접 넣어 저장하는 것 같지만, 클래스이기 때문에 reference type이다.<br>

## Call by value vs Call by Reference


