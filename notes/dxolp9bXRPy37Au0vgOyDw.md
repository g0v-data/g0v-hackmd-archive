# Chapter 1-5: Triangular Factors and Row exchanges
$$Ax=b$$
$$
\Rightarrow LUx=b \ 
\left\{ 
    \begin{array}
           LLc=b\\ 
    Ux=c\\
    \end{array}
\right.
$$

$$
Example.\\
\begin{bmatrix}2 & 4 & -2\\4 & 9 & -3\\-2 & -3 & 7\end{bmatrix}\begin{bmatrix}u\\v\\w \end{bmatrix} =\begin{bmatrix}2\\8\\10\end{bmatrix}=b\\
\ \ \ \ \ \ \ <A>\ \  \ \ \ <x>\ \ <b>\\
$$

$$
A=
\begin{bmatrix}
    2 & 4 & -2 &2\\
    4 & 9 & -3 &8\\
    -2 & -3 & 7 & 10
\end{bmatrix}
\rightarrow
\begin{bmatrix}
    2 & 4 & -2 & 2\\
    0 & 1 & 1 & 4\\
    0 & 1 & 5 & 12\\
\end{bmatrix}
\rightarrow
\begin{bmatrix}
    2 & 4 & -2 & 2\\
    0 & 1 & 1 & 4\\
    0 & 0 & 4 & 8\\
\end{bmatrix}
\\
$$

$$
E=
\begin{bmatrix}
    1 & 0 & 0 \\
    \mathbf{-2} & 1 & 0 \\
    0 & 0 & 1 \\
\end{bmatrix}
F=
\begin{bmatrix}
    1 & 0 & 0 \\
    0 & 1 & 0 \\
    \mathbf{1} & 0 & 1 \\
\end{bmatrix}
G=
\begin{bmatrix}
    1 & 0 & 0 \\
    0 & 1 & 0 \\
    0 & \mathbf{-1} & 1 \\
\end{bmatrix}
$$

$$
i.e. GFE\ Ax = 
\begin{bmatrix}
    2 & 4 & -2\\
    0 & 1 & 1\\
    0 & 0 & 4\\
\end{bmatrix}
\begin{bmatrix}
    u\\v\\w
\end{bmatrix}
=Ux=c=\begin{bmatrix}
    2\\4\\8
\end{bmatrix}
$$

# Q.How can we undo the steps of GE?
$$E^{-1}F^{-1}G^{-1}GFEA=A=E^{-1}F^{-1}G^{-1}U=\underline{LU}$$
$$
E^{-1}=
\begin{bmatrix}
    1 & 0 & 0 \\
    \mathbf{2} & 1 & 0 \\
    0 & 0 & 1 \\
\end{bmatrix}
F^{-1}=
\begin{bmatrix}
    1 & 0 & 0 \\
    0 & 1 & 0 \\
    \mathbf{-1} & 0 & 1 \\
\end{bmatrix}
G^{-1}=
\begin{bmatrix}
    1 & 0 & 0 \\
    0 & 1 & 0 \\
    0 & \mathbf{1} & 1 \\
\end{bmatrix}
$$
$$L=E^{-1}F^{-1}G^{-1}=
\begin{bmatrix}
    1 & 0 & 0 \\
    2 & 1 & 0 \\
    -1 & 1 & 1 \\
\end{bmatrix}\\
\Rightarrow
records\ everything \ that\ has\ been\ done\ so\ far!
$$

# Triangular Factorization A=LU
If no row exchanges are required, the original matrix A can be written as A=LU

The matrix L is a lower triangular with 1's on the diaginal and the multiplers $l_{ij}$ (taken from elimination) below the diagonal.

U is the upper triangular matrix which appears after forward elimination v before back-substitution; its diagonal entries are pivots!

$Note:\ LU\ decomposition\ is\  \mathbf{NOT}\ unique.$

$$
A=
\begin{bmatrix}
2 & -1 & -1\\
0 & -4 & 2\\
6 & -3 & 0\\
\end{bmatrix}=
\begin{bmatrix}
1 & 0 & 0\\
0 & 1 & 0\\
3 & 0 & 1\\
\end{bmatrix}
\begin{bmatrix}
2 & -1 & -1\\
0 & -4 & 2\\
6 & 0 & 3\\
\end{bmatrix}=
\begin{bmatrix}
2 & 0 & 0\\
0 & -4 & 0\\
6 & 6 & 3\\
\end{bmatrix}
\begin{bmatrix}
1 & -\frac{1}{2} & -\frac{1}{2}\\
0 & 1 & -\frac{1}{2}\\
0 & 0 & 1\\
\end{bmatrix}
$$

# Exercise
$$
A=
\begin{bmatrix}
4&5\\
1&2\\
\end{bmatrix};
A=
\begin{bmatrix}
2&6&5\\
-1&4&-2\\
1&2&3
\end{bmatrix};
A=
\begin{bmatrix}
1 & -1 & 0 & 0\\-1 & 2 & -1 & 0\\0 & 1 & 2 & -1\\0 & 0 & -1 & 2\\
\end{bmatrix}_{tridiagonal\ matrix}
$$
# One Linear System = Two Triangular Systems
$$Ax=b \Rightarrow Ux=c\ \&\ Lc=b$$
The LU form is unsymmetric in one aspect
U has pivots along its diagonal where L always has 1's.
We can rewrite U as:
$$
U=
\begin{bmatrix}
d_1 &  &  & \\ & d_2 &  & \\ &  & \ddots & \\ &  &  & d_n\\
\end{bmatrix}\begin{bmatrix}
1 &  u_{12}& u_{13} & ... \\ 0 & 1 &  u_{23}&... \\ \vdots &\vdots  & \ddots & ...\\0 & ... &...  & 1\\
\end{bmatrix}\\
$$
$Example.$



$$
A=\begin{bmatrix}3&4\\1&2\end{bmatrix}
=\begin{bmatrix}1&0\\ \frac{1}{3}&1\end{bmatrix}
\begin{bmatrix}3&4\\0&\frac{2}{3}\end{bmatrix}=\begin{bmatrix}1&0\\ \frac{1}{3}&1\end{bmatrix}
\begin{bmatrix}3&0\\0&\frac{2}{3}\end{bmatrix}\begin{bmatrix}1&\frac{4}{3}\\ 0&1\end{bmatrix}
=L\ D\ U
$$

$$Theorem.$$

$$
If\ A=L_1D_1U_1\ and\ A=L_2D_2U_2\\
then\ L_1=L_2,D_1=D_2,\ and\ U_1=U_2\\
i.e. if\ A\ has\ LDU\ decomposition,\ then\ it\ \mathbf{IS\ UNIQUE!}
$$

# Row Exchange and Permutation Matrices
$$P_{23}=\begin{bmatrix}
1 & 0 & 0\\0 & 0 & 1\\0 & 1 & 0\\
\end{bmatrix} <Permutation\ matrix\ P_{ij}>$$
$Example.$

$$
Px=\begin{bmatrix}1 & 0 & 0\\0 & 0 & 1\\0 & 1 & 0\\ \end{bmatrix}
\begin{bmatrix}1\\5\\3\\ \end{bmatrix}
=\begin{bmatrix}1\\3\\5\\ \end{bmatrix}
$$

$$
PA=
\begin{bmatrix}
    1 & 0 & 0\\
    0 & 0 & 1\\
    0 & 1 & 0\\ 
\end{bmatrix}
\begin{bmatrix}
    2 & 4 & 1\\
    0 & 0 & 3\\
    0 & 6 & 5\\ 
\end{bmatrix}=
\begin{bmatrix}
    2 & 4 & 1\\
    0 & 6 & 5\\ 
    0 & 0 & 3\\
\end{bmatrix}
<performing\ row\ exchange\ of\ A>
$$

$$
BP=
\begin{bmatrix}
    2 & 2 & 1\\
    3 & 0 & 7\\
    1 & 4 & 5\\ 
\end{bmatrix}
\begin{bmatrix}
    1 & 0 & 0\\
    0 & 0 & 1\\
    0 & 1 & 0\\ 
\end{bmatrix}=
\begin{bmatrix}
    2 & 1 & 2\\
    3 & 7 & 0\\ 
    1 & 5 & 4\\
\end{bmatrix}
<performing\ column\ exchange\ of\ B>
$$

$$
If\ Ax=b\Rightarrow P(Ax)=P(b)\\
Should\ we\ permute\ the\ components\ of\ x=\begin{bmatrix}u\\v\\w\\ \end{bmatrix} as\ well?\ \mathbf{NO!}
$$

$$\\ \Large Theorem.$$
In the nonsingular case, there's a permutation matrix P that recorders the rows of A to avoid zeros in the pivot positions.
In this case,
(1)Ax=b has a **unique** solution
(2)It is found by **elimination with row exchanges.**
(3)With the rows recordered in advance,PA can be factored into **LU(PA=LU)**
(4)In singular case, **no recordering can produce a full set of pivots.**

$Example.$
$$
A=
\begin{bmatrix}
    1 & 1 & 1\\
    1 & 1 & 3\\ 
    2 & 5 & 8\\
\end{bmatrix}
\rightarrow
\begin{bmatrix}
    1 & 1 & 1\\
    0 & 0 & 2\\ 
    0 & 3 & 6\\
\end{bmatrix}
\rightarrow
\begin{bmatrix}
    1 & 1 & 1\\
    0 & 3 & 6\\
    0 & 0 & 2\\ 
\end{bmatrix}
=U
$$

$$
L \not=
\begin{bmatrix}
    1 & 0 & 0\\
    1 & 1 & 0\\
    2 & 0 & 1\\ 
\end{bmatrix}!\ ,\ L=
\begin{bmatrix}
    1 & 0 & 0\\
    2 & 1 & 0\\
    1 & 0 & 1\\ 
\end{bmatrix}
\because it\ has\ performed\ exchange 
$$

# Summary
$\large A\ \normalsize good\ code\ for\ Gaussian\ Elimination\ keeps\ a\ record\ of\ L,U \& P$

$\large They \normalsize \  allow\ the\ solution\ Ax=b\ from\ \mathbf{\underline{two\ triangular\ systems}}.$

$\large If \normalsize \  the\ system\ Ax=b\ has\ an\ unique\ solution,\ then\ we\ say:$


$$
\Rightarrow LUx=b \ 
\left\{ 
    \begin{array}
        11.\ The\ system\ is\ nonsingular.\\
2.\ The\ matrix\ is\ nonsingular.\\
Otherwise, it\ is\ singular.
    \end{array}
\right.
$$

Last Chapter: [Matrix Notation and Matrix Multiplication](https://g0v.hackmd.io/ujx1rysxRyChze9DvkOprA?view)
Next Chapter: [Inverse and Transposes](https://g0v.hackmd.io/vurkAkSNSOCTq2HBEGW5vA?view)
