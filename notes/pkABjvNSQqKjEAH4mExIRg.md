import sys
brithday = input()
date = brithday.split()
M = int(date[0])
D = int(date[1])
S = ( M * 2 + D ) % 3
if S == 0:
    print("普通")
elif S == 1:
    print("吉")
elif S == 2:
    print("大吉")

