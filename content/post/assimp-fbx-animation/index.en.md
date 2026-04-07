---
title: "Assimp FBX Model Loading & Skinning Animation"
date: "2024-01-02T00:00:00+09:00"
description: "Assimp version issues, bone stretching bugs, and Blender export settings when implementing FBX skinning animation"
categories: ["DirectX"]
tags: ["DirectX11", "Assimp", "FBX", "Skinning", "Animation"]
---

> Current status: Implementing in a simple project structure first, then porting to the team engine.

## Version Issues

The bone count was way too high, so I tested by switching Assimp versions:

**Latest version (v143)**

![Latest version - 67 bones](/images/posts/assimp-fbx-animation/1.png)

**v140**

![v140 - 2 bones](/images/posts/assimp-fbx-animation/2.png)

This is from checking a single mesh. The latest version reports 67 bones, while the older version correctly shows 2.

## Skinning Animation — Head and Arms Stretching Bug

Skinning animation works, but the head and arms stretch out way too long.

![Head/arms stretching](/images/posts/assimp-fbx-animation/3.png)

~~After debugging for a while, I found that the bones in the FBX file were sticking out above the head.~~

I experimented in Blender and confirmed that when vertex positions are slightly above the bones on the Y axis, the arms and hands stretch. Since my animation causes stretching, the bones must be slightly offset downward.

![Checking bone positions in Blender](/images/posts/assimp-fbx-animation/4.png)

## Model Lying Down After Blender Export

Check the **Y Up** option in the export settings.

![Blender export settings](/images/posts/assimp-fbx-animation/5.png)

If the model is still lying down, try changing Y Up to something else, export, then switch back to Y Up and export again. That fixed it.
