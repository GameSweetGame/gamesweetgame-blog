+++
date = '2025-02-21T00:00:00+09:00'
title = '유니티 검기 이펙트 (Unity Sword Trail Effect)'
tags = ['Unity', '이펙트', '쉐이더', '검기']
categories = ['Unity']
description = 'Unity에서 검의 궤적 메시와 쉐이더 텍스쳐로 검기 이펙트 만들기'
+++

캐릭터 컨트롤러를 만들면서 기본적인 공격 애니메이션을 넣었다.

![그냥 공격](https://blog.kakaocdn.net/dna/A6Zb0/btsMrtAMszF/AAAAAAAAAAAAAAAAAAAAAMruZrqDPWlMJ-mDmIy-ueKEQvvNUirIWJmFulX8BGpR/img.gif?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=mIW43q0jPuofh%2FFZ5mq%2FPHVcF7M%3D)

검을 휘두르는데 뭔가 허전하다. 생각해 보니 내가 했던 게임들은 검을 빠르게 휘두르면 잔영처럼 남는 이펙트가 있었다.

## 구현 방법

검의 궤적을 메시로 만든다.

![검의 궤적을 메시로](https://blog.kakaocdn.net/dna/8bn2x/btsMqA8ukv1/AAAAAAAAAAAAAAAAAAAAAGtaadReZgShxRodGqfPT6YB5uUKmA6-exa_R6IILODK/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=20Qdqj0gxdlhdpPEqkixn4ncIFw%3D)

메시에 텍스쳐를 그리고, 쉐이더로 텍스쳐를 밀면 되는데 검이 지나가는 바로 뒤를 따라가야 하기 때문에 타이밍을 맞춰주면 된다.

타이밍 맞추는 것은 애니메이션에서 검을 보면서 쉐이더 텍스쳐의 Offset을 조절한다.

애니메이션에서 쉐이더의 텍스쳐가 무엇으로 저장이 되는지 한참 찾다가 `Material._MainTex_ST`라는 것을 찾았다.

이제 애니메이션으로 쉐이더 값을 조절할 수 있다.

![검을 따라 그려지는 검기 텍스쳐](https://blog.kakaocdn.net/dna/mxPTC/btsMsTMDBYk/AAAAAAAAAAAAAAAAAAAAAL5-77iuoBHeE5HfHEMIl9dg7qi8PaPRg04NSqNXTaoX/img.gif?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=EXD8vtIx%2F832%2F9BARrBr6KlfRGU%3D)

> **팁:** 쉐이더에서 텍스쳐 설정을 wrap이 아닌 **clamp**로 해야 텍스쳐가 계속 돌지 않고, 끝부분 마지막 픽셀로 이어져 나온다.

![잘 나온다](https://blog.kakaocdn.net/dna/pPVjT/btsMqLCU6LJ/AAAAAAAAAAAAAAAAAAAAAAk4l-JIcGkrEoi1Rd8hefEzrQN-xoqndgqG6M4hvNl0/img.gif?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=bJH9sX5lGLdW7d4WtsfQdtrY8Gk%3D)

기본적인 검기 이펙트이다. 3D로 만들거나 더 많은 옵션을 넣어서 더 화려하게 만들어 봐야겠다.

### 추가 팁

![브로큰 옵션](https://blog.kakaocdn.net/dna/kLZ8q/btsMsUe9Z6Z/AAAAAAAAAAAAAAAAAAAAAJ_clEqvFw90usufkFjmIqkQlSxj3zZhtTyfvAIHo13p/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=Do2ln9XTIHv72qsJ6CO0msgUFxQ%3D)

애니메이션 키를 찍을 때 **Broken 옵션**을 넣어주면 공격 애니메이션이 끝나고 텍스쳐가 처음으로 돌아갈 때 휙 보이는 현상을 없앨 수 있다.
