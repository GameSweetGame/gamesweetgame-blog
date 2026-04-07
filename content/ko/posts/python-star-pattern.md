+++
date = '2021-11-28T00:00:00+09:00'
title = '파이썬 반복문으로 별찍기'
tags = ['Python', '반복문', '입문']
categories = ['Python']
description = '파이썬 while 반복문으로 입력받은 수만큼 별 찍기'
+++

그냥 별찍기 말고, 몇 개를 찍을지 입력을 받아서 별찍기를 해보자.

```
☆
☆☆
☆☆☆
☆☆☆☆
☆☆☆☆☆
```

```python
i = int(input("반복하고자 하는 숫자를 입력해주세요:"))
star = 1
while True:
    print("☆" * star)
    if star == i:
        break
    star += 1
```

- 입력을 받으면 기본 타입이 문자열이다. `int`로 형변환 해준다.
- `while True`로 무한반복을 만들어준다.
- 한 번씩 돌 때마다 별을 1씩 증가시키면서 찍는데, 별과 입력한 숫자가 같으면 `break`로 중단한다.

![실행 결과](https://blog.kakaocdn.net/dna/vC5KM/btrmhY8U3X2/AAAAAAAAAAAAAAAAAAAAAHK7pWNtXdPHsXSNLKDXjIKAdSEFQdSiGIOM2yyRBTT7/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=xIFFzThB5lZ9Cc%2BTbBTqlOEdZCk%3D)

7을 입력해보니 별이 1개부터 7개까지 찍히고 실행이 끝났다.
