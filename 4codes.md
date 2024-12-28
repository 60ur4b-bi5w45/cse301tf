Here are Python implementations for the three algorithms: 

---

### 1. **Standard Euclidean Algorithm**
```python
def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

# Example
a, b = 56, 15
print(f"GCD of {a} and {b} is: {gcd(a, b)}")
```

---

### 2. **Extended Euclidean Algorithm**
This algorithm computes the GCD and also finds integers \(x\) and \(y\) such that \(a \cdot x + b \cdot y = \text{GCD}(a, b)\).
```python
def extended_gcd(a, b):
    if b == 0:
        return a, 1, 0  # GCD is a, coefficients are x = 1, y = 0
    gcd, x1, y1 = extended_gcd(b, a % b)
    x = y1
    y = x1 - (a // b) * y1
    return gcd, x, y

# Example
a, b = 56, 15
gcd, x, y = extended_gcd(a, b)
print(f"GCD of {a} and {b} is: {gcd}")
print(f"Coefficients: x = {x}, y = {y}")
```

---

### 3. **Solve Linear Diophantine Equation**
This algorithm uses the extended Euclidean algorithm to find integer solutions to the equation \(a \cdot x + b \cdot y = c\), if it is solvable.
```python
def solve_diophantine(a, b, c):
    gcd, x0, y0 = extended_gcd(a, b)
    if c % gcd != 0:
        return None  # No solution exists
    # Scale the solution to match `c`
    scale = c // gcd
    x0 *= scale
    y0 *= scale
    return gcd, x0, y0

# Example
a, b, c = 56, 15, 7
result = solve_diophantine(a, b, c)
if result:
    gcd, x, y = result
    print(f"Solution exists with GCD = {gcd}")
    print(f"Particular solution: x = {x}, y = {y}")
    print(f"General solution: x = {x} + {b // gcd}t, y = {y} - {a // gcd}t (where t is any integer)")
else:
    print("No solution exists.")
```

---

### Explanation of the Outputs

- **Standard Euclidean Algorithm**: Computes the greatest common divisor (GCD) of two integers.
- **Extended Euclidean Algorithm**: Computes the GCD and also finds coefficients \(x\) and \(y\) such that \(a \cdot x + b \cdot y = \text{GCD}(a, b)\).
- **Linear Diophantine Equation**: Determines if integer solutions exist for \(a \cdot x + b \cdot y = c\) and, if they do, provides a particular solution and the general solution.

Let me know if you need further clarification or enhancements!
