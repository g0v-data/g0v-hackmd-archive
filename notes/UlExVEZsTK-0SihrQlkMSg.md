# 機器學習基石hw2
```python=
import torch

# generate x
def x_set(n):
    x = (1- (-1)) * torch.rand(n) + -1
    x, _ = torch.sort(x)
    return x

# generate y
def y_set(x, tao):
    y = torch.sign(x)
    for yi in y:
        if torch.rand(1) <= tao:
            yi *= -1
    return y

# finding minimum Ein with decision stump
def ds(x, y):
    s_set = [-1, 1]
    min_e = 1
    min_s = -1
    min_theta = 0
    for s in s_set:
        for i in range(len(x)):
            if i+1 < len(x):
                theta = (x[i] + x[i+1]) / 2
            else:
                theta = -1
            e_in = E_in(x, y, s, theta)
            if e_in < min_e:
                min_e = e_in
                min_s = s
                min_theta = theta
    return min_e, min_s, min_theta 
                
# calculate E_in
def E_in(x, y, s, theta):
    error = 0
    for i in range(len(x)):
        if y[i] != s * torch.sign(x[i] - theta):
            error += 1
    return error/len(x)

# calculate E_out
def E_out(s, theta, tao):
    if s > 0:
        e_out = 0.5 * abs(theta)
    else:
        e_out = 0.5 * (2 - abs(theta))
    e_out = e_out * (1-2*tao) + tao
    return e_out

# setting the parameters for question 16~19
tao = 0.1         # 0.1
n = 2           # 20, 200

error = 0
for i in range(10000):
    x = x_set(n)
    y = y_set(x, tao)
    e_in, s, theta = ds(x, y)
    e_out = E_out(s,theta, tao)
    error += e_out - e_in
    if i % 1000 == 0:
        print(i)
mean_error = error/10000

print(mean_error)
```