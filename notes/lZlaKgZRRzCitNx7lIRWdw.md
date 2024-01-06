# 機器學習基石hw3
```python=
import requests
import torch
import random
import math

train_set = requests.get('https://www.csie.ntu.edu.tw/~htlin/course/ml20fall/hw3/hw3_train.dat')
test_set = requests.get('https://www.csie.ntu.edu.tw/~htlin/course/ml20fall/hw3/hw3_test.dat')

# data preprocessing
def dataloader(data_set, x0):
    data_set = data_set.text
    data_set = data_set.split('\n')
    del data_set[-1]
    nums = len(data_set)
    y_set = []
    for i in range(nums):
        data_set[i] = data_set[i].split('\t')
        data_set[i] = [float(x) for x in data_set[i]]
        label = data_set[i].pop()
        y_set.append(label)
        data_set[i].insert(0, x0)                           #insert x0
    data_set = torch.tensor(data_set)
    y_set = torch.tensor(y_set)
    return data_set, y_set

train_x, train_y = dataloader(train_set, 1)
test_x, test_y = dataloader(test_set, 1)

# Q14 linear regression
def linear_regression(x, y):
    # x_hat = torch.pinverse(x)        will get a different answer in Q20
    xt = torch.transpose(x, 0 ,1)
    xtx = xt @ x
    inv_xtx = torch.inverse(xtx)
    x_hat = inv_xtx @ xt
    w_lin = x_hat @ y
    return w_lin

def average_squared_error(y, labels):
    error = 0
    nums = len(y)
    for i in range(nums):
        error_i = (y[i] - labels[i])**2
        error += error_i
    return error/nums

w_lin = linear_regression(train_x, train_y)
y_lr = train_x @ w_lin
error_lr = average_squared_error(y_lr, train_y)
print('Answer for Q14:', error_lr)

# Q15 linear regression with stochastic gradient descent
def stochastic_gradient_descent_linear(x, y, learning_rate, error_lr):
    w_sgd = torch.zeros(len(x[0]))
    iter = 0
    while(1):
        iter += 1
        i = random.randint(0, len(x)-1)
        y_sgd = x @ w_sgd
        error_sgd = average_squared_error(y_sgd, y)
        if error_sgd <= error_lr * 1.01:
            break
        w_sgd += learning_rate * 2 * (y[i] - y_sgd[i]) * x[i]
    return iter, w_sgd

# run for a long time
iters = 0
for i in range(1000):
    iter, w_sgd = stochastic_gradient_descent_linear(train_x, train_y, 0.001, error_lr)
    print(iter)
    iters += iter
    print(iters/(i+1))
print('Answer for Q15:', iters/1000)

# Q16,Q17 logistic regression with stochastic gradient descent
def sigmoid(s):
    return 1 / (1 + math.exp(-s))

def cross_entropy_error(y, labels):
    error = 0
    nums = len(y)
    for i in range(nums):
        error_i = math.log(1+math.exp(-y[i] * labels[i]))
        error += error_i
    return error/nums

def stochastic_gradient_descent_logistic(x, y, learning_rate, w0 = None):
    if w0 != None:                       #for Q17
        w_sgd = w0
    else:                                #for Q16
        w_sgd = torch.zeros(len(x[0]))

    iter = 0
    for i in range(500):
        iter += 1
        i = random.randint(0, len(x)-1)
        y_sgd = x @ w_sgd
        theta = sigmoid(-(y[i] * y_sgd[i]))
        w_sgd += learning_rate * theta * y[i] * x[i]
    y_sgd = x @ w_sgd
    error_sgd = cross_entropy_error(y_sgd, y)
    return error_sgd

# Q16
errors_16 = 0
for i in range(1000):
    error_sgd_logistic = stochastic_gradient_descent_logistic(train_x, train_y, 0.001)
    errors_16 += error_sgd_logistic
print('Answer for Q16:', errors_16/1000)

# Q17
errors_17 = 0
for i in range(1000):
    error_sgd_logistic = stochastic_gradient_descent_logistic(train_x, train_y, 0.001, w0=w_lin)
    errors_17 += error_sgd_logistic
print('Answer for Q17:', errors_17/1000)

# Q18
def zero_one_error(y, labels):
    error = 0
    nums = len(y)
    for i in range(nums):
        if torch.sign(y[i]) != labels[i]:
            error += 1
    return error/nums

y_in = train_x @ w_lin
y_out = test_x @ w_lin
error_in = zero_one_error(y_in, train_y)
error_out = zero_one_error(y_out, test_y)
print('Answer for Q18:', abs(error_in - error_out))

# order-Q polynomial transform
def data_transforms(data, Q):
    data = data.clone().detach()
    scale = len(data[0])
    for i in range(2,Q+1):
        temp_data = data[:,1:scale]
        temp_data = temp_data**i
        data = torch.cat((data, temp_data), 1)
    return data

# Q19    order-3 polynomial transform
transform_train_x = data_transforms(train_x, 3)
transform_test_x = data_transforms(test_x, 3)

w_lin_transform = linear_regression(transform_train_x, train_y)
y_in_19 = transform_train_x @ w_lin_transform
y_out_19 = transform_test_x @ w_lin_transform
error_in_19 = zero_one_error(y_in_19, train_y)
error_out_19 = zero_one_error(y_out_19, test_y)
print('Answer for Q19:', abs(error_in_19 - error_out_19))

# Q20    order-10 polynomial transform
transform_train_x_20 = data_transforms(train_x, 10)
transform_test_x_20 = data_transforms(test_x, 10)

w_lin_transform_20 = linear_regression(transform_train_x_20, train_y)
y_in_20 = transform_train_x_20 @ w_lin_transform_20
y_out_20 = transform_test_x_20 @ w_lin_transform_20
error_in_20 = zero_one_error(y_in_20, train_y)
error_out_20 = zero_one_error(y_out_20, test_y)
print('Answer for Q20:', abs(error_in_20 - error_out_20))

```
