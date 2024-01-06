# Chapter 1-3: An Example of Gaussian Elimination
ex.
$$
\left\{ 
    \begin{array}
           22u +v+w = 5 \\
           4u-6v\ \ \ \ \ \ =-2\\
           -2u+7v+2w=9
    \end{array}
\right.
$$

$$ $$

\begin{matrix}
    (2)&1&1&5\\
    4&-6&0&-2\\
    -2&7&2&9
\end{matrix}

$$ \downarrow$$

\begin{bmatrix}
    2&1&1&5\\
    0&(-8)&-2&-12\\
    0&8&3&14
\end{bmatrix}
$$ \downarrow$$

\begin{bmatrix}
    2&1&1&5\\
    0&-8&-2&-12\\
    0&0&(1)&2
\end{bmatrix}

$$The\ digits\ enclosed\ by\ brackets\ are\ 1st/2nd/3rd\ pivots
$$


# Some new noun
* **Pivot** is the non-zero digit in each row
* **Forward Elimination(FE)** is using the row that the pivot in to eliminate other rows.
* **Back Substitution(BS)** is when we know the value of an unknown, we substitute it into other equation.

**//Note//** By definition, pivots ++can't be zero!!++

# Q&A

Q1: Under what circumstance could the process break down?
- Something ++must++ go wrong in **singular case.**
- Something ++might++ go wrong in **nonsingular case.**
 (A zero appear in a pivot position. However, we do not know whether a zero will appear until we try. If in the process, there are n (non-zero)pivots,then there's only one solution)

Q2: How many seperate arithmetical operations does elimination require for n unknowns?
- A single operation  = each division & each multiplication-subtraction 

$$FE=\sum_{i=1}^{n} i(i-1) = \frac{n(n-1)(n+1)}{3} $$

$$RHS=\sum_{i=1}^{n-1}i=\frac{n(n-1)}{2}$$

$$BS=\sum_{i=1}^{n}i=\frac{n(n+1)}{2}$$

$$ Total = FE+RHS+BS= \frac{n^3+3n^2-n}{3} $$

Last Chapter: [Geometry of Linear Equation](https://g0v.hackmd.io/rmrPvL-wTkmkgpp4tT2OyA?view)
Next Chapter: [Matrix Notation and Matrix Multiplication](https://g0v.hackmd.io/ujx1rysxRyChze9DvkOprA)



