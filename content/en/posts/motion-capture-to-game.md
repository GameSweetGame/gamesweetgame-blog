+++
date = '2026-01-20T11:00:00+09:00'
title = 'Applying Custom Motion Capture Animations to Your Game'
tags = ['Unity', 'Python', 'Motion Capture', 'Animation']
categories = ['Animation']
description = 'How to use Python-based motion capture to extract poses and apply them to Unity characters'
+++

I want to make a polished action game. Let's custom-make the attack animations.

I referenced this motion capture project on GitHub:

[GitHub - 3D Motion Capture From Video](https://github.com/SAKTHIVINASH2/3D-Motion-Capture-From-Video)

Using a Python pose estimation library, you can extract keypoint coordinates for head, shoulders, arms, legs, etc. These coordinates are then converted for use in Unity.

## Overall Flow

- External pose data (33 keypoints)
- Convert to Unity coordinate system
- Point objects (P0~P32)
- Estimate rotation relative to bind direction
- Root direction (yaw + slight tilt) estimation with smoothing

## Normalizing File Values + Axis Correction

```csharp
float px = float.Parse(toks[i * 3 + 0]) / scaleXY;
float py = float.Parse(toks[i * 3 + 1]) / scaleXY;
float pz = float.Parse(toks[i * 3 + 2]) / scaleZ;
```

- Different XY/Z scales: Video-based pose estimation has much more noise in depth (Z)
- invertZ: Corrects coordinate system difference between MediaPipe and Unity

## Storing Bind Rotation

```csharp
lUpperBind = lUpperArm.rotation;
```

Reference rotation from the T-Pose.

## Automatic Bind Direction Estimation

```csharp
lUpperBindDir = (lLowerArm.position - lUpperArm.position).normalized;
```

The core concept: **which direction was this bone originally facing?**

UpperArm → LowerArm direction = **bone's reference forward vector**

![Motion capture result](https://blog.kakaocdn.net/dna/r5Ipj/dJMcafejncp/AAAAAAAAAAAAAAAAAAAAAI4h9Lsaov86gsi_snD2bdruWq35a5pYQqaIPwR5WBD_/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=x0wWvUl2pIgwvNBPSmXc0c4nJAE%3D)

A bit rough, but the motion came through. Now it's time to refine it in Blender.
