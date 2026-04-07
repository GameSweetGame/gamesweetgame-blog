---
title: "Assimp FBX 모델 로드 & 애니메이션"
date: "2024-01-02T00:00:00+09:00"
description: "Assimp으로 FBX 스키닝 애니메이션 구현 시 버전 이슈, 본 늘어남 버그, 블렌더 Export 설정 정리"
categories: ["DirectX"]
tags: ["DirectX11", "Assimp", "FBX", "스키닝", "애니메이션"]
---

> 현재 상황: 과제 하던 간단한 구조에서 먼저 구현 중 → 구현 완료하면 팀 엔진으로 이식

## 버전 이슈

아무리 생각해도 본 개수 값이 너무 많이 나와서 Assimp 버전만 바꿔서 확인한 결과:

**최신 버전 (v143)**

![최신 버전 - 본 67개](/images/posts/assimp-fbx-animation/1.png)

**v140 버전**

![v140 - 본 2개](/images/posts/assimp-fbx-animation/2.png)

메쉬 하나를 확인한 것인데 최신 버전은 본이 67개가 있다고 나옴. 이전 버전을 사용하니까 2개로 나옴.

## 스키닝 애니메이션 — 머리와 팔이 길어지는 버그

스키닝 애니메이션이 되긴 하는데 머리와 팔이 엄청 길어짐.

![머리/팔 길어짐](/images/posts/assimp-fbx-animation/3.png)

~~한참을 디버깅 하다가 fbx 파일을 확인 결과 본이 머리위로 튀어 나와있었다.~~

블렌더에서 실험을 해봤는데 버텍스들의 위치가 본보다 Y로 조금씩 올라가면 팔과 손이 길어지는 것을 확인함. 반대로 나는 애니메이션을 적용하면 길어지니까 본이 조금씩 아래로 설정 되어 있을 것 같다.

![블렌더에서 본 위치 확인](/images/posts/assimp-fbx-animation/4.png)

## 블렌더 Export 시 모델이 누워있을 때

익스포트 설정에서 **Y Up**을 확인.

![블렌더 Export 설정](/images/posts/assimp-fbx-animation/5.png)

그래도 똑같이 나오면 Y Up을 다르게 바꿔서 뽑았다가 다시 Y Up으로 변경해서 하니까 정상 출력됨.
