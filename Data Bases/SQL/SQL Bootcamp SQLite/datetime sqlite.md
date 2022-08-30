https://www.sqlitetutorial.net/sqlite-date/

# Datetime
#### YYYY-MM-DD HH:MM:SS.SSS



```sql
-- UTC date and time
SELECT datetime('now')`
-- `2022-05-24 19:04:59`


SELECT datetime('now', 'localtime')
-- 2022-05-24 21:07:47

SELECT date(datetime('now', 'localtime'))
-- 2022-05-24

SELECT time(datetime('now', 'localtime'));
-- 21:10:51
```









