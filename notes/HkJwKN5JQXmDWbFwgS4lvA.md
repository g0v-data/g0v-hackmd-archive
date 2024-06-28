build pythonAI environment in CENTOS
1.conda create --name pythonAI python=3.8 # 創建python環境 會安裝相關套件
2.conda activate pythonAI  #激活新環境
3.conda install numpy pandas  #安裝所需的 Python 包
4.conda install scikit-learn #安裝 scikit-learn
5. which python
/usr/bin/python 當使用非ENV下的python會出現ImportError: No module named sklearn.datasets ==>/NasData01/yiling/anaconda3/envs/pythonAI/bin/python iris_class_test.py  #使用環境下的python就不會出錯




