---
title: "Rendering a 3D Character — Transform Pipeline Order"
date: "2024-01-04T00:00:00+09:00"
description: "Matrix transformation order for rendering 3D characters in DirectX"
categories: ["DirectX"]
tags: ["DirectX11", "Rendering", "Matrix Transform", "3D"]
---

## Transform Order

**Polygon × World Matrix × View Matrix × Projection Matrix**

1. **World Matrix** — Place the model in world space (position, rotation, scale)
2. **View Matrix** — Transform relative to the camera
3. **Projection Matrix** — Project 3D onto 2D screen
