# Chapter 2-2: The solution of m equations in n unknowns
$$For\ ax=b,\ \ a,b,x\in \mathbb{R}$$
- $if\ a \not=0 \rightarrow\ x=\frac b a,unique \ solution$
- $if\ a=0,b=0 \rightarrow\ \infty\ solution$
- $if\ a=0,b\not=0 \rightarrow\ \not\exists \ solution$
----
$$Ax=b,if\ A\ is\ square,\ then\ above\ may\ occur:$$
- $\exists A^{-1} \rightarrow x=A^{-1}b,unique\ solution.$
- $A\ is\ singular,\ \infty\ solution$
- $inconsistent\ case,\ \not\exists \ solution$
----
$$With\ a\ rectangular\ matrix\ A,\ x=A^{-1}b\ \mathbf{will\ NEVER\ happen!}$$
$1.\ There\ may\ be\ \infty\  solutions\ for\ some\ b\ ;$
$2. \infty\  solutions\ for\ some\ b\ and\ no\ solutions\ for\ others\ ;$
$3. one\ solution\ for\ some\ b\ and\ none\ for\ others.$

----
:pencil: $Definition-Row\ echelon\ matrix$
$$An\ m\times\ n\ matrix\ R\ is\ called\ a\ row\ echelon\ matrix\ if:$$

$1.\ The\ nonzero\ rows\ come\ first\ and\ the\ pivots\ are\ the\ first\ nonzero\ entries\ in\ those\ rows$
$2.\ Below\ each\ pivot\ is\ a\ column\ of\ zero.$
$3.\ Each\ pivot\ lies\ to\ the\ right\ of\ the\ pivot\ in\ the\ row\ above.$

----
:pencil: $Definition-Row\text-reduced\ echelon\ matrix$
$$An\ m\times\ n\ matrix\ R\ is\ called\ a\ row\text-reduced\ echelon\ matrix\ if:$$

$1.\ The\ nonzero\ rows\ come\ first\ and\ the\ pivots\ are\ the\ first\ nonzero\ entries\ in\ those\ rows\\ \mathbf{\ \ \ \ \ \ (Pivots\ are\ normalized\ to\ be\ 1)}$
$2.\ \mathbf{Above\ and\ below}\ each\ pivot\ is\ a\ column\ of\ zeros$
$3.\ Each\ pivot\ lies\ to\ the\ right\ of\ the\ pivot\ in\ the\ row\ above.$

---
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_40c4e4627e593734a8319ff8fa59ee37)

---
# Case 1. Homogeneous Case
$$i.e.\ Ax=0 \rightarrow\ Ux=0$$

$1^o$ We call the components of $x$, which correspond to columns with pivots the ++**basic varibles**++; otherwise, we call them ++**free varibles**++.

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c4fe0498520d8a6c5cde8472f0dd1ed8)

$2^o$ The basic varibles are then expressed in terms of free varibles by back substitution:
                                            
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7ecf1ccef433977c63ed1d6e27b60987)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fc22837537ded5609c9aaad829f3debe)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9e17c00b9d6a6f4a2ec2d63466e2dea4)


\begin{align*} 
&(1)\ After\ elimination\ reaches\ Ux=0,\ identify\ the\ basic\ and\ free\ varibles.\\
&(2)\ Set\ one\ free\ varible\ to\ be\ 1\ and\ the\ others\ to\ be\ 0,\ solve\ for\ Ux=0\ for\ the\ basic\ varibles\\
&(3)Every\ free\ varible\ produces\ its\ own\ solution\ by\ step(2),\\
&and\ the\ combinations\ of\ these\ solutions\ form\ the\ nullspace\ of\ A,\ \mathbb{N}(A)=\{x\in R^n\ |\ Ax=0\}
\end{align*}

:notebook: 
$If\ homogeneous\ system\ A_{m\times n}x=0\ has\ more\ unknowns,\ then\ equations(m<n),\ it\ has\ a\ nontrivial\ solution.$
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0a907700c241ae4b974e184480b971ca)

:notebook: $The\ nullspace\ is\ a\ subspace\ of\ the\ same\ "dimension"\ as\ the\ number\ of\ \mathbf{free}\ varibles.$

# Case 2. Inhomogeneous Case

$$Ax=b \rightarrow Ux=c\ \ where\ \ c=L^{-1}b$$

$\begin{bmatrix}
1 & 3 & 3 & 2\\ 
2 & 6 & 9 & 5\\ 
-1 & -3 & 3 & 0
\end{bmatrix}\begin{bmatrix}
u\\ 
v\\ 
w\\
y
\end{bmatrix}=\begin{bmatrix}
b_1\\ 
b_2\\ 
b_3
\end{bmatrix}$

$\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \Downarrow$

$\begin{bmatrix}
1 & 3 & 3 & 2\\ 
0 & 0 & 3 & 1\\ 
0 & 0 & 0 & 0
\end{bmatrix}\begin{bmatrix}
u\\ 
v\\ 
w\\
y
\end{bmatrix}=\begin{bmatrix}
b_1\\ 
b_2-2b_1\\ 
b_3-2b_2+5b_1
\end{bmatrix}$

----
We know that Ax=b can be solvable $\Rightarrow b\in \mathbb{C}(A)$

$\begin{bmatrix}1\\ 2\\ -1\end{bmatrix}\ \begin{bmatrix}3\\ 9\\ 3\end{bmatrix}\rightarrow1\&3:basic\ varible$

$\Rightarrow \mathbb{C}(A)=the\ set\ of\ combinations\ of\ \begin{bmatrix}1\\ 2\\ -1\end{bmatrix}\ \& \begin{bmatrix}3\\ 9\\ 3\end{bmatrix}$

$=\begin{Bmatrix}
\left.\begin{matrix}
\begin{bmatrix}
b_1\\ 
b_2\\ 
b_3
\end{bmatrix}
\end{matrix}\right|
5b_1-2b_2+b_3=0
\end{Bmatrix}_\perp \begin{bmatrix}
5\\ 
-2\\ 
1
\end{bmatrix}_{//}\begin{bmatrix}1\\ 2\\ -1\end{bmatrix}\times \begin{bmatrix}3\\ 9\\ 3\end{bmatrix}$

:pencil2: $Example$
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8f08bde1d034d4a1ed7a609ad09e2986)

$x_{general}=x_{particular}+x_{homogeneous}\ (x_g=x_p+x_h)$

Generally, the general solution files a two-dimensional surface (but **NOT** a subspace since it doesn't contain the **zero factor**) It is parallel to the nullspace of A.

---
$$//Steps\ to\ obtain\ the\ solution\ to\ Ax=b//$$
$(i)Reduce\ Ax=b\ \ to\ \ Ux=c\ \ to\ \  determine\ \mathbf{base/free\ varible}.$
$(ii)Set\ all\ free\ virables\ to\ zero,\ to\ find\ the\ \mathbf{particular\ solution}$
$(iii)Set\ RHS=0.\ Give\ each\ free\ varible\ 1,\ and\ the\ others\ 0\ in\ turn,\ find\ the\ \mathbf{homogeneous\ solution}$
$\Rightarrow x_g=x_p+x_n.$

---
# Rank

If there are **r** pivots,
there are ++**r**++ basic varibles and ++**n-r**++ free varibles.
The number of pivots, r, is called "the **rank** of the matrix"

Suppose elimination reduces $A_{m\times n}x=b$ to $Ux=c$ and there are r pivots and the last ++**m-r**++ rows of U are zero.

Then there is a solution only if the last ++**m-r**++ elements of c are zero.

- If r=m, there's always a solution:
  The general solution is the sum of particular solution and a homogeneous solution.
 - If r=n, there are ++**NO**++ free varible and the nullspace contains **++x=0 only++**. The number r is called the rank of A.

$\Rightarrow Two\ extreme\ case\ A_{m\times n}x=b$
$(i)\ if\ r=n \rightarrow\ No\ free\ varible\ \rightarrow \mathbb{N}(A)=\{x\in \mathbb{R}^n|Ax=0\}.$
$(ii)\ if\ r=m \rightarrow\ No\ zero\ rows\ in\ U\ \rightarrow \mathbb{C}(A)= \mathbb{R}^m \Rightarrow \exists\ solution\ for\ all\ b.$