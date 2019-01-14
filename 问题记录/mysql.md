# 查询重复出现次数最多的记录

```mysql
SELECT keyword, count( * ) AS count
FROM article_keyword
GROUP BY keyword
ORDER BY count DESC
LIMIT 20
```

# 查询某个字段的值出现的次数

```mysql
SELECT datetime, SUM('blue') AS 'blue', SUM('red') AS 'red' 
FROM color GROUP BY datetime 
```

