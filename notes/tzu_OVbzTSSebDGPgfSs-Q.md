# 機器學習技法hw6
```python=
import numpy as np
import requests
from collections import Counter

# data preprocessing
def dataloader(data_set):
    data_set = data_set.text
    data_set = data_set.split('\n')[:-1]
    nums = len(data_set)
    y_set = []
    for i in range(nums):
        data_set[i] = data_set[i].split('\t')
        data_set[i] = [float(x) for x in data_set[i][0].split(' ')]
        label = data_set[i].pop()
        y_set.append(label)
    return data_set, y_set


# decision stump
def ds(y_set, x_set, height):
    min_s, min_i, min_theta, min_e = -1, 0, 0, float("inf")
    min_negative_set, min_positive_set = [], []
    s_set = [1]
    i_set = len(x_set[0])       # dimension of x
    # print('level:', height, ' --->  train 2 *', i_set, '*', len(x_set)+1, 'combinations')
    for i in range(i_set):
        theta_set = [x[i] for x in x_set]
        theta_set.sort()
        theta_set.append(theta_set[-1] + 1)
        theta_set.insert(0, theta_set[0] -1)
        for j in range(len(theta_set) - 1):
            theta = (theta_set[j] + theta_set[j+1]) / 2
            for s in s_set:
                err, negative_set, positive_set = split(y_set, x_set, s, i, theta)   # split data and calculate impurity
                if err < min_e:
                    min_e = err
                    min_s = s
                    min_i = i
                    min_theta = theta
                    min_negative_set = negative_set    # (x_negative_set, y_negative_set)
                    min_positive_set = positive_set    # (x_positive_set, y_positive_set)
    return min_negative_set, min_positive_set, min_e, min_s, min_i, min_theta
                    

# split data and calculate impurity
def split(y_set, x_set, s, i, theta):
    x_negative_set = []      # h < 0
    x_positive_set = []      # h > 0
    y_negative_set = []
    y_positive_set = []
    for j in range(len(x_set)):
        h = s * np.sign(x_set[j][i] - theta)
        if h < 0:
            x_negative_set.append(x_set[j])
            y_negative_set.append(y_set[j])
        else:
            x_positive_set.append(x_set[j])
            y_positive_set.append(y_set[j])
    err = len(y_negative_set) * gini_index(y_negative_set) + len(y_positive_set) * gini_index(y_positive_set)
    return err, (x_negative_set, y_negative_set), (x_positive_set, y_positive_set)



# impurity function (only for binary classification)
def gini_index(y_set):
    N = len(y_set)
    if N == 0:
        return 0
    n_positive = y_set.count(-1)
    n_negative = y_set.count(1)
    return 1 - (n_positive/N)**2 - (n_negative/N)**2

# check terminate
def check_terminate(y_set, x_set):
    if len(y_set) <= 1:
        return True
    elif max(y_set) == min(y_set):
        return True
    elif max(x_set) == min(x_set):
        return True
    else:
        return False


# error function
def zero_one_err(pred_y, label):
    nums = len(label)
    err = 0
    for i in range(nums):
        if pred_y[i] != label[i]:
            err += 1
    return err/nums


class CartNode:
    def __init__(self, train_y, train_x, height):
        self.train_y = train_y
        self.train_x = train_x
        self.left = None
        self.right = None
        self.height = height

        # termination criteria
        if not check_terminate(self.train_x, self.train_y):  
            self.negative_set, self.positive_set, self.e, self.s, self.i, self.theta = ds(self.train_y, self.train_x, self.height)
            # print('left node data size:', len(self.negative_set[0]))
            # print('right node data size:', len(self.positive_set[0]))
            self.left = CartNode(self.negative_set[1], self.negative_set[0], self.height + 1)
            self.right = CartNode(self.positive_set[1], self.positive_set[0], self.height + 1)
            

    def predict(self, test_x):
        if self.left != None and self.right != None:
            h = self.s * np.sign(test_x[self.i] - self.theta)
            if h < 0:
                return self.left.predict(test_x)
            else:
                return self.right.predict(test_x)
        return Counter(self.train_y).most_common(1)[0][0]
        

train_set = requests.get('https://www.csie.ntu.edu.tw/~htlin/course/ml20fall/hw6/hw6_train.dat')
test_set = requests.get('https://www.csie.ntu.edu.tw/~htlin/course/ml20fall/hw6/hw6_test.dat')

train_x, train_y = dataloader(train_set)
test_x, test_y = dataloader(test_set)


# Q14
model = CartNode(train_y, train_x, 1)
pred_y = []
for i in range(len(test_x)):
    yi = model.predict(test_x[i])
    pred_y.append(yi)
print('Eout:', zero_one_err(pred_y, test_y))

# Q15、Q16、Q17、Q18
err_15 = 0
pred_16 = [0]*len(train_y)
pred_17 = [0]*len(test_y)
pred_18 = [0]*len(train_y)
for i in range(2000)):
    train_x_15 = []
    train_y_15 = []
    bag = []
    for j in range(len(train_x)//2):
        s = np.random.randint(len(train_x))
        train_x_15.append(train_x[s])
        train_y_15.append(train_y[s])
        bag.append(s)
    # train
    model = CartNode(train_y_15, train_x_15, 1)
    # Eout
    pred_y_15 = []
    for j in range(len(test_x)):
        yj = model.predict(test_x[j])
        pred_y_15.append(yj)
    pred_17 = np.add(pred_17, pred_y_15)
    err_15 += zero_one_err(pred_y_15, test_y)
    # Ein、Eoov
    pred_y_16 = []
    pred_y_18 = []
    for j in range(len(train_x)):
        yj = model.predict(train_x[j])
        pred_y_16.append(yj)
        if j not in bag:                        # out of bag
            pred_y_18.append(yj)
        else:
            pred_y_18.append(0)
    pred_16 = np.add(pred_16, pred_y_16)
    pred_18 = np.add(pred_18, pred_y_18)

print('Q15 Eout:', err_15/2000)
err_16 = zero_one_err(np.sign(pred_16), train_y)
print('Q16 Ein:', err_16)
err_17 = zero_one_err(np.sign(pred_17), test_y)
print('Q17 Eout:', err_17)          
pred_18 = [-1 if y == 0 else y for y in pred_18]
err_18 = zero_one_err(np.sign(pred_18), train_y)
print('Q18 Eoov:', err_18)      
    

