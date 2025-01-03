The **repertoire method**, also known as the **method of undetermined coefficients**, is a systematic approach to solving **linear recurrence relations with constant coefficients**. This method is especially useful for non-homogeneous recurrences, where the recurrence relation includes a non-recursive term \(f(n)\).

---

### **General Form of Recurrence Relation**
The recurrence has the form:
\[
T(n) = c_1 T(n-1) + c_2 T(n-2) + \cdots + c_k T(n-k) + f(n),
\]
where:
- \(c_1, c_2, \dots, c_k\) are constants,
- \(f(n)\) is the non-homogeneous term.

---

### **Steps to Solve Using the Repertoire Method**
1. **Solve the Homogeneous Part**:
   Solve the recurrence without the \(f(n)\) term:
   \[
   T_h(n) = c_1 T_h(n-1) + c_2 T_h(n-2) + \cdots + c_k T_h(n-k).
   \]
   - Write the **characteristic equation**:
     \[
     r^k - c_1 r^{k-1} - c_2 r^{k-2} - \cdots - c_k = 0.
     \]
   - Find the roots of the characteristic equation:
     - **Distinct Roots**: The solution is a linear combination of powers of the roots.
     - **Repeated Roots**: Add polynomial factors to account for multiplicities.

2. **Guess the Particular Solution**:
   Based on the form of \(f(n)\), guess a particular solution \(T_p(n)\):
   - If \(f(n) = d\) (constant): Guess \(T_p(n) = A\).
   - If \(f(n) = dn\): Guess \(T_p(n) = An + B\).
   - If \(f(n) = d n^m\): Guess \(T_p(n) = A n^m + B n^{m-1} + \dots + C\).
   - If \(f(n) = d \cdot a^n\): Guess \(T_p(n) = A a^n\).
   - If \(f(n)\) matches the form of the homogeneous solution, multiply the guess by \(n\) (to avoid overlap).

3. **Substitute and Solve**:
   Substitute \(T_p(n)\) into the original recurrence to find the coefficients.

4. **Combine the Solutions**:
   The general solution is:
   \[
   T(n) = T_h(n) + T_p(n).
   \]

5. **Apply Initial Conditions**:
   Use the initial values to solve for any remaining constants in the general solution.

---

### **Example 1: Constant Non-Homogeneous Term**
Solve:
\[
T(n) = 2T(n-1) - T(n-2) + 3, \quad T(0) = 1, T(1) = 2.
\]

**Step 1: Solve Homogeneous Part**  
The characteristic equation is:
\[
r^2 - 2r + 1 = 0 \quad \implies \quad (r-1)^2 = 0.
\]
Solution:
\[
T_h(n) = C_1 \cdot 1^n + C_2 \cdot n \cdot 1^n = C_1 + C_2 n.
\]

**Step 2: Guess Particular Solution**  
Since \(f(n) = 3\) (constant), guess \(T_p(n) = A\).

**Step 3: Substitute**  
Substitute \(T_p(n) = A\) into the recurrence:
\[
A = 2A - A + 3 \quad \implies \quad A = 3.
\]
Thus, \(T_p(n) = 3\).

**Step 4: General Solution**  
\[
T(n) = T_h(n) + T_p(n) = C_1 + C_2 n + 3.
\]

**Step 5: Apply Initial Conditions**  
Use \(T(0) = 1\) and \(T(1) = 2\):
- \(T(0) = C_1 + 3 = 1 \quad \implies \quad C_1 = -2\).
- \(T(1) = C_1 + C_2 + 3 = 2 \quad \implies \quad -2 + C_2 + 3 = 2 \quad \implies \quad C_2 = 1\).

Final solution:
\[
T(n) = -2 + n + 3 = n + 1.
\]

---

### **Example 2: Exponential Non-Homogeneous Term**
Solve:
\[
T(n) = 3T(n-1) - 2T(n-2) + 2^n, \quad T(0) = 0, T(1) = 3.
\]

**Step 1: Solve Homogeneous Part**  
The characteristic equation is:
\[
r^2 - 3r + 2 = 0 \quad \implies \quad (r-1)(r-2) = 0.
\]
Solution:
\[
T_h(n) = C_1 \cdot 1^n + C_2 \cdot 2^n = C_1 + C_2 \cdot 2^n.
\]

**Step 2: Guess Particular Solution**  
Since \(f(n) = 2^n\), guess \(T_p(n) = A \cdot 2^n\).

**Step 3: Substitute**  
Substitute \(T_p(n) = A \cdot 2^n\) into the recurrence:
\[
A \cdot 2^n = 3A \cdot 2^{n-1} - 2A \cdot 2^{n-2} + 2^n.
\]
Divide through by \(2^n\):
\[
A = \frac{3A}{2} - \frac{A}{2} + 1.
\]
Simplify:
\[
A = A + 1 \quad \implies \quad A = 1.
\]
Thus, \(T_p(n) = 2^n\).

**Step 4: General Solution**  
\[
T(n) = T_h(n) + T_p(n) = C_1 + C_2 \cdot 2^n + 2^n.
\]

**Step 5: Apply Initial Conditions**  
Use \(T(0) = 0\) and \(T(1) = 3\):
- \(T(0) = C_1 + 1 = 0 \quad \implies \quad C_1 = -1\).
- \(T(1) = C_1 + 2C_2 + 2 = 3 \quad \implies \quad -1 + 2C_2 + 2 = 3 \quad \implies \quad C_2 = 1\).



Let’s go over the **repertoire method** properly and focus on clarity. This method is primarily used for solving **recurrence relations**, particularly non-homogeneous ones. Let me explain it **accurately and concisely**.

---

### **What is the Repertoire Method?**
The repertoire method solves **linear recurrence relations with constant coefficients** by building a "repertoire" of solutions for various forms of the non-homogeneous term \(f(n)\). The idea is to construct a particular solution based on the form of \(f(n)\), solve the homogeneous part, and combine both.

---

### **General Form of the Recurrence Relation**
\[
T(n) = c_1 T(n-1) + c_2 T(n-2) + \cdots + c_k T(n-k) + f(n),
\]
where:
- \(c_1, c_2, \dots, c_k\) are constants,
- \(f(n)\) is the **non-homogeneous term**.

---

### **Steps in the Repertoire Method**

1. **Solve the Homogeneous Part**:
   Solve the recurrence without the \(f(n)\) term:
   \[
   T_h(n) = c_1 T_h(n-1) + c_2 T_h(n-2) + \cdots + c_k T_h(n-k).
   \]
   - This involves finding the roots of the **characteristic equation**.

2. **Construct a Repertoire**:
   Build a "repertoire" of solutions for \(f(n)\), depending on its type. Here's the guide for common forms:
   - \(f(n) = d\): Guess \(T_p(n) = A\),
   - \(f(n) = dn\): Guess \(T_p(n) = An + B\),
   - \(f(n) = dn^m\): Guess \(T_p(n) = A n^m + B n^{m-1} + \dots + C\),
   - \(f(n) = a^n\): Guess \(T_p(n) = A a^n\),
   - \(f(n) = n^m a^n\): Guess \(T_p(n) = (An^m + Bn^{m-1} + \dots) a^n\).

   If \(f(n)\) overlaps with a term in the homogeneous solution, multiply by \(n\) until independence is achieved.

3. **Combine the Solutions**:
   The general solution is:
   \[
   T(n) = T_h(n) + T_p(n),
   \]
   where \(T_p(n)\) is the particular solution.

4. **Apply Initial Conditions**:
   Use the initial values \(T(0), T(1), \dots\) to solve for constants in \(T_h(n)\).

---

### **Correct Example**
Solve:
\[
T(n) = 2T(n-1) - T(n-2) + n, \quad T(0) = 1, T(1) = 3.
\]

**Step 1: Solve the Homogeneous Part**  
Solve \(T(n) = 2T(n-1) - T(n-2)\).  
The characteristic equation is:
\[
r^2 - 2r + 1 = 0 \quad \implies \quad (r-1)^2 = 0.
\]
Thus, the solution is:
\[
T_h(n) = C_1 + C_2 n.
\]

**Step 2: Guess Particular Solution**  
The non-homogeneous term \(f(n) = n\).  
Guess:
\[
T_p(n) = An + B.
\]

Substitute \(T_p(n)\) into the recurrence:
\[
An + B = 2(A(n-1) + B) - (A(n-2) + B) + n.
\]

Simplify:
\[
An + B = 2(An - A + B) - (An - 2A + B) + n,
\]
\[
An + B = 2An - 2A + 2B - An + 2A - B + n,
\]
\[
An + B = An + n + B.
\]

Thus:
\[
A = 1, \quad B = 0.
\]
So:
\[
T_p(n) = n.
\]

**Step 3: Combine the Solutions**  
The general solution is:
\[
T(n) = T_h(n) + T_p(n) = C_1 + C_2 n + n.
\]

**Step 4: Apply Initial Conditions**  
Using \(T(0) = 1\) and \(T(1) = 3\):
- \(T(0) = C_1 = 1\),
- \(T(1) = C_1 + C_2 \cdot 1 + 1 = 3 \quad \implies \quad 1 + C_2 + 1 = 3 \quad \implies \quad C_2 = 1\).

Final solution:
\[
T(n) = 1 + n + n = 1 + 2n.
\]

---

### **Key Advantages of Repertoire Method**
- It systematically builds particular solutions based on \(f(n)\).
- It avoids blindly guessing and directly ties the form of \(T_p(n)\) to \(f(n)\).

Let me know if you'd like more examples or further clarification!

Final solution:
\[
T(n) = -1 + 2^n + 2^n = -1 + 2^{n+1}.
\]

---

Let me know if you need further examples or explanations!
