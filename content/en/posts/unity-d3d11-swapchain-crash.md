+++
date = '2026-01-28T00:00:00+09:00'
title = 'Unity Editor Crash Fix: D3D11 Swapchain Device Reset/Removed'
tags = ['Unity', 'D3D11', 'Troubleshooting', 'Windows Defender']
categories = ['Unity']
description = 'Fix Unity editor D3D11 swapchain crash caused by Windows Defender firewall blocking network access'
+++

I was working in Unity when suddenly the editor crashed with a D3D11 swapchain error — "Failed to present D3D11 swapchain due to device reset/removed."

After reopening, it would crash within 3 seconds every time.

![Error screenshot](https://blog.kakaocdn.net/dna/bLpuCk/dJMcajgH2Ai/AAAAAAAAAAAAAAAAAAAAAC1odZ9AlPMP1_JCB2vG9EEh90FKTGvyw4wmk0mrSAQF/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=4I9F%2FfATeEd%2Bzo%2FI%2BYckEB3AIf4%3D)

I tried everything — reinstalling Unity, changing versions — nothing worked.

I initially suspected **Wallpaper Engine** conflicting with DirectX in the background, but that wasn't it either.

The key symptom was that the editor was sluggish and unresponsive, but the scene and game view rendered fine before crashing. This suggested it wasn't a rendering issue but something loading in the background.

Then I noticed **Windows Defender**.

![Defender](https://blog.kakaocdn.net/dna/BWcNY/dJMcaiPDXME/AAAAAAAAAAAAAAAAAAAAAB1sByDYHHLTZu3k04A0UgqoWBur_P4fDCfyBkdDtx7C/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=Xt2f%2Fc6R5IvekBK4IlLrrW6Yccw%3D)

**The fix: Allow the Unity Editor and Unity Package Manager through Windows Defender Firewall.**

![Firewall settings](https://blog.kakaocdn.net/dna/dakfJU/dJMcahXzaSY/AAAAAAAAAAAAAAAAAAAAACK5r00g_D-90mlI8Bl49RMGswnwBly-wt2NfEacRh7V/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=X9RCOsdylYaERpKcbMhlBrhl5r8%3D)

My theory: Unity tries to communicate with Package Manager and other services on startup. The firewall blocks these requests, stalling the main thread, causing GPU timing to slip, and eventually triggering the D3D11 device reset.
