---
date: "2021-11-24T00:00:00+09:00"
title: "Python: Search Lists and Strings with the "in" Operator"
tags: ['Python', 'in', 'Beginner']
categories: ['Python']
description: "How to use Python in and not in operators to search lists and strings"
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

![Output](/images/posts/python-in-operator/1.png)

- `result1`: Is 1 in `[1, 2, 3]`? → Yes → `True`
- `result2`: Is 5 in `[1, 2, 3]`? → No → `False`
- `not in` is simply the opposite
- Strings work just like lists
- `result5`: Is "j" in "python"? → No → `False`
