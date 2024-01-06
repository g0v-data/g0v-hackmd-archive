# 數值線性代數HW2_4
```python=
import numpy as np

A = np.array([[1.0,2.0,3.0],
              [4.0,5.0,6.0],
              [7.0,8.0,7.0],
              [4.0,2.0,3.0],
              [4.0,2.0,2.0]])

# classical gram-schmit
def cgs(A):
    rows, columns = np.shape(A)
    R = np.zeros([columns,columns])
    Q = A
    for j in range(columns):
        for i in range(j):
            R[i][j] = Q[:,i].dot(Q[:,j])
            Q[:,j] = Q[:,j] - R[i][j] * Q[:,i]
        R[j][j] = np.linalg.norm(Q[:,j])
        Q[:,j] = Q[:,j] / R[j][j]
    print('Q:',Q)
    print('R:',R)
    print(Q.dot(R))
    return Q, R


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
    print('Q:',Q)
    print('R:',R)
    print(Q.dot(R))
    return Q, R

# Householder
def householder(A):
    rows, columns = np.shape(A)
    R = np.copy(A)
    for k in range(columns):
        a = R[k:,k]
        e = np.zeros([rows-k])
        v = np.zeros([rows-k])
        e[0] = 1
        norm = np.linalg.norm(a)
        v = sign(a[0]) * norm * e + a
        v = v / np.linalg.norm(v)
        # print('v',k,v)
        p = v.dot(R[k:,k:])
        R[k:,k:] = R[k:,k:] - 2*np.outer(v,p)
        # print('R',k,R)
    inv_R = np.linalg.inv(R[:3,:3])
    Q = A.dot(inv_R)
    print('Q:',Q)
    print('R:',R)
    return Q, R


def sign(x):
    if x >= 0:
        return 1
    else:
        return -1

print('CGS:')
cgs(A.copy())
print('MGS:')
mgs(A.copy())
print('Householder:')
householder(A.copy())


