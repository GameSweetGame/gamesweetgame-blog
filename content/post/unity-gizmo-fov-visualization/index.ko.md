---
date: "2025-03-13T00:00:00+09:00"
title: "유니티 캐릭터 시야 시각화 (기즈모)"
tags: ['Unity', '기즈모', '디버깅']
categories: ['Unity']
description: "Unity OnDrawGizmos로 캐릭터 시야 범위, 공격 범위 시각화하기"
---

유니티에서 자동으로 호출되는 함수 중 기즈모 관련 함수가 있다.

### OnDrawGizmos()
씬 뷰에서 **항상** 보이게

### OnDrawGizmosSelected()
씬 뷰에서 해당 오브젝트를 **선택하면** 보이게

시야 범위나 공격 범위 등 시각화에 사용하면 디버깅하기 좋다.

![파랑색 라인이 그려졌다](/images/posts/unity-gizmo-fov-visualization/1.png)
