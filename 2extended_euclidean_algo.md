The **Extended Euclidean Algorithm** is an extension of the Euclidean Algorithm that not only computes the greatest common divisor (GCD) of two numbers \(a\) and \(b\), but also finds two integers \(x\) and \(y\) (called Bezout coefficients) such that:

\[
a \cdot x + b \cdot y = \text{GCD}(a, b)
\]

---

### How It Works
1. **Start with the Euclidean Algorithm:** Use division to reduce the problem recursively until the GCD is found.
2. **Backtrack:** Express the GCD as a linear combination of \(a\) and \(b\) by substituting remainders from each step back into earlier equations.

---

### Steps with Example
Let’s find \(x\) and \(y\) for \(a = 56\) and \(b = 15\):

1. **Euclidean Algorithm**  
   Divide \(a\) by \(b\) repeatedly until the remainder is zero:
   - \(56 = 15 \times 3 + 11\)
   - \(15 = 11 \times 1 + 4\)
   - \(11 = 4 \times 2 + 3\)
   - \(4 = 3 \times 1 + 1\)
   - \(3 = 1 \times 3 + 0\)

   The GCD is \(1\).

2. **Backtracking to Find Coefficients**  
   Start from the last non-zero remainder equation and backtrack:
   - From \(4 = 3 \times 1 + 1\), rewrite as:  
     \[
     1 = 4 - 3 \times 1
     \]
   - Substitute \(3 = 11 - 4 \times 2\) into the equation:  
     \[
     1 = 4 - (11 - 4 \times 2)
     \]
     \[
     1 = 4 - 11 + 4 \times 2
     \]
     \[
     1 = 3 \times 4 - 11
     \]
   - Substitute \(4 = 15 - 11 \times 1\):  
     \[
     1 = 3 \times (15 - 11) - 11
     \]
     \[
     1 = 3 \times 15 - 3 \times 11 - 11
     \]
     \[
     1 = 3 \times 15 - 4 \times 11
     \]
   - Substitute \(11 = 56 - 15 \times 3\):  
     \[
     1 = 3 \times 15 - 4 \times (56 - 15 \times 3)
     \]
     \[
     1 = 3 \times 15 - 4 \times 56 + 12 \times 15
     \]
     \[
     1 = 15 \times 15 - 4 \times 56
     \]

   Thus, \(x = -4\) and \(y = 15\) satisfy \(56x + 15y = 1\).

---

### Python Implementation

Here’s how to compute it programmatically:

```python
def extended_gcd(a, b):
    if b == 0:
        return a, 1, 0  # Base case: gcd is `a`, coefficients are 1 and 0
    gcd, x1, y1 = extended_gcd(b, a % b)
    # Update x and y using recursion
    x = y1
    y = x1 - (a // b) * y1
    return gcd, x, y

# Example
a, b = 56, 15
gcd, x, y = extended_gcd(a, b)
print(f"GCD: {gcd}, x: {x}, y: {y}")
```

Output:
```
GCD: 1, x: -4, y: 15
```

---

### Applications
1. **Solving Linear Diophantine Equations:**  
   If \(ax + by = c\) has integer solutions, scale the coefficients from \(ax + by = \text{GCD}(a, b)\) appropriately.

2. **Modular Inverse:**  
   If \(a\) and \(m\) are coprime, the modular inverse of \(a \mod m\) is the \(x\) such that \(ax \mod m = 1\). This \(x\) is found using the Extended Euclidean Algorithm.

3. **Cryptography:**  
   Used in algorithms like RSA for computing modular inverses and key generation.

Let me know if you'd like to dive deeper into any specific application!
