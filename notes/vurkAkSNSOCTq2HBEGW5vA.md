# Chapter 1-6: Inverse and Transposes
:pencil: $Definition-Invertable$
$$An\ n \times n\ matrix\ A\ is\ "invertible"\\if\ \exists\ an\ n\times n\ matrix\ B\ \ \ \ s.t.BA=I=AB$$

---
:paperclip: $Proof:$
$If\ A\ is\ invertable\ ,then\ the\ matrix\ B\ satisfying\ AB=BA=I\ is\ \underline{unique}!$
$$
Suppose\ \exists\ C\not=B,\ s.t.AC=CA=I\\
B=BI=B(AC)=(BA)C=IC=C\ \Rightarrow\Leftarrow\\
$$

----
:notebook: $\Large{Note.1}$
if $Ax=O$ has nonzero solution(has zero divisor), then A  has  no  inverse.

:notebook: $Note.2$
$\ \ \ \ \ \ \ The\ inverse\ of\ A^{-1}\ is\ A\ itself.\ i.e.(A^{-1})^{-1}=A$

:notebook:  $Note.3$
$\ \ \ \ \ \ \ The\ inverse\ of\ A=[a]\ is\ A^{-1}=[\frac{1}{a}]\ (if\ a\not=0)$
$\ \ \ \ \ \ \ The\ inverse\ of\ A= \begin{bmatrix} a & b\\ c & d\\ \end{bmatrix}
\ is\ A^{-1}= \frac{1}{ad-bc}  \begin{bmatrix}
    d & -b\\-c & a\\
\end{bmatrix}(if\ (ad-bc)\not=0)$

:notebook: $Note.4$
$A=\begin{bmatrix}d_1 & ... & 0\\\vdots & \ddots & \vdots\\0 & ... & d_n\\\end{bmatrix} \&\ d_i\not=0,\ \forall i\Rightarrow A^{-1}=\begin{bmatrix}d_1^{-1} & ... & 0\\\vdots & \ddots & \vdots\\0 & ... & d_n^{-1}\\\end{bmatrix}$
:notebook: $Note.5$
$\ \ \ \ \ \ \ (AB)^{-1}=B^{-1}A^{-1}$

# Intro before Gauss-Jorden Method

$Define\ e_i=\begin{bmatrix}0\\\vdots\\0\\1\\0\\\vdots\\0\\\end{bmatrix}_{n\times 1} \leftarrow i^{th}$

$A[B_1|B_2|...|B_n]=[e_1|e_2|...|e_n] \Rightarrow AB_i=e_i \Rightarrow \mathbf{n\ linear\ systems(Ax=b)}$
$\Rightarrow Gauss-Jorden\ Method$

# Gauss-Jorden Method
Instead of stoping at U and switching to back-substitution, it continues by subtesting multiples of a row from the rows above till it reaches a diageral matrix, then we divide each row by the corresponding pivot.

$A=LU \Rightarrow A^{-1}=U^{-1}L^{-1}$
$[A|I] \xrightarrow{\text{x L^-1}}[U|L^{-1}] \xrightarrow{\text{xU^-1}}[I|A^{-1}]$

:pencil2:$Example.$

$Step.1\ :[\ A\ |\ I\ ]$
$$
\begin{bmatrix}
2 & -1 & 0 & | &1 & 0 & 0\\
-1 & 2 & -1 & | & 0 & 1 & 0\\
0 & -1 & 2 & | & 0 & 0 &1\\
\end{bmatrix}
$$


$Step.2\ :[\ U\ |\ L^{-1}\ ]$
$$
\begin{bmatrix}
2^* & -1 & 0 & | &1 & 0 & 0\\
0^* & \frac{3}{2}^* & -1 & | & \frac{1}{2} & 1 & 0\\
0^* & 0^* & \frac43^* & | & \frac{1}{3} & \frac{2}{3} &1\\
\end{bmatrix}
$$

$Step.3$
$$
\begin{bmatrix}
2 & 0^* & 0^* & | &\frac32 & 1 & \frac12\\
0 & \frac{3}{2} & 0^* & | & \frac34 & \frac32 & \frac34\\
0 & 0 & \frac43 & | & \frac13 & \frac23 &1\\
\end{bmatrix}
$$


$Step.4\ :[\ I\ |\ A^{-1}\ ]$
$$
\begin{bmatrix}
1 & 0 & 0 & | &\frac34 & \frac12 & \frac14\\
0 & 1 & 0 & | & \frac12 & 1 & \frac12\\
0 & 0 & 1 & | & \frac14 & \frac12 &\frac34\\
\end{bmatrix}
$$

:question: Question: Invertible = Nonsingular
$Q:What\ kind\ of\ matrices\ are\ invertible\ ?$
$A:1^o\ inpendent\ columns\ or\ rows$
$\ \ \ \ \ \ 2^o\ nonzero\ determinants$
$\ \ \ \ \ \ 3^o\ nonzero\ eigenvalues$
$\ \ \ \ \ \ 4^o\ nonzero\ pivots$

----

Suppose a matrix A has a full set of nonzero pivots.
By definition, A is nonsingular and the n systems $Ax_1=e_1, Ax_2=e_2,...,Ax_n=e_n$
can be solved by elimination or Gauss-Jorden Method.
=>Row exchange may be  necessary, but the column of $A^{-1}$ are uniquely determined.
Ax=b $\Rightarrow$ $$PAx=Pb\\PAx_i=Pe_i$$
${Pe_1,Pe_2,...,Pe_n}={e_1,e_2,...,e_n}$
- compute $A^{-1}$
$1^o\ A[x_1|...|x_n]\ =\ I\ [e_1|...|e_n] \Leftarrow \Rightarrow\ Ax_i=e_i,i=1,2,.....n$
$2^o\ GJM:\ [A|I] \rightarrow [I|A^{-1}]$

:question: $Question$
We have found a matrix $A^{-1}$, s.t $AA^{-1}=I$. But is $AA^{-1}=I$. But is $A^{-1}A=I$ ?
Recall that every GJM step is a multiplication of matrices on the left. There are 3 type of  matrices:

$1^o E_{ij}(l):to\ substract\ a\ multiple l\ of\ row\ j\ from\ row\ i.$
$2^o P_{ij}: to\ exchange\ row\ i\ and\ row\ j$
$3^o D: to\ multiply\ row\ i\ by\ d. i.e.$
$$\begin{bmatrix}
1 &  &  & &  &  & 0\\
& \ddots & &  &  &  & \\
&  & 1 &  &  & & \\
&  &  & d &  & \\
&  &  & & 1 &  & \\
&  &  &  & & \ddots & \\
0 &  &  &  & &  & 1\\
\end{bmatrix}
$$

# Theorem
1. Every nonsingular matrix is invertible.
2. Every invertible matrix is nonsingular.


# Transpose $A^T$
$(A+B)^T=A^T+B^T$
$(A^T)^T=A$
$(AB)^T=B^TA^T$
$(A^{-1})^T=(A^T)^{-1}$

---
:pencil:$Definition-Symmetric$
A symmetric is a matrix which equals its own transpose.
i.e. $A=A^T$
$$
\begin{bmatrix}3 & 1\\1 & 2\\\end{bmatrix}_{(V)}
\begin{bmatrix}5 & 4\\1 & 5\\\end{bmatrix}_{(X)}
\begin{bmatrix}0 & 0\\0 & 0\\\end{bmatrix}_{(V)}
$$

:notebook:  $Note:$
A symmetric matrix **is NOT necessarily** invertible!
If it is invertible, then its inverse is symmetric.

----

> $If\ A\ is\ symmetric\ and\ if\ A\ can\ be\ factored\ as\ LDU,\\ then\ \mathbf{A=LDL^T}.$


:paperclip: $Proof$
$$
A=A^T,A=LDU
A^T=(LDU)^T=U^TD^TL^T=U^TDL^T=A=LDU\\
\because A=LDU\ form\ is\ unique \rightarrow U^T=L\ \&\ L^T=U
$$




Last Chapter: [Triangular Factors and Row exchanges](https://g0v.hackmd.io/dxolp9bXRPy37Au0vgOyDw?view)


