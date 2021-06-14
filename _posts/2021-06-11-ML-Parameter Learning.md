---
title:  "[3] Parameter Learning"
excerpt: ""

categories:
  - ML
tags:
  - [coursera, ML]

breadcrumb: true
toc: true
toc_sticky: true
 
date: 2021-06-11
last_modified_at: 2021-06-14
---
## Parameter Learning

### Gradient Descent(경사하강법)

Cost Function의 최솟값을 구하는데에 Gradient Descent가 쓰인다.<br>
\\( \theta_0\\)와 \\( \theta_1 \\)을 기반으로한 Cost Function은 다음과 같다.<br>

<img width="598" alt="1" src="https://user-images.githubusercontent.com/41818011/121887634-f0260280-cd51-11eb-85e4-e554ed99c9d6.png">

* #### 경사하강법이란?
기울기의 절댓값이 낮은 곳으로 이동하는 알고리즘이다.<br>
그림의 빨간 화살표가 Cost Function의 극솟값들이다. <br>

* #### 경사하강법의 방향과 크기
**접선의 기울기(미분계수)**는 최솟값으로 가는 **방향**을 제시해준다.<br>
방향 말고 **크기**를 결정하는 것은 파라미터 \\( \alpha \\)이다.<br>

* #### \\( \alpha \\)가 의미하는 것
\\( \alpha \\)가 작으면 스텝이 작아지고 \\( \alpha \\)가 크면 스텝이 커진다. <br>

* #### 경사하강법의 시작 위치
그래프에서 경사하강법이 시작하는 위치에 따라 다른 지점에서 끝날 수 있다.<br>
위 그림은 서로 다른 시작 지점을 보여준다.<br>

* #### 경사하강법 식
경사하강법 식은 다음과 같다.<br>
\\[ \theta_j := \theta_j - \alpha \frac{\partial}{\partial\theta_j}J(\theta_0, \theta_1) \\]<br>
각 \\(\theta_j\\)를 동시에 업데이트 해줘야 된다.<br>
특정 \\(\theta\\)값을 먼저 업데이트하면,  다른 \\(\theta\\)이 원래 결과와 달라지게 된다.<br>
<img width="599" alt="2" src="https://user-images.githubusercontent.com/41818011/121887690-003de200-cd52-11eb-8ec8-aa7439f36796.png"><br>

### Gradient Decent Intuition

### Gradient Descent For Liner Regression