# cse301tf

## 2021 - 5 number
```
### Problem Statement:

A professor frequently gives exams to her students. She can give three possible types of exams, and the class is graded as either having done well or badly. Let \( P_i \) denote the probability that the class does well on a type \( i \) exam, where:

- \( P_1 = 0.3 \),
- \( P_2 = 0.6 \),
- \( P_3 = 0.9 \).

The class's performance affects the type of exam given next:

- If the class does well on an exam, the next exam is equally likely to be any of the three types (i.e., a uniform distribution over all types).
- If the class does badly on an exam, the next exam is always Type 1.

(a) **What proportion of exams are of type \( i \), \( i = 1, 2, 3 \), assuming the process has run for a long time?**

### Solution:

We need to find the steady-state probabilities of being in each exam type. This can be done using the **Markov chain** approach, where we define the transition probabilities and solve for the steady-state distribution.

#### Transition Matrix:

Based on the given probabilities, the transition matrix \( P \) for the three exam types is as follows:

- **Type 1 to other types**:
  - If the class does well (probability 0.3), the next exam is equally likely to be Type 1, Type 2, or Type 3.
  - If the class does badly (probability 0.7), the next exam is always Type 1.
  
  Therefore, the transition probabilities from **Type 1** are:
  \[
  P(\text{Type 1 to Type 1}) = 0.7 + 0.3 \times \frac{1}{3} = 0.8
  \]
  \[
  P(\text{Type 1 to Type 2}) = 0.3 \times \frac{1}{3} = 0.1
  \]
  \[
  P(\text{Type 1 to Type 3}) = 0.3 \times \frac{1}{3} = 0.1
  \]

- **Type 2 to other types**:
  - If the class does well (probability 0.6), the next exam is equally likely to be Type 1, Type 2, or Type 3.
  - If the class does badly (probability 0.4), the next exam is always Type 1.
  
  Therefore, the transition probabilities from **Type 2** are:
  \[
  P(\text{Type 2 to Type 1}) = 0.4 + 0.6 \times \frac{1}{3} = 0.6
  \]
  \[
  P(\text{Type 2 to Type 2}) = 0.6 \times \frac{1}{3} = 0.2
  \]
  \[
  P(\text{Type 2 to Type 3}) = 0.6 \times \frac{1}{3} = 0.2
  \]

- **Type 3 to other types**:
  - If the class does well (probability 0.9), the next exam is equally likely to be Type 1, Type 2, or Type 3.
  - If the class does badly (probability 0.1), the next exam is always Type 1.
  
  Therefore, the transition probabilities from **Type 3** are:
  \[
  P(\text{Type 3 to Type 1}) = 0.1 + 0.9 \times \frac{1}{3} = 0.4
  \]
  \[
  P(\text{Type 3 to Type 2}) = 0.9 \times \frac{1}{3} = 0.3
  \]
  \[
  P(\text{Type 3 to Type 3}) = 0.9 \times \frac{1}{3} = 0.3
  \]

Thus, the transition matrix \( P \) is:

\[
P = \begin{pmatrix}
0.8 & 0.1 & 0.1 \\
0.6 & 0.2 & 0.2 \\
0.4 & 0.3 & 0.3
\end{pmatrix}
\]

#### Steady-State Equations:

Let \( \pi_1 \), \( \pi_2 \), and \( \pi_3 \) represent the steady-state probabilities of Type 1, Type 2, and Type 3 exams, respectively. The steady-state equations are obtained by solving the system:

\[
\pi_1 = 0.8\pi_1 + 0.6\pi_2 + 0.4\pi_3
\]
\[
\pi_2 = 0.1\pi_1 + 0.2\pi_2 + 0.3\pi_3
\]
\[
\pi_3 = 0.1\pi_1 + 0.2\pi_2 + 0.3\pi_3
\]

Along with the normalization condition:
\[
\pi_1 + \pi_2 + \pi_3 = 1
\]

#### Solving the System:

1. Simplify the first equation:
   \[
   \pi_1 - 0.8\pi_1 = 0.6\pi_2 + 0.4\pi_3
   \]
   \[
   0.2\pi_1 = 0.6\pi_2 + 0.4\pi_3 \quad \text{(Equation 1)}
   \]

2. Simplify the second equation:
   \[
   \pi_2 - 0.2\pi_2 = 0.1\pi_1 + 0.3\pi_3
   \]
   \[
   0.8\pi_2 = 0.1\pi_1 + 0.3\pi_3 \quad \text{(Equation 2)}
   \]

3. Simplify the third equation:
   \[
   \pi_3 - 0.3\pi_3 = 0.1\pi_1 + 0.2\pi_2
   \]
   \[
   0.7\pi_3 = 0.1\pi_1 + 0.2\pi_2 \quad \text{(Equation 3)}
   \]

Now we solve this system of equations. After performing the necessary algebraic manipulations (substitution or elimination), the steady-state probabilities are found to be:

\[
\pi_1 = \frac{5}{7}, \quad \pi_2 = \frac{1}{7}, \quad \pi_3 = \frac{1}{7}
\]

Thus, the **proportion of exams of type \( i \)** (in the long run) is:

- **Type 1 exams**: \( \pi_1 = \frac{5}{7} \),
- **Type 2 exams**: \( \pi_2 = \frac{1}{7} \),
- **Type 3 exams**: \( \pi_3 = \frac{1}{7} \).

These proportions represent the long-run distribution of exam types after many exams have been given.

---
```

Let me know if you'd like further clarification or if you'd like to move on to part (b) of the problem!
