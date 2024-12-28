### Linear Diophantine Equations

A **Diophantine equation** is a polynomial equation where the solutions are required to be integers. The simplest form is the **Linear Diophantine Equation**:

\[
a \cdot x + b \cdot y = c
\]

Where:
- \(a\), \(b\), and \(c\) are integers.
- \(x\) and \(y\) are unknown integers to solve for.

---

### **Conditions for Solvability**

The equation \(a \cdot x + b \cdot y = c\) has integer solutions if and only if:

\[
\text{GCD}(a, b) \,|\, c
\]

---

### **Steps to Solve**

1. **Check for Solvability**  
   Compute the greatest common divisor (GCD) of \(a\) and \(b\). If \(c\) is divisible by \(\text{GCD}(a, b)\), proceed; otherwise, no solution exists.

2. **Use the Extended Euclidean Algorithm**  
   Find integers \(x_0\) and \(y_0\) such that:
   \[
   a \cdot x_0 + b \cdot y_0 = \text{GCD}(a, b)
   \]

3. **Scale to Match \(c\)**  
   Multiply \(x_0\) and \(y_0\) by \(\frac{c}{\text{GCD}(a, b)}\) to get a particular solution \((x_p, y_p)\).

4. **Find General Solution**  
   The general solution is:
   \[
   x = x_p + \frac{b}{\text{GCD}(a, b)} \cdot t
   \]
   \[
   y = y_p - \frac{a}{\text{GCD}(a, b)} \cdot t
   \]
   Where \(t\) is any integer.

---

### **Example**

Solve \(56x + 15y = 7\).

#### Step 1: Check Solvability  
\(\text{GCD}(56, 15) = 1\), and \(1 \,|\, 7\), so the equation is solvable.

#### Step 2: Use Extended Euclidean Algorithm  
From the Extended Euclidean Algorithm, we know:
\[
56(-4) + 15(15) = 1
\]

#### Step 3: Scale to Match \(c = 7\)  
Multiply through by \(7\):
\[
56(-28) + 15(105) = 7
\]

Thus, a particular solution is \(x_p = -28\), \(y_p = 105\).

#### Step 4: General Solution  
The general solution is:
\[
x = -28 + 15t
\]
\[
y = 105 - 56t
\]
Where \(t\) is any integer.

#### Particular Examples:
- For \(t = 0\): \(x = -28, y = 105\)
- For \(t = 1\): \(x = -13, y = 49\)
- For \(t = -1\): \(x = -43, y = 161\)

---

### **Python Implementation**

Here’s how to solve a Linear Diophantine Equation programmatically:

```python
def extended_gcd(a, b):
    if b == 0:
        return a, 1, 0  # GCD is `a`, coefficients are 1 and 0
    gcd, x1, y1 = extended_gcd(b, a % b)
    x = y1
    y = x1 - (a // b) * y1
    return gcd, x, y

def solve_diophantine(a, b, c):
    gcd, x0, y0 = extended_gcd(a, b)
    if c % gcd != 0:
        return None  # No solution
    scale = c // gcd
    x0 *= scale
    y0 *= scale
    return gcd, x0, y0

# Example
a, b, c = 56, 15, 7
result = solve_diophantine(a, b, c)
if result:
    gcd, x0, y0 = result
    print(f"Particular solution: x = {x0}, y = {y0}")
    print(f"General solution: x = {x0} + {b // gcd}t, y = {y0} - {a // gcd}t")
else:
    print("No solution exists.")
```

---

### **Applications of Linear Diophantine Equations**

1. **Cryptography:**  
   Modular arithmetic problems (e.g., finding modular inverses).

2. **Number Theory:**  
   Solving problems involving integer partitions.

3. **Optimization Problems:**  
   Resource allocation with integer constraints.

Let me know if you need further elaboration or additional examples!
