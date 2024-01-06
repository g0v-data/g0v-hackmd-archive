# 機器學習基石hw5
```python=
import requests
import numpy as np
from svmutil import *

train_y, train_x = svm_read_problem('satimage.scale.txt')
test_y, test_x = svm_read_problem('satimage.scale.t.txt')

# transform the label into binary classification
def label_transform(train_y, target_label):
    y = train_y.copy()
    for i in range(len(y)):
        if y[i] == float(target_label):
            y[i] = 1
        else:
            y[i] = -1
    return y

def w_counting(y, sv_coef, SV, x_dim):
    print('w counting...')
    assert len(sv_coef) == len(SV)
    w = np.zeros(x_dim)
    for i in range(len(sv_coef)):
        x = np.array([SV[i].get(j, 0) for j in range(1, x_dim+1)])
        w += sv_coef[i][0] * x
    return w

# E with 0/1 error
def error(y, label):
    nums = len(y)
    error = 0
    for i in range(nums):
        if y[i] != label[i]:
            error += 1
    return error/nums

# transform the label
train_y_trans = []
test_y_trans = []
for i in range(1, 7):
    train_y_trans.append(label_transform(train_y, i))
    test_y_trans.append(label_transform(test_y, i))

# Q15
m = svm_train(train_y_trans[2], train_x, '-s 0 -c 10 -t 0')
w = w_counting(train_y_trans[2], m.get_sv_coef(), m.get_SV(), 36)
print(np.linalg.norm(w))

# Q16, Q17
e_in_16 = []
nr_sv_17 = []
for i in range(5):
    m_16 = svm_train(train_y_trans[i], train_x, '-s 0 -c 10 -t 1 -d 2 -g 1 -r 1')
    p_label, p_acc, p_val = svm_predict(train_y_trans[i], train_x, m_16)
    e_in_16.append(1-(p_acc[0]/100))
    nr_sv_17.append(m_16.get_nr_sv())
print(e_in_16)
print(nr_sv_17)

# Q18
C = [0.01, 0.1, 1, 10 ,100]
e_out_18 = []
for c in C:
    print(c)
    m_18 = svm_train(train_y_trans[5], train_x, '-s 0 -t 2 -g 10 -c {c}'.format(c = c))
    p_label_18, p_acc_18, p_val_18 = svm_predict(test_y_trans[5], test_x, m_18)
    e_out_18.append(1-(p_acc_18[0]/100))
print(e_out_18)

# Q19
gamma = [0.1, 1, 10 , 100, 1000]
e_out_19 = []
for g in gamma:
    m_19 = svm_train(train_y_trans[5], train_x, '-s 0 -t 2 -g {gamma} -c 0.1'.format(gamma = g))
    p_label_19, p_acc_19, p_val_19 = svm_predict(test_y_trans[5], test_x, m_19)
    e_out_19.append(1-(p_acc_19[0]/100))
print(e_out_19)

# Q20
gamma = [0.1, 1, 10 , 100, 1000]
n = len(train_x)
vote = {0.1:0, 1:0, 10:0, 100:0, 1000:0}
for i in range(1000):
    print('----------------------------------------')
    print(i)
    rand = np.random.choice(n, 200, replace = False)
    rand = np.sort(rand)
    val_x_20 = [train_x[i] for i in rand]
    val_y_20 = [train_y_trans[5][i] for i in rand]
    train_x_20 = [train_x[i] for i in range(n) if i not in rand]
    train_y_20 = [train_y_trans[5][i] for i in range(n) if i not in rand]
    smallest_g = 0
    smallest_e_val = 1
    for g in gamma:
        m_20 = svm_train(train_y_20, train_x_20, '-s 0 -t 2 -g {gamma} -c 0.1'.format(gamma = g))
        p_label_20, p_acc_20, p_val_20 = svm_predict(val_y_20, val_x_20, m_20)
        e_val_20 = 1-(p_acc_20[0]/100)
        if e_val_20 < smallest_e_val:
            smallest_e_val = e_val_20
            smallest_g = g
    vote[smallest_g] += 1
    print(vote)

print(vote)