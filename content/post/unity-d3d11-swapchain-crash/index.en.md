---
date: "2026-01-28T00:00:00+09:00"
title: "Unity Editor Crash Fix: D3D11 Swapchain Device Reset/Removed"
tags: ['Unity', 'D3D11', 'Troubleshooting', 'Windows Defender']
categories: ['Unity']
description: "Fix Unity editor D3D11 swapchain crash caused by Windows Defender firewall blocking network access"
---

I was working in Unity when suddenly the editor crashed with a D3D11 swapchain error — "Failed to present D3D11 swapchain due to device reset/removed."

After reopening, it would crash within 3 seconds every time.

![Error screenshot](/images/posts/unity-d3d11-swapchain-crash/1.png)

I tried everything — reinstalling Unity, changing versions — nothing worked.

I initially suspected **Wallpaper Engine** conflicting with DirectX in the background, but that wasn't it either.

The key symptom was that the editor was sluggish and unresponsive, but the scene and game view rendered fine before crashing. This suggested it wasn't a rendering issue but something loading in the background.

Then I noticed **Windows Defender**.

![Defender](/images/posts/unity-d3d11-swapchain-crash/2.png)

**The fix: Allow the Unity Editor and Unity Package Manager through Windows Defender Firewall.**

![Firewall settings](/images/posts/unity-d3d11-swapchain-crash/3.png)

My theory: Unity tries to communicate with Package Manager and other services on startup. The firewall blocks these requests, stalling the main thread, causing GPU timing to slip, and eventually triggering the D3D11 device reset.
