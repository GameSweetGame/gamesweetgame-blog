---
title: "2D 물리엔진을 위한 수학 기초"
date: "2024-01-01T00:00:00+09:00"
description: "2D 물리엔진 개발에 필요한 선형대수, 미적분, 토크 등 수학 개념 정리"
categories: ["Physics"]
tags: ["수학", "물리", "2D", "미적분", "선형대수"]
---

D2D로 그림을 그린다.

선형대수, 미적분, 테일러시리즈

## 핵심 물리 용어

**임펄스 (Impulse):** 힘의 크기와 그 힘이 작용한 시간과의 곱 (힘의 크기 × 작용한 시간). 질량과 속도가 변한 정도.

**모멘텀 (Momentum):** 물질의 운동량을 뜻하는 물리학 용어. 질량에 속도를 곱해서 구하며 단위는 kg⋅m/s

**Damping:** 마찰력 같이 운동을 저항하는 힘

## Calculus (미적분)

아이작 뉴턴이 고안한 개념.

### 미분

어떤 함수가 있을 때 임의의 점에서 기울기를 구하는 것이라고 생각하면 됨.

![미분 - 접선의 기울기](/images/posts/2d-physics-math-basics/1.png)

#### Power Rule

![Power Rule](/images/posts/2d-physics-math-basics/2.png)

#### Quotient Rule

![Quotient Rule](/images/posts/2d-physics-math-basics/3.png)

#### Product Rule

![Product Rule](/images/posts/2d-physics-math-basics/4.png)

#### Chain Rule

![Chain Rule](/images/posts/2d-physics-math-basics/5.png)

#### 지수/로그 함수의 미분

![지수/로그 미분](/images/posts/2d-physics-math-basics/6.png)

### 적분

부호있는 면적을 구하는 것.

## 토크 (Torque)

벡터의 크로스 프로덕트 연산을 이용해서 구한다.

![토크](/images/posts/2d-physics-math-basics/7.png)

## 아이젠벨류 (Eigenvalue)

3차원 물리엔진 할 때 필요함. (축에 관한 것)

![아이젠벨류](/images/posts/2d-physics-math-basics/8.png)
