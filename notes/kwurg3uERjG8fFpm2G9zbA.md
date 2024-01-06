# 機器學習基石hw4
```python=
import requests
from liblinearutil import *

train_set = requests.get('https://www.csie.ntu.edu.tw/~htlin/course/ml20fall/hw4/hw4_train.dat')
test_set = requests.get('https://www.csie.ntu.edu.tw/~htlin/course/ml20fall/hw4/hw4_test.dat')

# data preprocessing
def dataloader(data_set, x0):
    data_set = data_set.text
    data_set = data_set.split('\n')[:-1]
    nums = len(data_set)
    y_set = []
    for i in range(nums):
        data_set[i] = data_set[i].split()
        data_set[i] = [float(x) for x in data_set[i]]
        label = data_set[i].pop()
        y_set.append(label)
        data_set[i].insert(0, x0)                           #insert x0
        data_set[i] = data_transforms(data_set[i])
        data_set[i] = list_to_dict(data_set[i])
    return data_set, y_set

# order-Q polynomial transform
def data_transforms(data):
    scale = len(data)
    for i in range(1, scale):
        for j in range(i, scale):
            xi_xj = data[i] * data[j]
            data.append(xi_xj)
    return data

# transform data format for liblinear
def list_to_dict(data):
    data_dict = {}
    for i in range(len(data)):
        data_dict[i+1] = data[i]
    return data_dict 

x, y = dataloader(train_set, 1)
x_test, y_test = dataloader(test_set, 1)
lambdas = [-4, -2, 0, 2, 4]

#Q16、Q17
max_accueacy_16 = 0
emin_lambda_16 = 0
max_accueacy_17 = 0
emin_lambda_17 = 0
for i in range(len(lambdas)):
    m = train(y, x, '-s 0 -c {el} -e 0.000001'.format(el=2/pow(10, lambdas[i])))
    p_label_16, p_acc_16, p_val_16 = predict(y_test, x_test, m)
    p_label_17, p_acc_17, p_val_17 = predict(y, x, m)
    if p_acc_16[0] > max_accueacy_16:
        max_accueacy_16 = p_acc_16[0]
        emin_lambda_16 = lambdas[i]
    if p_acc_17[0] > max_accueacy_17:
        max_accueacy_17 = p_acc_17[0]
        emin_lambda_17 = lambdas[i]
print('Q16:', emin_lambda_16, max_accueacy_16)
print('Q17:', emin_lambda_17, max_accueacy_17)
    
#Q18
x_train = x[:120]
y_train = y[:120]
x_val = x[120:]
y_val = y[120:]
max_accueacy_18 = 0
emin_lambda_18 = 0
m_18_best = 0
for i in range(len(lambdas)):
    m18 = train(y_train, x_train, '-s 0 -c {el} -e 0.000001'.format(el=2/pow(10, lambdas[i])))
    p_label_18, p_acc_18, p_val_18 = predict(y_val, x_val, m18)
    if p_acc_18[0] > max_accueacy_18:
        max_accueacy_18 = p_acc_18[0]
        emin_lambda_18 = lambdas[i]
        m_18_best = m18
p_label_18out, p_acc_18out, p_val_18out = predict(y_test, x_test, m_18_best)
print('Q18:', 1-(p_acc_18out[0]/100), emin_lambda_18)

#Q19
m19 = train(y, x, '-s 0 -c {el} -e 0.000001'.format(el=2/pow(10, emin_lambda_18)))
p_label_19, p_acc_19, p_val_19 = predict(y_test, x_test, m19)
print('Q19:', 1-(p_acc_19[0]/100))

#20
eval_set = []
for i in range(len(lambdas)):
    e_val = 0
    for j in range(5):
        x_train_20 = x[:j*40]
        y_train_20 = y[:j*40]
        x_train_20.extend(x[j*40+40:])
        y_train_20.extend(y[j*40+40:])
        x_val_20 = x[j*40:j*40+40]
        y_val_20 = y[j*40:j*40+40]
        m20 = train(y_train_20, x_train_20, '-s 0 -c {el} -e 0.000001'.format(el=2/pow(10, lambdas[i])))
        p_label_20, p_acc_20, p_val_20 = predict(y_val_20, x_val_20, m20)
        e_val += 1 - p_acc_20[0]/100
    e_val /= 5
    eval_set.append(e_val)
print('Q20:', min(eval_set))
        

print('-----------------------------------------------------------------')
print('Q16:', emin_lambda_16, max_accueacy_16)
print('Q17:', emin_lambda_17, max_accueacy_17)
print('Q18:', 1-(p_acc_18out[0]/100), emin_lambda_18)
print('Q19:', 1-(p_acc_19[0]/100))
print('Q20:', min(eval_set))
```