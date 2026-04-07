---
title: "DirectX UI System Implementation"
date: "2024-01-01T00:00:00+09:00"
description: "Shader-based UI system in DirectX11 — Static, OnMouse, and Gauge types"
categories: ["DirectX"]
tags: ["DirectX11", "UI", "Shader", "HLSL"]
---

When creating an entity, add UITestScript as a component. Pass the UI type during creation.

Each type is implemented inside the Update function.

## UI Types

- **STATIC** — A UI element that just sits there
- **ONMOUSE** — A UI element that "breathes" when hovered
- **GAUGE** — A gauge UI for time, hunger, mini-games, etc.
- If animation is needed, more types can be added

## Shader Code

```hlsl
float4 main(PixelIn input) : SV_TARGET
{
    float4 texColor = float4(1, 1, 1, 0);

    if(UItype == 1)
    {
        // Use frac() to wrap texture coordinates within 0-1 range
        // for seamless repetition
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

        // Discard pixels outside the visible gauge area
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

### Key Points

- **UItype == 1 (ONMOUSE):** Uses `frac()` to wrap texture coordinates for a breathing animation effect
- **UItype == 2 (GAUGE):** Controls the visible texture area via `textureTranslation` to create a fill effect
- **else (STATIC):** Simple texture sampling with alpha discard below 0.01
