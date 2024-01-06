# **影像處理**

General 3x3 mask 
w's are the kernel coefficients(weights)
R=w1z1+w2z2=...=

Special 1x1 mask
- T operates on only one ixel, i.e., s=T( r ) 
 // "s"means intensity of g, "r" means intensity of f
    -    Mapping, contrast stretching 
    -    Tresholding binarize//binary image
    





Function Style
intensity transformations 
sigmoid:1x1 mask s=T(r) 將偏高與偏低特別強化，保留中間數值不變。But因為偏高偏低都被凸顯變化 本來主要想研究的中間值 會被掩蓋住
參考L4p7右圖

basic intensity transformation function
- negative in[0,L-1]
s=T( r )=L-1-r
-
-
-
-


h=fspecial('average',mask_size)
imfilter(im, h, value//padding)