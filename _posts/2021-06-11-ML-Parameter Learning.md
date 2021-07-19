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
last_modified_at: 2021-06-20
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
\\(\alpha\\)는 learning rate라고 한다.<br>

* #### \\( \alpha \\)가 의미하는 것
\\( \alpha \\)가 작으면 스텝이 작아지고 \\( \alpha \\)가 크면 스텝이 커진다. <br>

* #### 경사하강법의 시작 위치
그래프에서 경사하강법이 시작하는 위치에 따라 다른 지점에서 끝날 수 있다.<br>
위 그림은 서로 다른 시작 지점을 보여준다.<br>

* #### 경사하강법 식
경사하강법 식은 다음과 같다.<br>
\\[ \theta_j := \theta_j - \alpha \frac{\partial}{\partial\theta_j}J(\theta_0, \theta_1) \\]<br>
이를 gradient decent의 `update rule`이라고 한다. 
각 \\(\theta_j\\)를 동시에 업데이트 해줘야 된다.<br>
특정 \\(\theta\\)값을 먼저 업데이트하면,  다른 \\(\theta\\)이 원래 결과와 달라지게 된다.<br>
<img width="599" alt="2" src="https://user-images.githubusercontent.com/41818011/121887690-003de200-cd52-11eb-8ec8-aa7439f36796.png"><br>

### Gradient Decent Intuition

경사하강법을 이해하기 위해서 cost function을 단순화 해보자.<br>
\\( \theta_0 \\)를 0이라고 했다. 즉, cost function이 \\(  J(\theta_1) \\) 된 것이다.  Gradient Decent 식을 다시 나타내면 다음과 같다.<br>

\\[ \theta_1 := \theta_1 - \alpha \frac{d}{d\theta_1}J(\theta_1) \\]

* #### 부호에 관계없는 \\(\theta_1\\)의 수렴
위 식에서 \\( \dfrac{d}{d\theta_1}J(\theta_1) \\) 는 cost function J의 기울기이다.<br>
이 기울기의 부호와 관계없이 \\( \theta_1 \\)은 cost function이 최솟값이 되는 값으로 수렴하게 된다.<br>
<img width="650" alt="4" src="https://user-images.githubusercontent.com/41818011/122662149-b038a280-d1cb-11eb-9355-d6416312dd5c.png"><br>

* #### \\( \alpha \\)의 크기에 따른 차이점
	* ##### \\(\alpha\\)가 너무 작을 때
	\\( \alpha \\)값이 너무 작으면 경사하강이 너무 느리다.<br>
	즉, 시간이 너무 오래 걸린다.<br>
	* ##### \\(\alpha\\)가 너무 클 때
	\\(\alpha\\)값이 너무 크면 \\(\theta_1\\)이 수렴하지 않을 수 있다.<br>
	즉, \\(\theta_1\\)에 수렴하지 못하고 발산하다.<br>
<img width="575" alt="3" src="https://user-images.githubusercontent.com/41818011/122662138-9b5c0f00-d1cb-11eb-94b1-cb7fcb6c8871.png"><br>


* #### \\(\theta_1\\)의 수렴조건 
미분계수가 0이면, 더 이상 \\( \theta_1 \\)의 값이 바뀌지 않으므로, 수렴한다고 할 수 있다.
<img width="678" alt="5" src="https://user-images.githubusercontent.com/41818011/122662156-c34b7280-d1cb-11eb-93c1-09e94500323d.png">

### Gradient Descent For Liner Regression
gradient decent식의 미분계수를 계산해보자.

* #### \\(J(\theta_0, \theta_1)\\)의 미분계수 계산
\\[ \dfrac{\partial}{\partial\theta_j}J(\theta_0, \theta_1)\\]
\\[ = \dfrac{\partial}{\partial\theta_j}\dfrac{1}{2m}\displaystyle\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})^2 \\]
\\[ = \dfrac{\partial}{\partial\theta_j}\dfrac{1}{2m}\displaystyle\sum_{i=1}^{m}(\theta_0+\theta_1x^{(i)}-y^{(i)})^2 \\]
이 때, 두가지 경우가 있다.<br>
\\[ j = 0 : \dfrac{\partial}{\partial\theta_0}J(\theta_0, \theta_1) = \dfrac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)}) \\]
\\[ j = 1 : \dfrac{\partial}{\partial\theta_1}J(\theta_0, \theta_1) = \dfrac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})x^{(i)} \\]

* #### 다시 표현한 gradient decent 식
미분계수 계산을 한 gradient decent 식은 다음과 같다.<br>
\\[ \theta_0 := \theta_0 - \alpha\dfrac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)}) \\]
\\[ \theta_1 := \theta_1 - \alpha\dfrac{1}{m}\sum_{i=1}^{m}(h_{\theta}(x^{(i)})-y^{(i)})\cdot x^{(i)} \\]

* #### cost function의  local minimum
일반적인 gradient decent에서는 하강 시작점에 따라서 local minimum이 달라진다고 했다. 지금 찾은 local minimum이 global minimum이라는 사실을 보장하지 못한다.<br>
그러나 cost function은 항상 볼록 함수이기 때문에, `local minimum`과 `global minimum`이 일치한다.

이렇게 cost function에서 반복적으로 기울기 하강을 해서 결과를 얻지만, 나중에 자료의 범위나 크기가 거대해서 기울기 하강 알고리즘을 사용 할 수 없을 때에는 `반복최소이승법`이라는 알고리즘을 사용한다.

> gradient decent의 개념 및 cost function에서 gradient decent 어떻게 이루어지는지 확인함.<br>