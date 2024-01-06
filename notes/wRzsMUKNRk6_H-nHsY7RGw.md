$$
<proof>\\
Total\ time\ T(N)\ is\ O(E\ log\ E)\\
\left\{\begin{matrix}
1.\ T(N) \leq c(E+N\ log\ N)\\
2.\ E \geq N-1
\end{matrix}\right.\\
condition:\ (1)\ E=N-1\ (2)\ E>N-1\\
(1)\ E=N-1:\\
T(N) \leq c(E+N\ log\ N)\\
=c(E+(E+1)\ log\ (E+1))\\
\leq c(E+(E+E)\ log\ (E+E))\\
\leq c(E+2E\ (log\ E+1))\\
= c(3E\ +2E\ log\ E)\\
\leq c(3E\ log\ E+2E\ log\ E)\\
=5c(E\ log\ E)\\
=O(E\ log\ E)\\
(2)E>N-1 \rightarrow E \geq N\\
T(N)\leq c(E+E\ log\ E)\\
\leq c(E\ log\ E+E\ log\ E)\\
=2c(E\ log\ E)\\
O(E\ log E)
$$