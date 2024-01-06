# 數值線性代數HW2_6
```python=
import numpy as np
import scipy.io
import matplotlib.pyplot as plt

# get data from .mat
mat = scipy.io.loadmat('ECGData.mat')
ecg = mat['ECGData']
y = ecg[0][0][0]        # got the 162*65536 matrix
label = ecg[0][0][1]    # got the 162*1 matrix
rows, columns = np.shape(y)

# create matrix D
D = np.identity(rows)
for i in range(rows):
    if i+1 < rows:
        D[i][i+1] = -2
    if i+2 < rows:
        D[i][i+2] = 1

# create first-order matrix D
D1 = np.identity(rows) * -1
for i in range(rows):
    if i+1 < rows:
        D1[i][i+1] = 1

# transpose function
def trans(A):
    rows, columns = np.shape(A)
    A = np.copy(A)
    if rows == columns:
        for i in range(rows):
            for j in range(i+1, columns):
                A[i][j], A[j][i] = A[j][i], A[i][j]
        return A
    else:
        return -1

# formula on the sheet
def func(lamb, D, y):
    Dt = trans(D)
    DD = Dt.dot(D)
    func = np.identity(len(DD)) + lamb * DD
    inv_func = np.linalg.inv(func)
    x = inv_func.dot(y)
    return x

# plot
t = [i/128 for i in range(columns)]
for i in range(1, 9):
    lamb = (i-4)
    x = func(10**lamb, D1, y)
    plt.subplot(2,4,i)
    for i in range(len(x)):
        p1 = plt.plot(t,x[i])
        plt.ylim(-7, 7)
    plt.title("lambda = {}".format(10**lamb), {'fontsize':5})

plt.show()




