The **Euclidean Algorithm** is a method for finding the greatest common divisor (GCD) of two integers. It’s efficient and forms the basis for many other algorithms in number theory and cryptography.

---

### **The Core Idea**
The algorithm is based on the principle that:
> The GCD of two numbers doesn't change if the larger number is replaced by its remainder when divided by the smaller number.

This process is repeated until the remainder becomes zero. At that point, the divisor is the GCD of the two numbers.

---

### **Steps of the Euclidean Algorithm**
1. Start with two integers \( a \) and \( b \) (\( a > b \)).
2. Compute the remainder \( r = a \mod b \).
3. Replace \( a \) with \( b \), and \( b \) with \( r \).
4. Repeat steps 2–3 until \( b = 0 \).
5. When \( b = 0 \), \( a \) is the GCD.

---

### **Example**
Find the GCD of \( 56 \) and \( 15 \).

1. \( a = 56 \), \( b = 15 \).
2. Compute \( 56 \mod 15 = 11 \). Replace \( a = 15 \), \( b = 11 \).
3. Compute \( 15 \mod 11 = 4 \). Replace \( a = 11 \), \( b = 4 \).
4. Compute \( 11 \mod 4 = 3 \). Replace \( a = 4 \), \( b = 3 \).
5. Compute \( 4 \mod 3 = 1 \). Replace \( a = 3 \), \( b = 1 \).
6. Compute \( 3 \mod 1 = 0 \). Replace \( a = 1 \), \( b = 0 \).

Result: The GCD is \( 1 \).

---

### **Python Implementation**

```python
def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

# Example
print(gcd(56, 15))  # Output: 1
```

---

### **Why It Works**
The algorithm relies on the fact that any common divisor of \( a \) and \( b \) must also divide \( a \mod b \). Therefore, reducing \( a \) and \( b \) in this way preserves the GCD.

---

### **Applications**
1. **Simplifying Fractions**: Reducing fractions to their simplest form.
2. **Cryptography**: Used in algorithms like RSA for modular arithmetic.
3. **Diophantine Equations**: Solving equations of the form \( ax + by = c \).
4. **LCM Calculation**: \( \text{LCM}(a, b) = \frac{|a \cdot b|}{\text{GCD}(a, b)} \).

The **Euclidean Algorithm** works based on the mathematical property of divisors. Here's the proof step-by-step:

---

### **Key Property Used**
If \( a \) and \( b \) are integers (\( a > b > 0 \)), then:

\[
\text{GCD}(a, b) = \text{GCD}(b, r)
\]

where \( r = a \mod b \) is the remainder when \( a \) is divided by \( b \).

---

### **Proof of Key Property**
Let \( d \) be the greatest common divisor of \( a \) and \( b \). By definition:

1. \( d \mid a \) and \( d \mid b \) (i.e., \( d \) divides both \( a \) and \( b \)).
2. Since \( r = a - q \cdot b \) (where \( q = \lfloor a / b \rfloor \), the integer quotient),
   \[
   d \mid r
   \]
   because \( d \mid a \) and \( d \mid b \) imply \( d \mid (a - q \cdot b) \).

Thus, \( d \) divides both \( b \) and \( r \), meaning:
\[
d \leq \text{GCD}(b, r).
\]

Conversely, let \( d' = \text{GCD}(b, r) \). Then:
1. \( d' \mid b \) and \( d' \mid r \).
2. Since \( a = q \cdot b + r \),
   \[
   d' \mid a.
   \]

Thus, \( d' \leq \text{GCD}(a, b) \).

Since both \( d \leq d' \) and \( d' \leq d \), we conclude \( d = d' \). Therefore:
\[
\text{GCD}(a, b) = \text{GCD}(b, r).
\]

---

### **Proof of Termination**
The Euclidean Algorithm guarantees termination because:

1. At each step, the pair \( (a, b) \) is replaced by \( (b, a \mod b) \).
2. The remainder \( r = a \mod b \) satisfies:
   \[
   0 \leq r < b.
   \]
3. Therefore, the sequence of values \( b, a \mod b, \dots \) strictly decreases and remains non-negative.
4. Since \( b \) is a positive integer, the sequence eventually reaches \( 0 \).

When \( b = 0 \), the algorithm terminates, and \( a \) is the GCD.

---

### **Example with Proof**
Let \( a = 56 \), \( b = 15 \):
1. \( 56 = 15 \cdot 3 + 11 \). So, \( \text{GCD}(56, 15) = \text{GCD}(15, 11) \).
2. \( 15 = 11 \cdot 1 + 4 \). So, \( \text{GCD}(15, 11) = \text{GCD}(11, 4) \).
3. \( 11 = 4 \cdot 2 + 3 \). So, \( \text{GCD}(11, 4) = \text{GCD}(4, 3) \).
4. \( 4 = 3 \cdot 1 + 1 \). So, \( \text{GCD}(4, 3) = \text{GCD}(3, 1) \).
5. \( 3 = 1 \cdot 3 + 0 \). So, \( \text{GCD}(3, 1) = 1 \).

By the proof, \( \text{GCD}(56, 15) = 1 \).

---

### **Conclusion**
The Euclidean Algorithm is correct because:
1. The GCD remains unchanged during the steps.
2. The process terminates in a finite number of steps when the remainder becomes \( 0 \).

If you'd like, I can explain how this proof extends to the **Extended Euclidean Algorithm**!

---

Let me know if you'd like to explore the **Extended Euclidean Algorithm**, which also finds coefficients \( x \) and \( y \) such that \( ax + by = \text{GCD}(a, b) \).
