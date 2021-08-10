---
title:  "Binary Search with python"
excerpt: "Introduce binary search algorithm with simple python code"

categories:
  - PS
tags:
  - Algorithm
  - DFS

comments: true
last_modified_at: 2021-08-10T00:00:00-23:59
---



Will be added!



## Binary Search algorithm

```python
def binary_search(array, target, start, end):
    while start <= end:
        mid = (start+end)//2
        if array[mid] == target:
            return mid
        elif array[mid] >= target:
            end = mid - 1
        else:
            start = mid + 1
    return None
```

This post is part of [Python-Team-Notes for coding test](https://gimquokka.github.io/ps/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98_Python_Team_Notes/) posting that I posted. If you have any questions or mistakes regarding the code, **please point it out!**

