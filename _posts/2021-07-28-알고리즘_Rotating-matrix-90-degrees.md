---
title:  "Rotating-matrix-90-degrees with python"
excerpt: "Method to rotate python matrix by 90-degrees without libraries"

categories:
  - PS
tags:
  - Algorithm

comments: true
last_modified_at: 2021-07-28T00:00:00-23:59
---

Introduce method to rotate python matrix by 90-degrees without libraries.

This post is part of [Python-Team-Notes for coding test]() posting that I posted.

If you have any questions or mistakes regarding the code, **please point it out!**



```python
def rotate_matrix_90_degrees(a):
    # length of row
    n = len(a)
    # length of column
    m = len(a[0])
		
    # array for storing result
    result = [[0] * n for _ in range(m)]
		
    # rotating element with rule
    # if you couldn't under standing, drawing it on paper!
    for i in range(n):
        for j in range(m):
            result[j][n-i-1] = a[i][j]
		
    return result
```
