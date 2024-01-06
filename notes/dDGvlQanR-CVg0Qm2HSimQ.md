---
title: "♎ 立委咖電喂(Call-LiWei) Database Schema"
tags: 立委咖電喂 (call-liwei),hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/dlLHqYSPtwu)


## Revision:


| **Version** | **Date** | **Author** | **Change Log** |
| --- | --- | --- | --- |
| 0.1.0 | 2016/04/21 | Hong | 1\. Add table Legislators |
|  |  |  | 2\. Add table Districts |
|  |  |  | 3\. Add table Parties |
|  | 2016/04/24 | Hong | 1\. Add Relational Diagram |
|  | 2016/05/09 | Hong | 1\. Add table serving_offices |
|  |  |  | 2\. Add columns of legislators table: experience, facebook, wiki, line |
|  |  |  | 3\. Modify the naming convention |
|  | 2016/05/10 | Hong | 1\. Add table commitees |
|  |  |  | 2\. add table legislatros_commitees |
| 0.2.0 | 2016/06/09 | Hong | 1\. Move column onboard\_date from legislators to legislators\_committees |
|  |  |  | 2\. Remove table legislators_districts |
|  |  |  | 3\. Add column electoral\_district\_id to districts |

## Relational Diagram

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_150dde1c786c288a7afb7a1bf9838de6)



## Schemas

### legislators

| **Field Name** | **Key** | **Data Type** | **Description** |
| --- | --- | --- | --- |
| id | primary key | integer(10), unsigned |  |
| name |  | varchar(60) | 中文性名 |
| english_name |  | varchar(60) | 英文姓名 |
| gender |  | char(1) | M: Male, F:Female |
| email |  | varchar(255), nullable |  |
| experience |  | varchar(1023), nullabel |  |
| facebook |  | varchar(255), nullable |  |
| wiki |  | varchar(511), nullable |  |
| line |  | varchar(255), nullable |  |
| party_id | foreign key | integer(10), unsigned, nullable | 政黨 |
| party\_group\_id | foreign key | integer(10), unsigned, nullable | 黨團 |
| electoral\_district\_id | foreign key | integer(10), unsigned | 選區, ex: 台中市第五選區 |

### committees

委員會
| **Field Name** | **Key** | **Data Type** | **Description** |
| --- | --- | --- | --- |
| id | primary key | integer(10), unsigned |  |
| name |  | varchar(60) | ex:外交及國防委員會 |

### legislators_committees

| **Field Name** | **Key** | **Data Type** | **Description** |
| --- | --- | --- | --- |
| legislator_id | foreign key | integer(10), unsigned |  |
| committee_id | foreign key | integer(10), unsigned |  |
| term |  | integer(10), unsigned | 任期；第幾屆 |
| session |  | integer(10), unsigned | 會期；第幾會期 |
| onboard_date |  | timestamp |  |


### parties

政黨
| **Field Name** | **Key** | **Data Type** | **Description** |
| --- | --- | --- | --- |
| id | primary key | integer(10), unsigned |  |
| name |  | varchar(60) |  |

### party_groups

黨團
| **Field Name** | **Key** | **Data Type** | **Description** |
| --- | --- | --- | --- |
| id | primary key | integer(10), unsigned |  |
| name |  | varchar(60) |  |


### electoral_districts

選區
| **Field Name** | **Key** | **Data Type** | **Description** |
| --- | --- | --- | --- |
| id | primary key | integer(10), unsigned |  |
| name |  | varchar(60) | 選區, ex: 台中市第五選區 |

### districts

選區所含蓋的行政區(區、市、鄉)
區域立委才有
| **Field Name** | **Key** | **Data Type** | **Description** |
| --- | --- | --- | --- |
| id | primary key | integer(10), unsigned |  |
| name |  | varchar(60) | ex:大安區 |
| electoral\_district\_id | foreign key | integer(10), unsigned |  |

### serving_offices

服務處
| **Field Name** | **Key** | **Data Type** | **Description** |
| --- | --- | --- | --- |
| id | primary key | integer(10), unsigned |  |
| address |  | varchar(255) |  |
| telephone |  | varchar(20), nullable |  |
| fax |  | varchar(20), nullable |  |
| legislator_id | foreign key | integer(10), unsigned |  |





