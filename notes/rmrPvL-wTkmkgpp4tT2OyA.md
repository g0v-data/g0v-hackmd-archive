# Chapter 1-2: Geometry of Linear Equation
$$
\left\{ 
    \begin{array}
           22x - y = 1 \\
           x + y = 5
    \end{array}
\right.
$$



$(Approach.1)\ row\ picture:\ two\ lines\ in\ the\ plane$
$(Approach.2)\ column\ picture:\ to\ find\ the\ linear\ combination\ of \begin{bmatrix}2\\1\end{bmatrix}\ and \begin{bmatrix}-1\\1\end{bmatrix}\ to\\ form\ a\ column\ vector\ \begin{bmatrix}1\\5\end{bmatrix}$

---

$Note:\  A\ vector\ is\ an\ (n\times1)\ array\ with\ n\ real\ number.\\C_{us}^{'},\begin{bmatrix}c_1\\c_2\\...\\c_n\end{bmatrix},some\ write\ it\ as\ (c_1,c_2...c_n)\ in\ text.$ 
* $\alpha\begin{bmatrix}c_1\\...\\c_n\end{bmatrix}=\begin{bmatrix}\alpha c_1\\...\\\alpha c_n\end{bmatrix}\ ,\ \alpha\in\mathbb{R}$
* $\begin{bmatrix}c_1\\...\\c_n\end{bmatrix}+\begin{bmatrix}d_1\\...\\d_n\end{bmatrix}=\begin{bmatrix}c_1+d_1\\...\\c_n+d_n\end{bmatrix}$


$y\in\mathbb{R}\rightarrow\ \begin{bmatrix}y_1\end{bmatrix}$

$y\in\mathbb{R^2}\rightarrow\ \begin{bmatrix}y_1\\y_2\end{bmatrix}$

$y\in\mathbb{R^n}\rightarrow\ \begin{bmatrix}y_1\\y2\\...\\y_n\end{bmatrix}$

---
# Q:How to extend into n-dimension
\- Each equation represents a plane (with high dimension)
\- The first equation produces an $(n-1)$-dimension plane in $n$-dimension
\- The second equation produces another one. They intersectin a smaller set of $(n-2)$-dimension
$(n-3)\rightarrow(n-4)\rightarrow...\rightarrow 3\rightarrow2\rightarrow1\rightarrow point$

---
# singular case
$<Row\ Picture>$
$\ (1) ++\\
\ (2) \Delta\\
\ (3) *\\
\ (4) 川$

$<Column\ Picture>$
$The\ vector\ will\ be\ all\ on\ the\ same\ plane:$

$$
if\ the\ target\ is
\left\{ 
    \begin{array}
            oon\ the\ plane:\infty\ solution\\
            not\ on\ the\ plane:0\ solu    tion
    \end{array}
\right.
$$

# Foundational LA Theorem
$If\ n\ planes\ have\ no\ point\ in\ common,\ then\ the\ n\ columns\ lie\ in\ the\ same\ plane.\\(Consistent\ of\ row\ and\ column\ picture)$

Last Chapter: [Introduction](https://g0v.hackmd.io/07dhVXvGTDGG8tc-QWCr4g?view)
Next Chapter:[An Example of Gaussian Elimination](https://g0v.hackmd.io/j-fQTjzKTqSFKj_aHVknFQ?view)
