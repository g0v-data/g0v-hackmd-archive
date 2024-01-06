image
import cv2
import numpy as np
import math
import os
import matplotlib.pyplot as plt
from scipy.interpolate import splprep, splev 

#針對單秒5張frame進行去噪,產出單張 Image 
s=(5,1920,1792)
image=np.zeros(s) #建立一個空矩陣，裡面都是0(後面要放img進矩陣中)
fullpath="image_start/image_5/56"  #輸入秒數
sec=56           #輸入秒數
ctr=0
for file in os.listdir(f'./{fullpath}'):
            
    img=cv2.imread(f'./{fullpath}/{file}')
    img = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)   #彩色轉灰階;層數較少

    image[ctr]+=img;     #存入大矩陣
    #print(img);
    ctr+=1;
gray = np.uint8(image);  #轉成0-255，整個矩陣
dst = cv2.fastNlMeansDenoisingMulti(gray, 2, 5, None, 4, 7, 35);  #去噪
plt.imshow(dst,'gray')
cv2.imwrite('./image_final/%d.jpg'%(sec),dst)
