+++
date = '2021-11-28T00:00:00+09:00'
title = 'Python Star Pattern with While Loop'
tags = ['Python', 'Loop', 'Beginner']
categories = ['Python']
description = 'Print a star pattern using Python while loop with user input'
+++

Instead of a simple star pattern, let's take user input to decide how many rows to print.

```
☆
☆☆
☆☆☆
☆☆☆☆
☆☆☆☆☆
```

```python
i = int(input("Enter the number of rows: "))
star = 1
while True:
    print("☆" * star)
    if star == i:
        break
    star += 1
```

- `input()` returns a string by default. Convert it to `int`.
- `while True` creates an infinite loop.
- Each iteration prints stars and increments by 1. When it matches the input, `break` stops the loop.

![Result](https://blog.kakaocdn.net/dna/vC5KM/btrmhY8U3X2/AAAAAAAAAAAAAAAAAAAAAHK7pWNtXdPHsXSNLKDXjIKAdSEFQdSiGIOM2yyRBTT7/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=xIFFzThB5lZ9Cc%2BTbBTqlOEdZCk%3D)

Entering 7 prints stars from 1 to 7 rows.
