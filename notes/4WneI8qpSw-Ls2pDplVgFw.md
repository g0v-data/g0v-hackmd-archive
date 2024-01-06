---
title: "addressbook-api"
tags: hackpad
---

# addressbook-api

> [點此觀看原始內容](https://g0v.hackpad.tw/I0XwxrdoilO)

~Server:~ [~http://pgrest.io/hychen/api.addressbook/v0/collections/~](http://pgrest.io/hychen/api.addressbook/v0/collections/)
~server is base on~ [~PgREST~](http://pgre.st/)  [~投影片~](https://speakerdeck.com/clkao/pgrest-postgresql-javascript-and-rest)
[~how to host api.addressbook at local~](https://gist.github.com/Superbil/11076880)

目前使用新的方案 [Popit](http://popit.poplus.org/)  [API文件在此](http://popit.poplus.org/docs/api/)
server: [https://taiwan.popit.mysociety.org/](https://taiwan.popit.mysociety.org/)

## server side

:type is organization, person, membership

**Search**
- **global search**
    /search?q="keyword"

- search on type
```javascript
request: /person/search?q="張"
{
    "paging": {
        "count": 111,
        "l": 2,
        "sk": 0
    },
    "entries": [
     {s

            "memberships": [
                ...
            ],
            "name": "張建榮",
            "id": 1
        },
        {
            "memberships": [
                ...
            ],
            "name": "張漢東",
            "id": 11
        }
    ],
    "query": "(\"name\" ~ '張')"
}


```
- **scope search**
    /:type/:subtype/:subtype_id/:name/search?q="keyword"

```javascript
request: /person/memberships/2/name/search?q="張"
{
    "paging": {
        "count": 5,
        "l": 2,
        "sk": 0
    },
    "entries": [
        {
            "memberships": [
                {
                 id: 2,
                 role: "黨員"
                 ...
             }
             ...
            ],
            "name": "張建榮",
            "id": 1
        },
        {
            "memberships": [
             {
                 id: 2,
                 role: "黨員"
                 ...
             }
             ...
            ],
            "name": "張漢東",
            "id": 11
        }
    ],
    "query": "(\"name\" ~ '張')"
}


```
**Resource**
- **one data with id**
    /:person/:person_id/
    這邊就直接寫 person 如何?
> 讓他是個變數，這樣比較好懂 :smile:
> [name=Superbil]

> person不是固定的 string 嗎? 應該不會變了吧 
> [name=Kuang-Che L]

> 除了 person 外還有 organiztaion 和 membership 阿
> [name=Superbil]


```javascript
request: /person/1
{
 name:"Foo Bar"
 memberships: [
 {
     id: 1,
     role: "議長"
     ...
 },
 {
     id: 2,
     role: "黨員"
     ...
 }
 ]
 ...
}

```
## Base mapping

- paging:
    - count // 總數
    - l // 長度
    - sk // offset 位置
    - fo: only return entry if fo is true
    - c: only return count if c is true
- entries:
    資料的 array
- query:
    查詢的條件

## organization:

/organzations/
- entries:
    [popolo.organzation](http://popoloproject.com/specs/organization.html)

## Person

/person/
- entries:
    popolo.person

## Membership:

/membership/

