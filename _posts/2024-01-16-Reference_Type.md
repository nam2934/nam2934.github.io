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
last_modified_at: 2024-01-16
---

## Primitive Type
int, long, float, double, boolean 등 변수에 사용할 값을 직접 넣어 저장하는 data type<br>
```
int a = 0;
float b = 2.1f;
```


## Reference Type
`TwoNumber twoNumber`과 같이 데이터에 접근하기 위한 주소(reference)를 저장하는 data type<br>
객체 or 배열에 사용된다.<br>
```
TwoNumber 
```

## String
String은 예외적으로 값을 직접 넣어 저장하는 것 같지만, 클래스이기 때문에 reference type이다.<br>

