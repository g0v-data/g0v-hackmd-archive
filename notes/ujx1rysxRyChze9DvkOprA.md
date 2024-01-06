# Chapter 1-4: Matrix Notation and Matrix Multiplication

$An (\ m \times n)\ matrix,\ A_{m\times n}\ over  \ \mathbb{R}\ is\ an\ array\ with\ m\ rows\ and\ n\ columns\ of\ real\ number,\\ which\ can\ be\ rewritten\ as:$

$$
A=\begin{bmatrix}
a_{11} & a_{12} & ... & a_{1n}\\a_{21} & a_{22} & ... & a_{2n}\\ \vdots & \vdots & \ddots & \vdots\\a_{m1} & a_{m2} & ... & a_{mn}\\
\end{bmatrix}_{m \times n} , where \begin{cases} a_{ij} \in \mathbb{R}\\ i:\ index\ for\ row\\j:index\ for\ column \end{cases}
$$

- $m \times n\ is\ called\ the\ \mathbf{dimension(size)}\ of\ A$
- $a_{ij}\ is\ called\ the\ \mathbf{entry/element/coefficient}\ of\ A$

# Matrix Multiplication
$$
A_{n\times m}X_{m \times l} = B_{n \times l}\\
In \ particular,\ if\ A_{1\times n}B_{n\times 1}=\mathbb{V}\cdot\mathbb{W}  =  scalar\\
then\ it's\ called\ the\ inner\ produxt\ of
\ vector \mathbb{V}\  \&\  \mathbb{W}.\\
.\\
Example.\\
$$

$$
Ax=\begin{bmatrix}
2 & 4 & -2\\4 & 9 & -3\\-2 & 3 & 7\\
\end{bmatrix}
\begin{bmatrix}
-1\\2\\2\\
\end{bmatrix} = 
\begin{bmatrix}
2\\8\\22\\
\end{bmatrix}
$$

$$
1^o\ by\ row:3\ inner\ products.\\
2^oby\ column: a\ combination\ of\ 3\ columns\ of\ A.\\
i.e.\ 
(-1)\begin{bmatrix}2\\4\\-2\\\end{bmatrix}+2\begin{bmatrix}4\\9\\3\\\end{bmatrix}+2\begin{bmatrix}-2\\-3\\7\\\end{bmatrix}
$$

# Special Matrices
- $$
zero\ matrix: O = \begin{bmatrix}0 & 0 & ... & 0\\0 & 0 & ... & 0\\\cdots & \cdots & \ddots & \cdots\\0 & 0 & ... & 0\\\end{bmatrix}
$$

- $$
identity\ matrix: I = \begin{bmatrix}1 & 0 & ... & 0\\0 & 1 & ... & 0\\\cdots & \cdots & \ddots & \cdots\\0 & 0 & ... & 1\\\end{bmatrix}
$$

- $$
elementary\ matrix: E_{i,j} = \begin{bmatrix}1 & 0 & ... & 0\\0 & 1 & ... & 0\\\cdots & -l & \ddots & \cdots\\0 & 0 & ... & 1\\\end{bmatrix}
$$

$$
Elementary\ matrix,also\ known\ as\  \mathbf{elimination\ matrix},\\
\ can\ create\ 0\ at\ (i,j)\ \ if\ "l"\ is\ at\ (i,j)\ position\ of\ E.\\
.\\
Example.\\
\begin{bmatrix}1 & 0 & 0\\-2 & 1 & 0\\0 & 0&1\end{bmatrix} \begin{bmatrix}2 & 4 & -2\\4 & 9 & -3\\-2 & -3 & 7\end{bmatrix}=\begin{bmatrix}2 & 4 & -2\\0 & 1 & 1\\-2 & -3 & 7\end{bmatrix}
$$

$$
(1)The\ (i,j)^{th}\ entry\ of\ AB\ is\ the\ inner\ product\ of\ the\ i^{th}row\ of\ A\ and\ the\ j^{th}
column\ of\ B.\\
(2)Each\ column\ of\ AB\ is\ the\ product\ of\ a\ matrix\ A\ and \ a\ column\ of\ B \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ .\\
$$
\begin{align}
j^{th}\ column\ of\ AB\  & = A\times the\ j^{th}row \ of\ B  \\
& = l.combination\ of\ \mathbf{columns\ of\ A} \\
& =b_{1j}A._1+b_{2j}A._2+...+b_{nj}A._n\end{align}\
$$
(3)Each\ row\ of\ AB\ is\ the\ product\ of\ a\ row\ of\  A\ and\ a\ matrix\ B \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ .\\
$$
$$
\begin{align}
j^{th}\ row\ of\ AB\ & = the\ j^{th}row \ of\ A \times B\\
& = l.combination\ of\ \mathbf{rows\ of\ B} \\
& = a_{j1}B_{1.}+a_{j2}B_{2.}+...+a_{jn}B_{n.}\end{align}
$$

# Term
$$
\begin{cases} 
2u+4v-2w=2\\ 
4u+9v-3w=8\\ 
-2u-3v+7w=10\\ 
\end{cases} \Rightarrow
u\begin{bmatrix}
2\\4\\-2\\
\end{bmatrix}
+v\begin{bmatrix}
4\\9\\-3\\
\end{bmatrix}
+w\begin{bmatrix}
-2\\-3\\7\\
\end{bmatrix}
=\begin{bmatrix}
2\\8\\10\\
\end{bmatrix}\\
.\\
.\\
Ax=b\\
A=\begin{bmatrix}
2 & 4 & -2\\4 & 9 & -3\\-2 & -3 & 7\\
\end{bmatrix},x=
\begin{bmatrix}
u\\v\\w\\
\end{bmatrix},b=
\begin{bmatrix}
2\\8\\10\\
\end{bmatrix} \Rightarrow
x=
\begin{bmatrix}
-1\\2\\2\\
\end{bmatrix}\\
<coefficient\ matrix><unknown> <RHS> \Rightarrow<solution>
$$

# Theorem
$$
Let\ A.B.C\ be\ matrices\ (possibly\ rectangular).\\
Assume\ that\ their\ dimension\ permit\ them\ to\ be\ added\ and\ multiplied\ in\ the\ following\ theorem:
$$

$$
(1) The\ matrix\ multiplication\ is\ associative:\ (AB)C=A(BC)\\
(2) Matrix\ operations\ are\ distributive:\ A(B+C)=AB+AC\\
(3)Matrix\ multiplication\ is\ non-communative: AB \not=BA\ (in\ general)\\
(4)
AI=IA=A\\
(5)AO=OA=O\\
(6)The\ product\ of\ lower\ triangular\ matrices\ is\ a\ lower\ triangular\ matrix.
$$

Last Chapter: [Gaussian Elimination](https://g0v.hackmd.io/j-fQTjzKTqSFKj_aHVknFQ?view)
Next Chapter: [Triangular Factors and Row exchanges](https://g0v.hackmd.io/dxolp9bXRPy37Au0vgOyDw?view)
