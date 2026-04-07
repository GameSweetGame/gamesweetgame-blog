---
title: "DirectX Lighting Basics — Ambient, Diffuse, Specular"
date: "2024-01-03T00:00:00+09:00"
description: "Ambient, Diffuse, and Specular lighting calculations in DirectX shaders, plus saturate and rim light tips"
categories: ["DirectX"]
tags: ["DirectX11", "Shader", "HLSL", "Lighting"]
---

## Lighting Calculation

```hlsl
float4 fvTotalAmbient  = fvAmbient * fvBaseColor;
float4 fvTotalDiffuse  = fvDiffuse * fNDotL * fvBaseColor;
float4 fvTotalSpecular = fvSpecular * pow( fRDotV, fSpecularPower );

return( saturate( fvTotalAmbient + fvTotalDiffuse + fvTotalSpecular ) );
```

## Notes

- `saturate()` clamps the value between 0 and 1
- **Do NOT use saturate in HDR** (values above 1.0 are needed)
- Large capacity is possible due to texture compression
- **Rim lighting** technique: compute using the normal vector at the vertex stage
