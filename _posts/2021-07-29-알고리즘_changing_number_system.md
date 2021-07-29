---
title:  "Changing base-notation(number-system) with python"
excerpt: "Introduce the way that changing base-notation(number-system)"

categories:
  - PS
tags:
  - Algorithm
  - Implementation

comments: true
last_modified_at: 2021-07-29T00:00:00-23:59
---

It's simple to think a little bit about how to change number system, but it's easy to get a head down when you encounter it in a real coding interview. That's why we need to prepare this thoroughly. Let's start with the code below!

This post is part of [Python-Team-Notes for coding test]() posting that I posted. If you have any questions or mistakes regarding the code, **please point it out!**

```python
# changing base-notation(number-system)

# 1. If base go beyond decimal (0 ~ infinity)
def numeral_system(number, base):
    # If base = 16? => NOTATION = '0123456789ABCDEF'
    NOTATION = '012' # Incase of base = 3. 
    q, r = divmod(number, base)
    n = NOTATION[r]
    return numeral_system(q, base)+n if q else n

  
# 2. If inside decimal(10)
while n:
    tmp += str(n % 3) + tmp
    n = n // base

    
# 3. When you change base to decimal
int(tmp, 3)
```
