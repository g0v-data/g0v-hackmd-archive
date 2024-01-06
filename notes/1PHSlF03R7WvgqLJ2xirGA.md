# 0archive 資料缺少確認流程

以 自由時報 http://news.ltn.com.tw/ 為例

1. 確認有沒有抓到文章 (`discover`)

去 [phpMyAdmin](https://middle2.com/phpMyAdmin/db_structure.php?server=1&db=user_tainan-sun-500796) /user_tainan-sun-500796 去看 table `SiteStats` 
```sql=
SELECT * FROM SiteStats where site_id = (SELECT site_id FROM Site where url like "%ltn%");
```

- 若沒有抓到文章，確認
    - (A) [m2首頁](https://middle2.com/project/detail/tainan-sun-500796)  的 `Node Status` 中是否有 `CronNode:python3 ./zs.py discover --limit-sec 3000`，
    - (B) [phpMyAdmin](https://middle2.com/phpMyAdmin/db_structure.php?server=1&db=user_tainan-sun-500796) 的 `Variable` table，是否有 `key=discover:pid` 的 row。
    - 若 (A) 無 (B) 有，則將 (B) 手動刪除後即可恢復

2. 確認有沒有 parse & publish
去 [phpMyAdmin](https://middle2.com/phpMyAdmin/db_structure.php?server=2&db=user_taoyuan-chu-975484) /user_taoyuan-chu-975484 去看 table `parser_stats` 

```sql=
SELECT * FROM `parser_stats` where producer_id = (select producer_id from producer where url like "%ltn%")
```


###### tags: `0archive`