# 數值線性代數3-3
```python=
import numpy as np
import matplotlib.pyplot as plt
import math

# initialize matrix A, b
def initialize(size):
    A = np.identity(size)
    for i in range(size):
        for j in range(i+1, size):
            el = np.random.uniform(-1, 1)
            A[i][j] = A[j][i] = el
    np.random.seed(10)
    b = np.random.uniform(-0.01, 0.01, (size,1))
    return A, b

#is psd
def is_pos_def(x):
    return np.all(np.linalg.eigvals(x) > 0)

# well-condition
def filter(A, tao):
    rows, columns = np.shape(A)
    A = np.copy(A)
    for i in range(rows):
        for j in range(i+1, columns):
            if abs(A[i][j]) > tao:
                A[i][j] = 0.0
                A[j][i] = 0.0
    return A

# error bound
def error_bound(k, iter, method):
    if method == 'cg':
        k_sqrt = math.sqrt(k)
        temp = (k_sqrt-1) / (k_sqrt+1)
        return 2*(temp**iter)
    elif method == 'gd':
        temp = (k-1) / (k+1)
        return temp**iter
    else:
        return 'no such method'

# A-norm
def norm_a(A, x):
    return ((np.transpose(x).dot(A).dot(x))**0.5)[0]

# CG iteration
def cg(A, b, iters = 20):
    rows, columns = np.shape(A)
    alpha = [0]*(iters+1)
    x = [0]*(iters+1)
    r = [0]*(iters+1)
    beta = [0]*(iters+1)
    p = [0]*(iters+1)
    x[0] = np.zeros((rows, 1))
    r[0] = np.copy(b)
    p[0] = np.copy(b)
    for i in range(1, iters+1):
        alpha[i] = r[i-1].T.dot(r[i-1]) / p[i-1].T.dot(A).dot(p[i-1])
        x[i] = x[i-1] + alpha[i] * p[i-1]
        # if (x[i] == x[i-1]).all():         #converge
        #     r[i] = r[i-1]
        # else:
        r[i] = r[i-1] - alpha[i] * A.dot(p[i-1])
        beta[i] = r[i].T.dot(r[i]) / r[i-1].T.dot(r[i-1])
        p[i] = r[i] + beta[i] * p[i-1]
    return x, r

# GD iteration
def gd(A, b, iters = 20):
    rows, columns = np.shape(A)
    alpha = [0]*(iters+1)
    x = [0]*(iters+1)
    r = [0]*(iters+1)
    x[0] = np.zeros((rows, 1))
    r[0] = np.copy(b)
    for i in range(1, iters+1):
        alpha[i] = r[i-1].T.dot(r[i-1]) / r[i-1].T.dot(A).dot(r[i-1])
        x[i] = x[i-1] + alpha[i] * r[i-1]
        r[i] = b - A.dot(x[i])
    return x, r

# PCG iteration
def pcg(A, b, iters = 20):
    rows, columns = np.shape(A)
    M = np.linalg.inv(np.diag(np.diagonal(A)))
    alpha = [0]*(iters+1)
    x = [0]*(iters+1)
    r = [0]*(iters+1)
    beta = [0]*(iters+1)
    p = [0]*(iters+1)
    z = [0]*(iters+1)
    x[0] = np.zeros((rows, 1))
    r[0] = np.copy(b)
    p[0] = M.dot(r[0])
    z[0] = np.copy(p[0])
    for i in range(1, iters+1):
        alpha[i] = r[i-1].T.dot(z[i-1]) / p[i-1].T.dot(A).dot(p[i-1])
        x[i] = x[i-1] + alpha[i] * p[i-1]
        # if (x[i] == x[i-1]).all():         #converge
        #     r[i] = r[i-1]
        # else:
        r[i] = r[i-1] - alpha[i] * A.dot(p[i-1])
        z[i] = M.dot(r[i])
        beta[i] = r[i].T.dot(r[i]) / r[i-1].T.dot(r[i-1])
        p[i] = r[i] + beta[i] * p[i-1]
    return x, r

# initialize parameters
it = 20
A, b = initialize(500)
tao = [0.01, 0.05, 0.1, 0.2]
iters = [i for i in range(it+1)]
k = []


# 3(a) plot the curve 
print('cg: 3(a)')
rn = [0]*(it+1)
for i in range(len(tao)):
    A_fil = filter(A, tao[i])
    true_x = np.linalg.inv(A_fil).dot(b)
    print('PSD:', is_pos_def(A_fil))
    np.linalg.cond(A_fil)
    print('condition number of tao = {tao}:'.format(tao=tao[i]), np.linalg.cond(A_fil))
    k.append(np.linalg.cond(A_fil))
    x ,r = cg(A_fil, b, it)
    error_bound_cg = []
    e_acc = []
    e_acc_0 = 1
    for j in range(it+1):
        e_acc.append(norm_a(A_fil, np.linalg.inv(A_fil).dot(r[j])))
        if j == 1:
            e_acc_0 = np.copy(e_acc[1])
        e_acc[j] /= e_acc_0
        error_bound_cg.append(error_bound(k[i], j, 'cg'))
        rn[j] = np.linalg.norm(r[j])
    plt.subplot(2,2,i+1)
    plt.ylim(10**-22, 10**4)
    plt.yscale('log')
    plt.plot(iters, rn, label='r norm of CG')
    plt.title("tao = {}".format(tao[i]), {'fontsize':8})
    plt.legend(loc='best')
plt.show()

# 3(b) plot the curve 
print('cg: 3(b)')
rn = [0]*(it+1)
for i in range(len(tao)):
    A_fil = filter(A, tao[i])
    true_x = np.linalg.inv(A_fil).dot(b)
    np.linalg.cond(A_fil)
    k.append(np.linalg.cond(A_fil))
    x ,r = cg(A_fil, b, it)
    error_bound_cg = []
    e_acc = []
    e_acc_0 = 1
    for j in range(it+1):
        e_acc.append(norm_a(A_fil, np.linalg.inv(A_fil).dot(r[j])))
        if j == 1:
            e_acc_0 = np.copy(e_acc[1])
        e_acc[j] /= e_acc_0
        error_bound_cg.append(error_bound(k[i], j, 'cg'))
        rn[j] = np.linalg.norm(r[j])
    plt.subplot(2,2,i+1)
    plt.ylim(10**-22, 10**4)
    plt.yscale('log')
    p1 = plt.plot(iters[1:], error_bound_cg[1:], 'r', label='RHS')     
    p1 = plt.plot(iters[1:], e_acc[1:], 'y', label='LHS')
    plt.title("tao = {}".format(tao[i]), {'fontsize':8})
    plt.legend(loc='best')

    # covergence rate
    en1 = (math.log(e_acc[20]) - math.log(e_acc[3])) / 18
    k1 = (math.log(error_bound_cg[20]) - math.log(error_bound_cg[3])) / 18
    print('convergence rate of en/e0', en1)
    print('convergence rate of k', k1)
    print('difference', en1 - k1)
plt.show()

# 3(c) plot the curve 
print('gd: 3(c)')
rn_c = [0]*(it+1)
for i in range(len(tao)):
    A_fil = filter(A, tao[i])
    true_x = np.linalg.inv(A_fil).dot(b)
    x ,r = gd(A_fil, b, it)
    error_bound_gd = []
    e_acc_c = []
    e_acc_c_0 = 1
    for j in range(it+1):
        e_acc_c.append(norm_a(A_fil, x[j] - true_x))
        if j == 0:
            e_acc_c_0 = np.copy(e_acc_c[0])
        e_acc_c[j] /= e_acc_c_0
        error_bound_gd.append(error_bound(k[i], j, 'gd'))
        rn_c[j] = np.linalg.norm(r[j])
    plt.subplot(2,2,i+1)
    plt.ylim(10**-22, 10**4)
    plt.yscale('log')
    p1 = plt.plot(iters, rn_c, label='r norm of GD')
    plt.title("tao = {}".format(tao[i]), {'fontsize':8})
    plt.legend(loc='best')
plt.show()

rn_c = [0]*(it+1)
for i in range(len(tao)):
    A_fil = filter(A, tao[i])
    true_x = np.linalg.inv(A_fil).dot(b)
    x ,r = gd(A_fil, b, it)
    error_bound_gd = []
    e_acc_c = []
    e_acc_c_0 = 1
    for j in range(it+1):
        e_acc_c.append(norm_a(A_fil, x[j] - true_x))
        if j == 0:
            e_acc_c_0 = np.copy(e_acc_c[0])
        e_acc_c[j] /= e_acc_c_0
        error_bound_gd.append(error_bound(k[i], j, 'gd'))
        rn_c[j] = np.linalg.norm(r[j])
    plt.subplot(2,2,i+1)
    plt.ylim(10**-22, 10**4)
    plt.yscale('log')
    plt.plot(iters, error_bound_gd, 'r', label='RHS')
    plt.plot(iters, e_acc_c, 'y', label='LFS')
    plt.title("tao = {}".format(tao[i]), {'fontsize':8})
    plt.legend(loc='best')

    # covergence rate
    en2 = (math.log(e_acc_c[20]) - math.log(e_acc_c[3])) / 18
    k2 = (math.log(error_bound_gd[20]) - math.log(error_bound_gd[3])) / 18
    print('convergence rate of en/e0', en2)
    print('convergence rate of k', k2)
    print('difference', en2 - k2)

plt.show()

# 3(d) plot the curve 
print('pcg: 3(d)')
rn_d = [0]*(it+1)
for i in range(len(tao)):
    A_fil = filter(A, tao[i])
    true_x = np.linalg.inv(A_fil).dot(b)
    x ,r = pcg(A_fil, b, it)
    for j in range(it+1):
        rn_d[j] = np.linalg.norm(r[j])
    plt.subplot(2,2,i+1)
    plt.ylim(10**-22, 10**4)
    plt.yscale('log')
    p1 = plt.plot(iters, rn_d, label='r norm of PCG')
    plt.title("tao = {}".format(tao[i]), {'fontsize':8})
    plt.legend(loc='best')

plt.show()
```