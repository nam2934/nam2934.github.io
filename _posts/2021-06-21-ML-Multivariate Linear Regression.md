---
title:  "[4] Multivariate Linear Regression"
excerpt: ""

categories:
  - ML
tags:
  - [coursera, ML]

breadcrumb: true
toc: true
toc_sticky: true
 
date: 2021-06-21
last_modified_at: 2021-06-21
---
## Multivariate Linear 

### Multiple Features
이 전까지는 단일 변수에 대한 선형회귀만 다뤘다.<br><br>
<img width="40%" alt="1" src="https://user-images.githubusercontent.com/41818011/122918885-913c3b00-d39a-11eb-9935-bba75b520a8b.png">{: .align-center}<br>


그러나 이제는 다변수에 대한 선형회귀를 다룰것이다.<br><br>
<img width="80%" alt="2" src="https://user-images.githubusercontent.com/41818011/122918986-afa23680-d39a-11eb-8ce9-049aa5512651.png">{: .align-center}<br>

예를들어, 집의 가격은 집의 크기로만 정해지지 않는다.<br>
계단과 방의 갯수나 집의 연식에 따라서 가격이 변하기 마련이다. 이러한 경우에 다변수 선형회귀를 쓴다.<br>

* #### New notation
다변수에서 각각의 변수를 feature 라고 한다.<br>
n = `features의 갯수`<br>
\\( x^{(i)} \\) =`i번째 training example의 input(features vector)`<br>
\\( x^{(i)}_{j} \\) = `i번째 training example의 j번째 feature의 값`<br><br>
바로 위의 그림을 예시로 들어보자.<br>
feature의 갯수가 4개이기 때문에 n = 4이다.<br>
\\[ \begin{bmatrix}a & b \\\ c & d\end{bmatrix} \\]