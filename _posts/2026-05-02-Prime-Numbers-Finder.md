---
layout: post
title: Prime Numbers Finder with Python
image: "/posts/prime_nums.jpg"
tags: [Python, Primes]
---

Hello! For my first post, I'll be walking through a Python function I wrote that returns a list of all prime numbers that are below a specified input number. For example, if we passed in a value n=10, this function would return a list of all prime numbers below the specified number 10!

For reference, a prime number is an integer that can only be divided wholly by itself and 1. In our example of n=10, we would expect an output as follows:
```python
>>> {2, 3, 5, 7}
```

--- 

First, let's set our input value "n", the number in which we want to find all prime numbers under

```python
n = 20
```


The lowest prime number to exist is 2. Because of this, we want our initial list of possible prime numbers, "number_range", to be a list of numbers starting from 3 and ending at specified input "n"
```Python
number_range = set(range(2, n+1))
```