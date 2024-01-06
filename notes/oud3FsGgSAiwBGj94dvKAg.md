# Collect your documents with a book

View the book with "<i class="fa fa-book fa-fw"></i> Book Mode".

Examples
---
- [Book example](/s/book-example)
- [Slide example](/s/slide-example)
- [YAML metadata](/s/yaml-metadata)
- [Features](/s/features)

Themes
---
- [Dark theme](/theme-dark?both)
- [Vertical alignment](/theme-vertical-writing?both)

```
SELECT '{{fab}}' AS site,
       SUBSTR({{bucket_key}},1,10) AS Compare_Date,
       COUNT({{count_key}}) AS Oracle_Count 
  FROM (SELECT TO_CHAR({{bucket_key}},'yyyy-mm-dd hh24:mi:ss') AS {{bucket_key}},                        SAMPLE_ID                 
          FROM SPACE.t_ext_samples
         WHERE {{bucket_key}} > to_date('{{date1}}','yyyy-mm-dd hh24:mi:ss')
           AND {{bucket_key}} <=to_date('{{date2}}','yyyy-mm-dd hh24:mi:ss') 
       ) samples 
GROUP BY '{{fab}}',SUBSTR({{bucket_key}},1,10) 
ORDER BY '{{fab}}',SUBSTR({{bucket_key}},1,10)
```
###### tags: `Templates` `Book`
