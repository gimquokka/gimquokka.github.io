---
title:  "Useful parsing skill with python"
excerpt: "Introduce various useful parsing technique for real coding test"

categories:
  - PS
tags:
  - Algorithm
  - Implementation

comments: true
last_modified_at: 2021-08-02T00:00:00-23:59
---

In a real coding test, there are many difficulties in conditioning simple string processing. Python can use a variety of built-in functions and regular expressions for string data types as a basic built-in library, so with a few simple taps, you can use them very well.

## Extract only the number of digits in a string into dictionary

```python
number_cnt = Counter(re.findall('\d+', string))
```

## Change to All Alphabet Case

```python
# Change to Lowercase
string.lower()

# Change to uppercase
string.upper()
```

## Determine if a string consists only of alphabets or numbers

```python
# Determine if it is made up of only alphabets
"abcd".isalpha() # True
"ab2d".isalpha() # False

# Determine if it consists only of numbers
"123".isdigit() # True
"ab123".isdigit() # False

# Determine if it consists only of alphabets or numbers
"123abc".isalnum() # True
"123##ab".isalnum() # False
```

## regular expression examples

See the link below for full information. Only examples from real problems are summarized.

[Well-organized documents](https://wikidocs.net/4308#_2)

```python
import re
from collections import Counter

# Returns if non-alphabet characters are contained in it
string = "12 #abc# 123"
result = re.findall('[^a-zA-Z]+', string)
print(result) # ['12 #', '# 123']

# Returns the number and number that appears in the string in dict form
string = "{% raw%}{{2},{2,1},{2,1,3},{2,1,3,4}}{%endraw%}"
result = Counter(re.findall('\d+', string))
print(result) # Counter({% raw%}{'2': 4, '1': 3, '3': 2, '4': 1}{%endraw%})
```

This post is part of [Python-Team-Notes for coding test](https://gimquokka.github.io/ps/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98_Python_Team_Notes/) posting that I posted. If you have any questions or mistakes regarding the code, **please point it out!**
