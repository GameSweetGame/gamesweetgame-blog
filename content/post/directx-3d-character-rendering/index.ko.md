---
title: "3D 캐릭터 띄우기 — 렌더링 파이프라인 변환 순서"
date: "2024-01-04T00:00:00+09:00"
description: "DirectX에서 3D 캐릭터를 화면에 띄우기 위한 행렬 변환 순서 정리"
categories: ["DirectX"]
tags: ["DirectX11", "렌더링", "행렬 변환", "3D"]
---

## 변환 순서

**폴리곤 × 월드행렬 × 뷰행렬 × 프로젝션행렬(투영)**

1. **월드행렬 (World Matrix)** — 모델을 월드 공간에 배치 (위치, 회전, 스케일)
2. **뷰행렬 (View Matrix)** — 카메라 기준으로 변환
3. **프로젝션행렬 (Projection Matrix)** — 3D → 2D 화면으로 투영
