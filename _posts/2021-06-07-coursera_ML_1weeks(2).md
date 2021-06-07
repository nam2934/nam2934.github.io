---
title:  "[2] Coursrea ML 1주차 강의노트"
excerpt: ""

categories:
  - ML
tags:
  - [coursera, ML]

breadcrumb: true
toc: true
toc_sticky: true
 
date: 2021-06-07
last_modified_at: 2021-06-07
---

# Linear Regression with One Variable

## Model Representation

먼저, Oregon과 Protland 도시의 주택 가격 데이터를 이용해서 집세에 대한 예측을 해보자.

### Training Set 이란?

주택 가격과 주택 크기 데이터 자료는 다음과 같다.
<img width="752" alt="1" src="https://user-images.githubusercontent.com/41818011/121008164-a7100480-c7cd-11eb-91ea-ac935fb77bb7.png">

친구가 1250 \\( feet^2 \\) 의 크기를 가진 주택의 가격을 알고싶다고 할 때, 우리가 할 수 있는 일은 선을 그어보는 것이다.<br>
그러면 대략 22만 달러에 팔 수 있다고 말할 수 있을 것이다.
<img width="731" alt="2" src="https://user-images.githubusercontent.com/41818011/121008216-b8f1a780-c7cd-11eb-98ec-437cd362f38c.png">

이것이 지도 학습(Supervised Learning) 알고리즘의 예시이다.<br>
이것이 지도학습이라고 불리는 이유는 각각의 예시에 `올바른 답` 을 주기 때문이다.

또한 이것은 가격을 예측하는 회귀라는 의미의 회귀 문제(Regression Problem)의 예시이다.(연속된 데이터에서 사용)<br>

그리고 다른 지도학습의 형태는 분류문제(Classification)로 불린다.<br>
예를들면 암종양을 찾을 때 그것이 악성인지 아닌지에 대한 결정을 내리는 것과 같은 이산값을 예측하는 문제같은 것이다. <br>
즉, 이것은 0-1의 이산값이다. 

지도학습에서 우리가 알고 있는 올바른 답(데이터셋)을  `학습셋(Training Set)`이라고 한다.<br>

위의 주택 가격의 예제에서 우리는 서로 다른 주택 가격의 학습셋을 가지고 있다.<br>
우리가 할 일은 이 데이터로부터 어떻게 주택 가격을 예측할 지 학습시키는 것이다.<br>

### 표기법 정의
**m = 학습예제의 수**<br>
**x = 입력변수(feature)**<br>
**y = 출력값 or 예측하려는 목표변수(target variable)**<br>
**(x,y) = 하나의 학습예제(training example)**<br>
**\\( x^{(i)}, y^{(i)} \\) = i번째 학습예제**<br>


<img width="556" alt="3" src="https://user-images.githubusercontent.com/41818011/121008283-cc047780-c7cd-11eb-8cc2-73cca1c5d23f.png">

### 지도학습 알고리즘
위의 Training set을 통해 지도학습이 어떻게 돌아가는지 배울 것이다.<br>
위의 주택 예시에서 Training set들을 보았고, 이 set에 지도 알고리즘을 사용 할 것이다. <br>
이 지도 알고리즘은 결과 값으로 나타나지는데 이것을 소문자 h라고 할 것이다(hypothesis).<br>

친구가 팔려고 하는 새로운 집의 사이즈를 x로 받고, h를 통해서 결과 값으로 추측되는 값을 y에 받는 것이다.<br>

즉,  `h = function maps from x’s to y’s` 라고 볼 수 있다.<br>

h라는 용어는 가설이라는 의미이지만, ML에서는 가설이라는 뜻과는 좀 거리가 있으니 참고하면 된다.<br>
<img width="568" alt="4" src="https://user-images.githubusercontent.com/41818011/121008352-dde61a80-c7cd-11eb-83d1-368479f115e2.png">

지도 알고리즘을 디자인할 때, 우리가 결정해야 할 것은 가설 h를 어떻게 표현할 것인지에 대해서이다.<br>

h는 다음과 같이 표현한다.<br>
\\( h_\Theta(x) = \Theta_0 + \Theta_1x\\)

이것의 의미는 x의 선형함수인 y를 예측하는 것이다. <br>
왜 선형함수를 사용할까?<br>
가끔 복잡한 비선형함수를 사용하기도 하지만, 선형 유형은 간단한 기본 구성 요소이기때문에 이 유형부터 시작하는 것이다.<br>

우리는 결과적으로 더 복잡한 모형들, 더 복잡한 학습 알고리즘을 배울것이다.<br>
<img width="359" alt="5" src="https://user-images.githubusercontent.com/41818011/121008393-e9394600-c7cd-11eb-9c89-c9f423136cf8.png">

위 모형을 단변수 선형회귀라고 부른다.<br>