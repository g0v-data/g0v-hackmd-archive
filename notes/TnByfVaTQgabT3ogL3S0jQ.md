# Kettle注意事項

table output
特点：

1，字段刷新，表结构修改后，必须在kettle里清除缓存，tools->clear catch，才能看到新字段。

或者麻烦一点：编辑【表输出】的属性，选择【数据库连接】【编辑】，选择【浏览】，点击这张表，在弹出界面中选择【action】【DDL】【use current connection】,在弹出界面中选择【清除缓存】

2. PostgreSQL不支持批量插入：当目标数据库为PostgreSQL时，【使用批量插入】勾掉，不支持。

3. 默认目标表字段和源数据的字段一致，如果不一样，需要选中【specify database fields】，否则映射配置没作用。,