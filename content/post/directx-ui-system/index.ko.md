---
title: "DirectX UI 시스템 구현"
date: "2024-01-01T00:00:00+09:00"
description: "DirectX11에서 셰이더 기반 UI 시스템 구현 — Static, OnMouse, Gauge 타입"
categories: ["DirectX"]
tags: ["DirectX11", "UI", "Shader", "HLSL"]
---

엔티티를 만들 때 UITestScript를 컴포넌트로 추가한다. 생성할 때 종류를 넣어준다.

Update 함수 안에 종류 별로 구현.

## UI 종류

- **STATIC** — 그냥 가만히 있는 UI
- **ONMOUSE** — 마우스를 올리면 숨쉬고 있는 UI
- **GAUGE** — 게임에서 시간이나 배고픔, 미니게임 등 사용가능한 게이지 UI
- 만약 애니메이션이 추가 되면 더 늘려야 함

## Shader Code

```hlsl
float4 main(PixelIn input) : SV_TARGET
{
    float4 texColor = float4(1, 1, 1, 0);

    if(UItype == 1)
    {
        // 텍스처 좌표가 0과 1을 벗어나면 frac 함수를 사용하여
        // 해당 범위 내로 되돌려주어 반복
        input.tex.x = frac(input.tex.x);
        input.tex.y = frac(input.tex.y);
        texColor = shaderTexture.Sample(SampleType, input.tex);
        if (texColor.a < 0.01)
            discard;
    }
    else if(UItype == 2)
    {
        float2 textureOffset = float2(0.0f, 0.0f);
        float2 textureSize = float2(1.0f, 1 - textureTranslation);

        // 텍스처 좌표가 특정 영역을 벗어나면 투명하게 처리
        if (input.tex.x < textureOffset.x ||
            input.tex.x > textureOffset.x + textureSize.x ||
            1 - input.tex.y < textureOffset.y ||
            1 - input.tex.y > textureOffset.y + textureSize.y)
        {
            discard;
        }
        else
        {
            texColor = shaderTexture.Sample(SampleType, input.tex);
        }
    }
    else
    {
        texColor = shaderTexture.Sample(SampleType, input.tex);
        if (texColor.a < 0.01)
            discard;
    }
    return texColor;
}
```

### 핵심 포인트

- **UItype == 1 (ONMOUSE):** `frac()`으로 텍스처 좌표를 0~1 범위로 반복시켜 숨쉬는 느낌 구현
- **UItype == 2 (GAUGE):** `textureTranslation`으로 텍스처 표시 영역을 조절해서 게이지 채워지는 효과
- **else (STATIC):** 단순 텍스처 샘플링, 알파 0.01 미만이면 discard
