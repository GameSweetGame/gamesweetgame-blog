---
date: "2021-11-24T00:00:00+09:00"
title: "[파이썬] in을 이용해서 리스트, 문자열 검색하기"
tags: ['Python', 'in', '입문']
categories: ['Python']
description: "파이썬 in 연산자로 리스트와 문자열에서 값 검색하기"
---

```python
result1 = 1 in [1, 2, 3]
result2 = 5 in [1, 2, 3]

result3 = 1 not in [1, 2, 3]
result4 = 5 not in [1, 2, 3]

result5 = "j" in "python"
result6 = "y" in "python"
result7 = "y" not in "python"

print(result1)  # True
print(result2)  # False
print(result3)  # False
print(result4)  # True
print(result5)  # False
print(result6)  # True
print(result7)  # False
```

![출력 결과](/images/posts/python-in-operator/1.png)

- `result1`: 리스트 `[1, 2, 3]` 안에 1이 있니? → 있음 → `True`
- `result2`: 리스트 `[1, 2, 3]` 안에 5가 있니? → 없음 → `False`
- `not in`은 반대로 하는 것
- 문자열도 리스트처럼 확인이 가능하다
- `result5`: "python" 안에 "j"가 있니? → 없음 → `False`
