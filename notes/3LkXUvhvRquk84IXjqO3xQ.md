# 配合款查詢

從 github 上面把檔案 clone 下來

```
git clone https://github.com/eopXD/twcouncil_fund_analytic
```

電腦需要安裝 python3

安裝 python3 :

- [Mac](https://pythonguidecn.readthedocs.io/zh/latest/starting/install3/osx.html)
- [Windows](https://pythonguidecn.readthedocs.io/zh/latest/starting/install3/win.html)



```
python3 twcouncil_fund_analytic/src/query-accountmapping.py
```

四種操作：

- list：列出所有的物件
- list [NAME]：列出特定物件及其成份
- top [NUMBER]：列出金額排名前幾的物件
- compare [NAMEA] [NAMEB] [NAMEC] ...：比較物件之間的成分

範例：

```
#########################################################################
#               Welcome to the query of accountmapping                  #
#                                                                       #
# Specify a county and a year, then you can list out top ranks of       #
# councilor/company and its specifics. Type "-1" to return to  parent   #
# layer.                                                                #
#                                                                       #
# Hierarchy: county >> year >> councilor/company                        #
#########################################################################
County available 臺北市 新北市 桃園市 臺中市 高雄市 ('-1' to end program)
Select a county : 臺北市
You have selected county: "臺北市"
Select a year(2011~2017), '-1' to go back to parent section : 2017
You have selected county "臺北市" and year: "2017"
Select "councilor" or "company", '-1' to go back to parent section : company
98 company is read
Operations:
$ list: list all company
$ list [name]: list component of [name]
$ top [n]: top [n] company with most money
$ compare [two or more names seperated with " "]: list out repeating component among the names
$ -1: back to parent section
$ top 5
台球營造 : 234242000
樹盛營造 : 57778429
福固營造 : 41947140
冠筑營造 : 39068000
福呈營造 : 37677000
```