---
title:  "[2] Model and Cost Function"
excerpt: ""

categories:
  - ML
tags:
  - [coursera, ML]

breadcrumb: true
toc: true
toc_sticky: true
 
date: 2021-06-07
last_modified_at: 2021-06-09
---

## Model and Cost Function

### 1. Training Set 이란?
<br>
지도학습(Supervised Learning)은 각각의 예시에 `올바른 답` 이 주어진다.<br>

지도학습에서 우리가 알고 있는 올바른 답(data set)을  `학습셋(Training Set)`이라고 한다.<br>
<br>
<hr>

### 2. Training Set의 표기법 정의

<br>
Training Set은 아래 그림과 같다. <br><br>

<img width="556" alt="3" src="https://user-images.githubusercontent.com/41818011/121008283-cc047780-c7cd-11eb-8cc2-73cca1c5d23f.png">

<br>

여기서 각각의 용어가 뜻하는 의미는 다음과 같다.<br>

**m = 학습예제의 수**<br>
**x = 입력변수(feature)**<br>
**y = 출력값 or 예측하려는 목표변수(target variable)**<br>
**(x,y) = 하나의 학습예제(training example)**<br>
**\\( x^{(i)}, y^{(i)} \\) = i번째 학습예제**<br>

<br>
<hr>

### 3. 지도학습 알고리즘

* #### Training set을 이용한 지도학습의 동작과정

<img width="568" alt="4" src="https://user-images.githubusercontent.com/41818011/121008352-dde61a80-c7cd-11eb-83d1-368479f115e2.png">

먼저, 우리가 세울 함수 h(가설)를 정의해야한다.<br>
이 함수 h는 입력변수인 x가 h에 의해서 결과값인 y로 대응된다.<br>

즉,  `h = function maps from x’s to y’s` 라고 볼 수 있다.<br>

h라는 용어는 가설이라는 의미이지만, ML에서는 가설이라는 뜻과는 좀 거리가 있으니 참고하면 된다.<br>

<br>

* #### 지도 알고리즘의 디자인

  * ##### 가설함수 h 표현방법 <br>
**\\[ h_\Theta(x) = \Theta_0 + \Theta_1x\\]**

  * ##### 가설함수 h의 의미 <br>
= x의 `선형함수`인 y를 예측하는 것이다. <br>

  * ##### 가설함수에 선형함수를 사용하는 이유<br>
가끔 복잡한 비선형함수를 사용하기도 하지만, 선형함수가 가장 기본적이기 때문이다.<br>
나중에는 비선형 함수를 다룰 예정이다.<br>

  * ##### 단변수 선형회귀 모형<br>
<img width="359" alt="5" src="https://user-images.githubusercontent.com/41818011/121008393-e9394600-c7cd-11eb-9c89-c9f423136cf8.png"><br>
위 그림이 단변수 선형회귀 모형이다.

<hr>

### Cost Function(비용함수)

`Cost Function` : 주어진 데이터에 가장 가까운 일차함수 그래프를 알아내는 방법

* #### Cost Function의 쓰임새
비용함수는 가설 함수의 정확도를 측정하는데 쓰인다. <br>
가설 함수의 정확도란 실제 y값과, x값을 입력받은 가설함수를 통해 나온 y값의 차이를 뜻한다.<br>

* #### Cost Function의 정의
\\[ J(\theta_{0}, \theta_{1}) = \frac{1}{2m} \sum_{i=1}^{m}(\hat y_i - y_i)^{2} = \frac{1}{2m}  \sum_{i=1}^{m}(h_{\theta}(x_i) - y_i)^{2} ) =  \frac{1}{2} \bar{x} \\]
\\( \bar{x} \\) 는 \\( h_{\theta}(x_i) - y_i \\) 의 제곱의 평균. 즉,  실제값과 예측값의 차이의 제곱의 평균이다.<br>
이 함수는 “Squared error funtion” or “Mean squared error” or 평균 제곱 오차함수 라고 부른다.<br>

* #### Cost Function에서 2로 나누는 이유
gradient descent(경사하강법)의 계산의 편의를 위해 Squared error function을 2로 나눈 값을 Cost Function으로 정의한다.

* #### 그래프로 보는 Cost Function 

  2. #####  \\(\theta_0 = 0\\)
원래 Cost Function인 \\( J(\theta_0, \theta_1) \\) 에서 \\(\theta_0\\) 를 0이라고 가정해보자.<br><br>
그러면 Cost Function은 \\( J(\theta_1)\\) 즉, \\(\theta_1\\)만을 변수로 가지는 함수가 된다.<br>
다음 그래프는, Training Set이 (1,1), (2,2), (3,3) 이라고 가정했을 때의 Cost Function이다.<br><br>
<img width="352" alt="6" src="https://user-images.githubusercontent.com/41818011/121207838-8ec6e500-c8b4-11eb-80f9-5cc24b9c1d54.png"><br><br>
예를들어, \\(\theta_1=1\\) 일때의 비용함수를 구해보자.<br><br>
가설함수 : \\(h_(\theta_1) = x\\)<br>
비용함수 : 0<br><br>
y = x 이기때문에 x=1,2,3일때, y=1,2,3이 되고, 이는 실제 훈련셋의 y값과 동일하다.<br>
그러므로 실제값과 예측값의 차이가 0이라서 비용함수는 0이 된다.<br><br>
마찬가지로 모든 \\(\theta_1\\) 에 대해서 구해보게 되면 위 그림과 같은 2차함수 형태가 나오게 된다.<br>
그리고 이 그래프에서 알 수 있는 점은  \\(\theta_1 = 1\\)일때 비용함수가 최소가 되고, 이 때 가설함수와 실제 값이 일치함을 볼 수 있다.<br>

  2. ##### \\(\theta_0 \neq 0\\) 
\\(\theta_0 \neq 0\\) 이면 비용함수를 이차원 평면상에 나타낼 수 없다.<br>
비용함수를 3차원 그래프 으로 나타내면 밑의 그림과 같다.<br><br>
<img width="531" alt="7" src="https://user-images.githubusercontent.com/41818011/121208408-ff6e0180-c8b4-11eb-93c8-eca18bad8ddc.png"><br><br>
아래 그림은 3차원 그래프를  \\(\theta_0\theta_1\\) 평면에 통과시켰다고 생각하면 된다.<br><br>
<img width="702" alt="8" src="https://user-images.githubusercontent.com/41818011/121208468-0b59c380-c8b5-11eb-923d-f4c134881e89.png"><br><br>
즉, 같은 \\(J(\theta_0,\theta_1)\\) 값을 가지는 값끼리 선을 그어놓은 것이다.<br>
이를 등고선 그래프라고 한다.<br><br>
비용함수 등고선 그래프에서 특정  \\(\theta_0, \theta_1\\)을 정하고 가설함수를 그려보면 실제 Training Set과 어느정도 피팅되는지 확인할 수 있다.<br>
가장 안쪽에 있는 원의   \\(\theta_0,\theta_1\\)값일수록 실제 값들과 가설함수가 잘 피팅됨을 확인할 수 있다.<br><br>
<img width="690" alt="9" src="https://user-images.githubusercontent.com/41818011/121208547-1a407600-c8b5-11eb-98e1-0185bc6a2524.png"><br>

<hr>

### 4. 결론

> Training Set, Hypothesis Function, Cost Function의 정의를 배움
<br>

> Cost Function이 최소면 h-function의 정확도가 올라감
<br>

다음 포스팅에는 Cost Function의 최솟값을 구하는 알고리즘에 대해서 알아볼 예정이다.<br>
<hr>