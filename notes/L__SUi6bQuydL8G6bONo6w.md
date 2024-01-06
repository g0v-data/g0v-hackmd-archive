# 數值線性代數HW1
```python=
import numpy as np    #only used to initialize the matrices and check the answer with dot function

# initialize matrix A
A = np.zeros([60,60])
for i in range(len(A)):
    for j in range(len(A[0])):
        if i > j:
            A[i][j] = -1
        elif i == j:
            A[i][j] = 1
        elif j == len(A[0]) - 1:
            A[i][j] = 1
print('A:')
print(A)

# initialize random vector b
B = np.random.randint(5, size=60)
print('B:')
print(B)

# LU decomposition
def LU(A):
    rows, columns = np.shape(A)
    L = np.identity(rows)
    U = A
    for k in range(columns-1):
        for j in range(k+1,rows):
            L[j][k] = U[j][k] / U[k][k]
            for i in range(k,columns):
                U[j][i] = U[j][i] - L[j][k] * U[k][i]    
    return L, U

# LU decomposition with partial pivoting
def PLU(A):
    rows, columns = np.shape(A)
    P = np.identity(rows)
    L = np.identity(rows)
    U = A
    for k in range(columns):
        max_id = k       # find the maximize absolute number in column k
        for j in range(k+1, rows):
            if abs(U[j][k]) > abs(U[max_id][max_id]):
                max_id = j
        # interchange two rows
        for i in range(columns):
            P[k][i], P[max_id][i] = P[max_id][i], P[k][i]
        for i in range(k, columns):
            U[k][i], U[max_id][i] = U[max_id][i], U[k][i]   
        for i in range(k-1):
            L[k][i], L[max_id][i] = L[max_id][i], L[k][i]
        # factorization
        for j in range(k+1, rows):
            L[j][k] = U[j][k] / U[k][k]
            for i in range(k,columns):
                U[j][i] = U[j][i] - L[j][k] * U[k][i]
    return P, L, U

# inverse of permutation matrix is the transpose if it
def p_inverse(P):
    rows, columns = np.shape(P)
    inv_P = P
    for i in range(rows):
        for j in range(i):
            inv_P[i][j], inv_P[j][i] = inv_P[j][i], inv_P[i][j]
    return inv_P


# solve Ly = b
def forward_sub(L, b):
    y = b
    for i in range(len(b)):
        for j in range(i):
            y[i] -= L[i][j] * y[j]
        y[i] /= L[i][i]
    return y

# solve Ux = y
def backward_sub(U, y):
    x = y
    for i in range(len(y)-1, -1, -1):
        for j in range(len(y)-1, i, -1):
            x[i] -= U[i][j] * x[j]
        x[i] /= U[i][i]
    return x

# pertubed the matrix(for 4_2)
u = np.ones([60, 1])
v = np.ones([1, 60])
m = u.dot(v)
A_m = A + m
print('modified of A:')
print(A_m)


P, L, U = PLU(A)    #or change to A_m
print('L:')
print(L)
print('U:')
print(U)
print('P:')
print(P)

# solve the x (would come out an error)
inv_P = p_inverse(P)
y = forward_sub(L, B)
x = backward_sub(U, y)
print('answer of x')
print(x)

# show that Growth factor is equal to 2^59
print('compare to growth factor:')
print(np.max(U)/1)
print(pow(2,59))

# show it got problem after PA =LU without pertubed
print('L*U:')
print(L.dot(U))
```


