對題數 = input("答對題數為:")
right= int(對題數)
得分 = 0
if 0<right <=10:
  得分=得分+right*6
elif 10<right<=20:
  得分=得分+right*2
elif 20<right<=40:
  得分=得分+right
elif right>40:
  得分=100
print(得分)