# 清空表数据操作
delete----速度慢，不适合大量数据删除，但是可以进行条件删除
```python
delete from tablename where id=1
```
truncate----清空表数据，速度教delete快，但是不支持条件删除，不支持撤销还原
```python
TRUNCATE TABLE tablename
```
drop----删除表以及数据，快速
```python
TRUNCATE TABLE tablename
```
# limit用法

```python
SELECT * FROM table LIMIT 5,10; // 检索记录行 6-15, 偏移量从0开始数，这里5就是0,1,2,3,4,5   
```

```python
SELECT * FROM table LIMIT 5; //检索前 5 个记录行   
```

# 连接
## 内连接
内连接其实就是公共部分
```python
SELECT * from A JOIN B ON A.Aid=B.Bid
SELECT * from A,B WHERE A.Aid=B.Bid
```
## 左连接
左连接就是公共交集加上左边的A，对应不上的字段则为null
```python
SELECT * FROM A LEFT JOIN B ON A.Aid=B.Bname
```
## 右连接
右连接就是公共交集加上右边的B，对应不上的字段则为null
```python
SELECT * FROM A RIGHT  JOIN B ON A.Aid=B.Bname
```
