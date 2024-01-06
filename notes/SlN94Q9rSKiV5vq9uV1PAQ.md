# 數值線性代數HW2_5
```python=
import numpy as np
import random
import math

# f(x)
def func(x):
    return 1/(1+25*(x**2))

# modified gram-schmit
def mgs(A):
    rows, columns = np.shape(A)
    R = np.zeros([columns,columns])
    Q = A
    for i in range(columns):
        R[i][i] = np.linalg.norm(Q[:,i])
        Q[:,i] = Q[:,i] / R[i][i]
        for j in range(i+1, columns):
            R[i][j] = Q[:,i].dot(Q[:,j])
            Q[:,j] = Q[:,j] - R[i][j] * Q[:,i]
    return Q, R

# Givens rotation
def givens(A, row_i, row_j, column):
    rows, columns = np.shape(A)
    g = np.identity(rows)
    xi = A[row_i][column]
    xj = A[row_j][column]
    cos = xi / math.sqrt(xi**2 + xj**2)
    sin = -xj / math.sqrt(xi**2 + xj**2)
    g[row_i][row_i] = cos
    g[row_j][row_j] = cos
    g[row_i][row_j] = -sin
    g[row_j][row_i] = sin
    return g.dot(A)

m = 50
n = 12
# generate 50 points
p = np.arange(-1, 1, 2/m)

#generater A matrix
A = np.zeros([m,n])
for i in range(m):
    A[i][0] = 1
    A[i][1] = p[i]
    for j in range(2, n):
        A[i][j] = A[i][j-1] * A[i][1]

# generate B matrix
B = p.copy()
for i in range(len(B)):
    B[i] = func(B[i])

# computing x with normal equation 5(a)
At = A.transpose()
AtA = At.dot(A)
inv_AtA = np.linalg.inv(AtA)
pseudo_inv = inv_AtA.dot(At)
x_ne = pseudo_inv.dot(B)
print('5(a)')
print(x_ne)
print('---------------------------------------')

#computing x with QR factorization   5(b)
Q, R = mgs(A.copy())
inv_R = np.linalg.inv(R)
Qt = Q.transpose()
x_qr = (inv_R.dot(Qt)).dot(B)
print('5(b)')
print(x_qr)
print('--------------------------------------')

# insert column to A (n=13)   5(c)
A_insert = np.zeros([m,n+1])
A_insert[:,:-1] = A
A_insert[:,-1] = A_insert[:,1] * A_insert[:,-2]

# deal with R after insert column
R_insert = np.zeros((50,13))
R_insert[:12,:12] = R
R_insert[:,-1] = A_insert[:,-1]
for i in range(12, 50):
    R_insert = givens(R_insert, 11, i, 12)

inv_R_insert = np.linalg.inv(R_insert[:13,])
Q_insert = A_insert.dot(np.linalg.inv(inv_R_insert))
Q_insert_t = Q_insert.transpose()
x_modified_qr = (inv_R_insert.dot(Q_insert_t)).dot(B)
print('5(c):')
print(x_modified_qr)
