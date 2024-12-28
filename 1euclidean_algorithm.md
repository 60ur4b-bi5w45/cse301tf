```markdown
# Euclidean Algorithm

The **Euclidean Algorithm** is a method for finding the greatest common divisor (GCD) of two integers. It is efficient and widely used in number theory and cryptography.

---

## The Core Idea

The algorithm is based on the principle that:
> The GCD of two numbers remains the same if the larger number is replaced by its remainder when divided by the smaller number.

This process is repeated until the remainder becomes zero. At that point, the divisor is the GCD.

---

## Steps of the Euclidean Algorithm

1. Start with two integers `a` and `b` (assume `a > b`).
2. Compute the remainder `r = a % b`.
3. Replace `a` with `b`, and `b` with `r`.
4. Repeat steps 2–3 until `b = 0`.
5. When `b = 0`, `a` is the GCD.

---

## Example: Finding GCD of 56 and 15

1. `a = 56`, `b = 15`
2. Compute `56 % 15 = 11`. Replace `a = 15`, `b = 11`.
3. Compute `15 % 11 = 4`. Replace `a = 11`, `b = 4`.
4. Compute `11 % 4 = 3`. Replace `a = 4`, `b = 3`.
5. Compute `4 % 3 = 1`. Replace `a = 3`, `b = 1`.
6. Compute `3 % 1 = 0`. Replace `a = 1`, `b = 0`.

Result: The GCD is `1`.

---

## Python Implementation

```python
def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

# Example
print(gcd(56, 15))  # Output: 1
```

---

## Proof

### Key Property

If `a` and `b` are integers (`a > b > 0`), then:

```
GCD(a, b) = GCD(b, r)
```

where `r = a % b` (remainder when `a` is divided by `b`).

### Proof of Key Property

1. Let `d` be the GCD of `a` and `b`. By definition:
   - `d` divides both `a` and `b` (`d | a` and `d | b`).
   - Since `r = a - q * b` (where `q = a // b`), `d` also divides `r`.

   Thus, `d` divides both `b` and `r`, so:
   ```
   d ≤ GCD(b, r)
   ```

2. Let `d' = GCD(b, r)`. Then:
   - `d'` divides both `b` and `r`.
   - Since `a = q * b + r`, `d'` also divides `a`.

   Thus, `d' ≤ GCD(a, b)`.

3. Since both `d ≤ d'` and `d' ≤ d`, we have `d = d'`.

---

### Proof of Termination

1. At each step, the pair `(a, b)` is replaced by `(b, a % b)`.
2. The remainder `r = a % b` satisfies:
   ```
   0 ≤ r < b
   ```
3. Therefore, the sequence of values (`b, a % b, ...`) strictly decreases and remains non-negative.
4. The process terminates when `b = 0`.

---

## Applications

1. **Simplifying Fractions**: Reducing fractions to their simplest form.
2. **Cryptography**: Used in algorithms like RSA for modular arithmetic.
3. **Diophantine Equations**: Solving equations of the form `ax + by = c`.
4. **LCM Calculation**: `LCM(a, b) = |a * b| / GCD(a, b)`.

---

The Euclidean Algorithm is a fundamental concept in mathematics and computer science. Let me know if you'd like to learn about its extended version or applications!
```
