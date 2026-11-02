# 😀 Positive numbers

## 📝 Problem Statement
A student ID number is considered "positive" if its digits are in strictly increasing order (each subsequent digit is strictly greater than the previous one). Write a program to count the number of such valid ID numbers based on the given parameters.

### Input Data:
The input consists of three values, each on a new line:
1. S(S <= 36) — the base of the numeral system.
2. A(a character from 0..9, A..Z) — the first digit of the ID number in base S
3. N(N <= 10) — the length of the ID number.

### Output Data:
Print a single integer — the total number of "positive" ID numbers of length N that start with the digit A in base S

### Solving the problem
```python
import sys
d = sys.stdin.read().split()
s, a, n = int(d[0]), d[1].upper(), int(d[2])
ax = int(a, s)
m = {}
def number(s, a, n):
    if n == 0:
        return 1
    if (s - 1) - a < n:
        return 0
    if (a, n) in m:
        return m[(a, n)]
    else:
        m[(a, n)] = sum(number(s, i, n-1) for i in range(a + 1, s))
        return m[(a, n)]
print(number(s, ax, n-1))
```
