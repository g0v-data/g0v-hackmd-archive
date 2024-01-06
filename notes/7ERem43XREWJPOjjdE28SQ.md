# 頭像與假名

LINE bot 使用者會使用生成的頭像與名字。

## 頭像

目前實作：Gravatar 提供的 identicon (wordpress)

- [各家 Identicon 比較](https://barro.github.io/2018/02/avatars-identicons-and-hash-visualization/)
- ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0d156fe19d9a6c42680b53cba213d6ec =48x) [Get avataaars](https://getavataaars.com/)
- [Github style identicon](https://github.com/stewartlord/identicon.js)
- [jdenticon](https://jdenticon.com/)
- [Open Peeps](https://github.com/CeamKrier/react-peeps) (chosen)

不用 dedup

## 假名

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_08ca66bee421f31309e1458334116317)
https://github.com/PlatoForum/PlatoForum/tree/2cdc807a6ec54f68e0479787ccb865f0e89aed50/utils/pseudonym_gen (不考慮英文)

不用 dedup

(同時頭像跟假名一樣的機率也很小就是了)

### 形容詞

- 煞氣
- 煞氣a
- 疝氣
- 狂氣
- 超狂
- 可愛
- 可愛の
- 敲可愛
- 萌萌噠

### 地名
直接用區域名，或許可以達到跨縣市的功效 (?)

- 板橋
- 東區
- 西區
- 中西區
- 北區
- 永和
- 頭城
- 竹圍
- 台西

### 人名
- 林志玲
- 金城武
- 小叮噹
- 阿姆羅
- 

### Separator

- `adjplacename`
- `adj✖place✖name`
- `place✖adj✖name`
- `adj✿place✿name`
- `adj卍place卍name`


### Decorator

- `joinedName`
- `joinedName®`
- `joinedName™`
- `↖joinedName↗`
- `☞joinedName☜`
- `卍joinedName卍`
- `joinedName♡`
- `㊣joinedName㊣`
- `OojoinedNameoO`
- `乂joinedName乂`
