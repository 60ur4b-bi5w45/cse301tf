# Extended Euclidean Algorithm

The **Extended Euclidean Algorithm** builds upon the Euclidean Algorithm and not only computes the GCD of two integers `a` and `b`, but also finds integers `x` and `y` such that:
```
\[
ax + by = \text{GCD}(a, b)
\]
```
These integers `x` and `y` are called **Bezout coefficients**. This property is particularly useful in solving linear Diophantine equations and modular inverses in cryptography.

---

## Core Idea

Using the steps of the Euclidean Algorithm, we express the GCD as a linear combination of `a` and `b` by backtracking through the remainders.

For example, if:

1. \( r = a - q \cdot b \)
2. Then, \( \text{GCD}(a, b) = \text{GCD}(b, r) \), and
3. \( r \) can be expressed in terms of \( a \) and \( b \).

---

## Steps of the Extended Algorithm

1. Use the Euclidean Algorithm to compute the GCD of \( a \) and \( b \).
2. Backtrack to express the GCD as a linear combination of \( a \) and \( b \).
3. Stop when the GCD is written as \( ax + by \).

---

## Example: Finding \( x \) and \( y \) for \( a = 56 \), \( b = 15 \)

### Euclidean Algorithm
1. \( 56 = 15 \cdot 3 + 11 \)
2. \( 15 = 11 \cdot 1 + 4 \)
3. \( 11 = 4 \cdot 2 + 3 \)
4. \( 4 = 3 \cdot 1 + 1 \)
5. \( 3 = 1 \cdot 3 + 0 \)

GCD is \( 1 \).

---

### Backtracking to Find \( x \) and \( y \)

1. From \( 4 = 3 \cdot 1 + 1 \), rewrite \( 1 \):
   \[
   1 = 4 - 3 \cdot 1
   \]

2. Substitute \( 3 = 11 - 4 \cdot 2 \) into \( 1 \):
   \[
   1 = 4 - (11 - 4 \cdot 2) \cdot 1
   \]
   \[
   1 = 4 - 11 + 4 \cdot 2
   \]
   \[
   1 = 3 \cdot 4 - 11
   \]

3. Substitute \( 4 = 15 - 11 \cdot 1 \) into \( 1 \):
   \[
   1 = 3 \cdot (15 - 11) - 11
   \]
   \[
   1 = 3 \cdot 15 - 3 \cdot 11 - 11
   \]
   \[
   1 = 3 \cdot 15 - 4 \cdot 11
   \]

4. Substitute \( 11 = 56 - 15 \cdot 3 \) into \( 1 \):
   \[
   1 = 3 \cdot 15 - 4 \cdot (56 - 15 \cdot 3)
   \]
   \[
   1 = 3 \cdot 15 - 4 \cdot 56 + 12 \cdot 15
   \]
   \[
   1 = 15 \cdot 15 - 4 \cdot 56
   \]

Thus, \( x = -4 \), \( y = 15 \) satisfy \( 56x + 15y = 1 \).

---

## Python Implementation

```python
def extended_gcd(a, b):
    if b == 0:
        return a, 1, 0  # Base case: GCD is `a`, coefficients are `1` and `0`.
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

## Applications

1. **Solving Linear Diophantine Equations**:
   Solve equations of the form \( ax + by = c \) by scaling \( x \) and \( y \) from \( ax + by = \text{GCD}(a, b) \).

2. **Modular Inverse**:
   The modular inverse of \( a \mod m \) exists if and only if \( \text{GCD}(a, m) = 1 \). Using the Extended Euclidean Algorithm, the modular inverse is \( x \) from \( ax + my = 1 \).

3. **Cryptography**:
   Used in algorithms like RSA for modular arithmetic and key generation.

---

The Extended Euclidean Algorithm is a powerful tool in number theory and cryptography. Let me know if you'd like to explore specific applications in more detail!
