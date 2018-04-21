# Ellipitical Curve Cryptography

```python
# import everything and define a test runner function
from importlib import reload
from helper import run_test

import ecc
import helper
```

### Exercise 1

Remember the % operator does the actual modulo operation. Also remember that + and - need to be in () because in the order of operations % comes before + and -.

#### 1.1. Solve these equations in \\(F_{31}\\):

```
2+15=?
17+21=?
29-4=?
15-30=?
```

#### 1.2. Make [these tests](/edit/session1/ecc.py) pass:
```
ecc.py:FieldElementTest:test_add
ecc.py:FieldElementTest:test_sub
```


```python
# Exercise 1.1

# remember that % is the modulo operator
prime = 31
# 2+15=?
# 17+21=?
# 29-4=?
# 15-30=?
```


```python
# Exercise 1.2

reload(ecc)
run_test(ecc.FieldElementTest('test_add'))
run_test(ecc.FieldElementTest('test_sub'))
```

### Exercise 2

#### 2.1. Solve these equations in \\(F_{31}\\):

\\(24\cdot19=?\\)

\\(17^3=?\\)

\\(5^5\cdot18=?\\)

#### 2.2. Write a program to calculate \\(0k, 1k, 2k, 3k, ... 30k\\) for some k in \\(F_{31}\\).  Notice anything about these sets?

#### 2.3. Write a program to calculate \\(k^{30}\\) for all k in \\(F_{31}\\). Notice anything?

#### 2.4. Make [these tests](/edit/session1/ecc.py) pass:
```
ecc.py:FieldElementTest:test_mul
ecc.py:FieldElementTest:test_pow
```


```python
# Exercise 2.1

# remember that ** is the exponentiation operator
prime = 31
# 24*19=?
# 17^3=?
# 5^5*18=?
```


```python
# Exercise 2.2

from random import randint

prime = 31
k = randint(1,prime)

# use range(prime) to iterate over all numbers from 0 to 30 inclusive
```


```python
# Exercise 2.3

prime = 31

# use range(1, prime) to iterate over all numbers from 1 to 30 inclusive
```


```python
# Exercise 2.4

reload(ecc)
run_test(ecc.FieldElementTest('test_mul'))
run_test(ecc.FieldElementTest('test_pow'))
```

### Exercise 3

#### 3.1. Solve these equations in \\(F_{31}\\):

\\(3/24 = ?\\)

\\(17^{-3} = ?\\)

\\(4^{-4}\cdot{11} = ?\\)

#### 3.2. Write a program to calculate \\(k/1, k/2, k/3, ...k/30\\) for some k in \\(F_{31}\\). Notice anything about these sets?

#### 3.3. Make [these tests](/edit/session1/ecc.py) pass:

```
ecc.py:FieldElementTest:test_div
```


```python
# Exercise 3.1

# remember pow(x, p-2, p) is the same as 1/x in F_p
prime = 31
# 3/24 = ?
# 17^(-3) = ?
# 4^(-4)*11 = ?
```


```python
# Exercise 3.2

from random import randint

prime = 31
k = randint(1, prime)

# use range(31) to iterate over all numbers from 0 to 30 inclusive
```


```python
# Exercise 3.3

reload(ecc)
run_test(ecc.FieldElementTest('test_div'))

# Hint: the __pow__ method needs a positive number for the exponent.
# You can mod by p-1
```

### Exercise 4

#### 4.1. For the curve \\(y^2 = x^3 + 5x + 7\\), which of these are on the curve?

\\((-2,4), (3,7), (18,77)\\)

#### 4.2. Make [this test](/edit/session1/ecc.py) pass
```
ecc.py:PointTest:test_on_curve
```


```python
# Exercise 4.1

# (-2,4), (3,7), (18,77)
# equation in python is: y**2 == x**3 + 5*x + 7

points = ((-2,4), (3,7), (18,77))

for x, y in points:
    # determine whether (x,y) is on the curve
```


```python
# Exercise 4.2

reload(ecc)
run_test(ecc.PointTest('test_on_curve'))
```

### Exercise 5

#### 5.1. Make [this test](/edit/session1/ecc.py) pass
```
ecc.py:PointTest:test_add0
```


```python
# Exercise 5.1

reload(ecc)
run_test(ecc.PointTest('test_add0'))
```

### Exercise 6

#### 6.1. For the curve \\(y^2 = x^3 + 5x + 7\\), what is \\((2,5) + (-1,-1)\\)?

#### 6.2. Make [this test](/edit/session1/ecc.py) pass
```
ecc.py:PointTest:test_add1
```


```python
# Exercise 6.1

x1, y1 = (2,5)
x2, y2 = (-1,-1)
# formula in python:
# s = (y2-y1)/(x2-x1)
# x3 = s**2 - x2 - x1
# y3 = s*(x1-x3)-y1
```


```python
# Exercise 6.2

reload(ecc)
run_test(ecc.PointTest('test_add1'))
```

### Exercise 7

#### 7.1. For the curve \\(y^2 = x^3 + 5x + 7\\), what is \\((-1,1) + (-1,1)\\)?

#### 7.2. Make [this test](/edit/session1/ecc.py) pass
```
ecc.py:PointTest:test_add2
```


```python
# Exercise 7.1

a, b = 5, 7
x1, y1 = -1, -1

# formula in python
# s = (3*x1**2+a)/(2*y1)
# x3 = s**2 - 2*x1
# y3 = s*(x1-x3) - y1y3 = s*(x1-x3) - y1
```


```python
# Exercise 7.2

reload(ecc)
run_test(ecc.PointTest('test_add2'))
```
