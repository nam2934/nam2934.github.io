---
title:  "[1] Machine Learning Introduction"
excerpt: ""

categories:
  - ML
tags:
  - [coursera, ML]

breadcrumb: true
toc: true
toc_sticky: true
 
date: 2021-06-06
last_modified_at: 2021-06-09
---
## Introduction of Machine Learning

### 1. Machine Learning(기계학습)이란?
<br>
ML의 정의는 시대에 따라서 변해왔다.<br>
다음은 옛날 정의이다.<br>

* #### Authur Samuel의 정의
기계학습이란, 컴퓨터가 명시적 프로그램이 없어도 스스로 학습할 수 있는 능력을 연구하는 학문 분야이다.<br>

* #### Tom Mitchell의 정의
프로그램이 일정 수준의 `작업 성능(P)`를 가지고 `작업(T)`을 수행한다고 했을 때, `경험(E)`이 증가함에 따라 `작업(T)`을 수행하는 `성능(P)`이 향상 될 수 있다.<br>
이 때, 프로그램이 `경험(E)`로부터 `학습`했다고 표현한다.<br>

Tom Mitchell의 정의가 지금의 ML 정의이다.<br>
<hr>

### 2. 기계학습 알고리즘의 종류

* #### Supervised Learning(지도학습) 
작업을 수행할 수 있는 방법을 컴퓨터에게 가르치는 것<br>

* #### Unsupervised Learning(비지도학습)
컴퓨터가 스스로 학습하도록 유도하는 것<Br>

그 외에 강화학습이나 추천시스템 같은 알고리즘도 있다. 그러나 가장 많이 사용되는 알고리즘은 지도학습과 비지도학습이다.<br>
<hr>

### 3. Supervised Learning

지도학습은 올바른 Data set이 주어지고 이를 통해 더 많은 정답을 만들어 내는 것이다.<br>

비지도학습은 Regression Problem(회귀문제)과 Classification problem(분류문제)으로 나뉜다.<br>

* #### Regression Problem
회귀문제는 `연속된` 출력안에서 결과값을 예측하는 것이다.<br>
<img width="552" alt="1" src="https://user-images.githubusercontent.com/41818011/121335387-7fe43f00-c955-11eb-8644-c5882f4de51d.png"><br>
<br>
ex) 부동산 시장에서 주택 규모에 따른 가격을 예측하는 문제.<br>
규모의 함수로서 가격은 연속적인 값을 가지기 때문에 회귀문제이다.<br>

* #### Classification problem
분류문제는 `이산적인` 출력안에서 결과값을 예측하는 것이다.<br>
<br>
ex) 부동산에서 주택 규모에 따른 가격에 대해서 요구하는 가격보다 비싸게 팔리는가를 예측하는 문제<br>
이 경우는  요구하는 가격에 기초해서 2개의 집합으로 나눌 수 있기 때문에 분류문제이다.<br>
<img width="567" alt="2" src="https://user-images.githubusercontent.com/41818011/121335433-8d012e00-c955-11eb-94fe-f931c752bb6e.png"><br>
<hr>

### 4. Unsupervised Learning

지도학습에서는 정답이 주어지지만, 비지도 학습에서는 어떤 레이블도 가지고 있지 않다.<br>
모두 같은 레이블을 갖고 있거나, 아예 레이블이 없다.<br>

<img width="493" alt="3" src="https://user-images.githubusercontent.com/41818011/121335506-9ee2d100-c955-11eb-9c4a-0c84293b366d.png"><br>

cluster과 non-clustering 알고리즘으로 나뉜다.<br>

* #### Clustering 알고리즘
서로 연관이 있는 그룹끼리 분류하는 알고리즘<br><br>
ex) 1,000,000개의 서로 다른 유전자를 모아서, 이 유전자를 수명, 위치, 역할 등이 유사한거나 관련이 있는 그룹으로 자동 분류하는 것.<br>

* #### Non-Clustering 알고리즘
혼란스러운 환경에서 구조를 찾게 해주는 알고리즘.<br>
ex) 칵테일 파티 알고리즘<br>
<hr>