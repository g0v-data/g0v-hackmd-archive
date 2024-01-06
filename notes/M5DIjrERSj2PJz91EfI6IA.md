# Chapter 2-1: Vector space and subspaces
To answer the basic questions about the "existence" and "uniqueness" of the solution of Ax=b, we need the concept of vector space.


# Field
:pencil: $Definition-Field$

Let F be a set with two operations "+" & "．"
$Closed:\left\{\begin{matrix}
+:F \times F \rightarrow F\\ 
\ \cdot\ :F \times F \rightarrow F
\end{matrix}\right.$
where $+$ and $\cdot$ are well-defined functions.

If the system (F,+,．) satisfies the following conditions,
then F is called a **Field**.

$Assume\ a,b,c \in F:$
$$\left\{\begin{matrix}
\begin{align*}
&1.\ (a+b)+c=a+(b+c)\\
&2.\ \ a+b = b+a\\
&3.\ \exists\ 0 \in F,\ s.t.\ a+0=0+a=a\\
&4.\ \forall a \in F, \exists-a\in F, s.t. a+(-a)=0\\
&5.\ (a\cdot b)\cdot c = a \cdot(b \cdot c)\\
&6.\ a \cdot b = b \cdot a\\
&7.\ \exists\ 1 \in F, s.t.\ a \cdot 1 = 1 \cdot a =a\\
&8.\ \forall a\not=0 \in F , \exists \ a^{-1} \in F,   \ s.t.\ \ a \cdot a^{-1}=a^{-1} \cdot a =1\\
&9.\ a\cdot(b+c)=ab+ac\\
\end{align*}
\end{matrix}\right.$$

$Literally\ is:$
$$
\left\{\begin{matrix}
\begin{align*}
&1.\ Addition\ Associative\\
&2.\ Addition\ Commutative\\
&3.\ Additive\ Identity\ exists\\
&4.\ Additive\ Inverse\ exists\\
&5.\ Multiplicative\ Associative\\
&6.\ Multiplicative\ Commutative\\
&7.\ Multiplicative\ Identity\ exist \\
&8.\ Multiplicative\ Inverse\ exists \\
&9.\ Distributive
\end{align*}
\end{matrix}\right.$$

:pencil2: $Example.$

$Yes:\mathbb{CRQ}\\  No:\mathbb{ZN}$

# Vector space
Let V be a set and F be a field.
V is a vector space over F if addition and multiplication by scalar are defined on V and they satisfy:
$$
vector\ addition
\left\{
\begin{matrix}
(A1)\ Addition\ is\ associative\\
(A2)\ Addition\ is\ commutative\\
(A3)\ \exists \ zero\ vector,\ s.t.\ 0+v=v,\ \forall v \in V\\
(A4)\ \forall v \in V, \exists-v \in V,\ s.t.(-v)+v=0
\end{matrix}\right.\\
scalar\ multiplication \left\{
\begin{matrix}
(M1)\ 1\cdot v=v\ (v \in V,1 \in F)\\
(M2)\ (\lambda \mu)\cdot v=\lambda (\mu \cdot v)\ (v \in V,\lambda , \mu \in F)\\
(M3)\ \lambda (v_1+v_2)=\lambda v_1+\lambda v_2\ (v_1,v_2 \in V,\lambda \in F)\\
(M4)\ (\lambda + \mu)v=\lambda v + \mu v\ (v \in V,\lambda , \mu \in F)\\
\end{matrix}\right.
$$

----
:pencil2: $Example.$
- $n \in N,\mathbb{R}^n\ is \ a\ vector\ space?\ \mathbf{Yes!}$
- $M_{2 \times 2}(\mathbb{R})=\begin{Bmatrix}
\begin{bmatrix}a & b\\ c& d\end{bmatrix}\left.\begin{matrix}&\\ &\end{matrix}\right|a,b,c,d\in \mathbb{R}\end{Bmatrix},M_{2 \times 2}(\mathbb{R})/\mathbb{R}\ \ a\ vector\ space?\ \mathbf{Yes!}$
- $V=\{all\ 3\times 3\ symmetric\ matrices\ over\ \mathbb{R}\},\ is\ V\ a\ vector\ space\ over\ \mathbb{R}?\ \mathbf{Yes!}$
---
:pencil:$Definition-Subspace$

A subspace W of a vector space over F is a nonempty subset of V, such that (W,+,‧) itself is a vector spcae over F.

W is a subspace of V over F if and only if W is closed under addition and scalar multiplication.

Q. Does the zero vector belong to subspace? **Yes!**

:heavy_exclamation_mark: $if\ W_1\ and\ W_2\ are\ subspaces\ of\ V\ and\ F,\ then\ W_1 \cap W_2 \not= \phi$
$\ \ \ \ \ \ \because \ W_1 \cap W_2\ contains\ at\ least\ the\ zero\ vector!$
:page_facing_up: $if\ W\ is\ a\ subspace\ of\ V/F,\ then\ we\ use\ the\ notation\ W \leq F$

Distinguish Standard: Closed + $\exists$ Zero

# Theorem
Let V be avector space over F
A nonempty subset W of V is a subspace of V
If and only if for each pair x,y $\in W$ and $\alpha \in F$ 
$1^o\ The\ zero\ vector \in W$
$2^o\ \alpha x +y \in W$

---
# Column space

The first concern is to find all attainable RHS vector b.

:pencil2:Example.

$\begin{bmatrix}1 & 4\\2 & 5\\3 & 6\\\end{bmatrix}\begin{bmatrix}u\\v\\\end{bmatrix}=\begin{bmatrix}b_1\\b_2\\b_3\end{bmatrix}\rightarrow\begin{bmatrix}b_1\\b_2\\b_3\end{bmatrix}=u\begin{bmatrix}1\\2\\3\end{bmatrix}+v\begin{bmatrix}4\\5\\6\end{bmatrix}$

The system Ax=b is solvable if and only if the vector b can expresses as a combination of the columns of A.

Let $\mathbb{C}(A)=\{all\ combinations\ of\ columns\ of\ A\}$
Then $\mathbb{C}(A)\ is\ a\ subspace\ of\ \mathbb{R}^m/\mathbb{R}$

----
:pencil: $Definition-Column\ Space$
$\mathbb{C}(A)$ is called the column space of A.
Thus if  $b \in \mathbb{C}$, then Ax=b is solvable.

- $A_{m \times \ n} = O \rightarrow \mathbb{C}(A)=O_{m \times 1}$
- $A_{m \times \ n} = I_m \rightarrow \mathbb{C}(A)=\mathbb{R}^m$


# Nullspace

:pencil: $Definition-Nullspace$
We are concerning not only which RHS b are attainable but also the set of solutions x that attain them.

If b=0, then x=0 is alwaysva solution but there may be $\infty$ other solutions.

$Let\ \mathbb{N}(A)=\{x \in \mathbb{R}\ |\ Ax=0\},then\ \mathbb{N}(A) \leq \mathbb{R}/\mathbb{R}$
$\mathbb{N}(A)\ is\ called\ the\ nullspace\ of\ A$

:paperclip: $Proof$
$x,x' \in \mathbb{N}(A)\ \Rightarrow Ax=0,\ Ax'=0$
$A(x+x')=Ax+Ax'=0+0=0 \Rightarrow\ x+x' \in \mathbb{N}(A)$

:notebook: $The\ system\ Ax=0\ is\ called\ a\ homogeneous\ equation.$

:heavy_exclamation_mark: $The\ solution\ set\ of\ Ax=b\ \ \mathbf{IS\ NOT}\ a\ subspace\ of\ \mathbb{R}^n/\mathbb{R}$
$\ \ \ \ \ \ \because x,x' \rightarrow\ Ax=b,\ Ax'=b$
$\ \ \ \ \ \     A(x+x')=Ax+Ax'=b+b=2b\mathbf{\not=b}$

:pencil2: $Example$

$\begin{bmatrix}1 & 4\\2 & 5\\3 & 6\\\end{bmatrix}\begin{bmatrix}u\\v\\\end{bmatrix}=\begin{bmatrix}0\\0\\0\\\end{bmatrix}\Rightarrow \mathbb{N}(A)=\begin{Bmatrix}
\begin{bmatrix}
0\\ 0\end{bmatrix}\end{Bmatrix}$

$\begin{bmatrix}1 & 4 & 5\\2 & 5 & 7\\3 & 6 & 9 \\\end{bmatrix}\begin{bmatrix}u\\v\\w\end{bmatrix}=\begin{bmatrix}0\\0\\0\\\end{bmatrix}\Rightarrow \mathbb{N}(A)=\begin{Bmatrix}
\begin{bmatrix}
t\\t\\-t\end{bmatrix},t \in \mathbb{R}\end{Bmatrix}$


# Summary
The vector $b \in \mathbb{R}^n$ are in the column space of A and the vectors $x \in \mathbb{R}^n\ s.t.\ Ax=0$ are in the nullspace of $A_{m\times n}(\mathbb{R})$

$1^o\ \mathbb{C}(A)=\{all\ combinations\ of\ columns\ of\ A\} \leq \mathbb{R}$
$2^o\ \mathbb{N}(A)=\{x\in \mathbb{R}^n|Ax=0\}$