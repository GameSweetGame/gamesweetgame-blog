---
title: "DirectX 라이팅 기초 — Ambient, Diffuse, Specular"
date: "2024-01-03T00:00:00+09:00"
description: "DirectX 셰이더에서 Ambient, Diffuse, Specular 라이팅 계산과 saturate, 림라이트 팁"
categories: ["DirectX"]
tags: ["DirectX11", "Shader", "HLSL", "라이팅"]
---

## 라이팅 계산

```hlsl
float4 fvTotalAmbient  = fvAmbient * fvBaseColor;
float4 fvTotalDiffuse  = fvDiffuse * fNDotL * fvBaseColor;
float4 fvTotalSpecular = fvSpecular * pow( fRDotV, fSpecularPower );

return( saturate( fvTotalAmbient + fvTotalDiffuse + fvTotalSpecular ) );
```

## 메모

- `saturate()`는 0~1 사이의 값으로 클램핑
- **HDR에서는 saturate 함수를 사용하면 안 됨** (1.0 이상의 값이 필요하기 때문)
- 텍스처 압축하기 때문에 큰 용량 가능
- **림라이트**는 버텍스에서 노멀벡터와 연산 하는게 테크닉
