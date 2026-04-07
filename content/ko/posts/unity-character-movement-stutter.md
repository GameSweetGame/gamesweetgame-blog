+++
date = '2026-02-20T12:31:00+09:00'
title = '캐릭터 이동이 버벅거리고 이상할 때'
tags = ['Unity', '캐릭터 컨트롤러', '트러블슈팅']
categories = ['Unity']
description = 'Unity 캐릭터 컨트롤러 Min Move Distance 설정으로 이동 버벅거림 해결'
+++

캐릭터 컨트롤러에서 **Min Move Distance**가 0인지 확인해봐야 한다.

![Min Move Distance 설정](https://blog.kakaocdn.net/dna/bvQ4F5/dJMcaivvW1D/AAAAAAAAAAAAAAAAAAAAAK_0mcieFCzG7mUQw6R8R-yAIy9conqYRwGKRj9ptJO7/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=hV2RwgTAjakDkk5JnXj0KOGZGVI%3D)

값이 왜 변경되었었는지.. 한참을 이동관련 코드 수정하면서 찾다가 Min Move Distance를 0으로 하니 잘 움직인다.
