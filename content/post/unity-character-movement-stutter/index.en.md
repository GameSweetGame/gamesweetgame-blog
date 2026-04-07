---
date: "2026-02-20T12:31:00+09:00"
title: "Fix Character Movement Stutter in Unity"
tags: ['Unity', 'Character Controller', 'Troubleshooting']
categories: ['Unity']
description: "Fix character movement stutter by setting Min Move Distance to 0 in Unity Character Controller"
---

Check if **Min Move Distance** is set to 0 in your Character Controller.

![Min Move Distance setting](/images/posts/unity-character-movement-stutter/1.png)

I spent a long time tweaking movement code trying to figure out why the character was stuttering. Turns out, setting Min Move Distance to 0 fixed it right away.
