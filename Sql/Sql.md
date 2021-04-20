<!--
 * @Author: joker.zhang
 * @Date: 2021-04-19 15:11:36
 * @LastEditors: joker.zhang
 * @LastEditTime: 2021-04-19 17:50:34
 * @mail: zhanghua7890@163.com
 * @Description: For Automation
-->

# Student-Course-SC-Teacher
Student-Course-SC-Teacher 表字段： 
* Student（sid，Sname，Sage，Ssex）学生表
* Course（cid，Cname，tid）课程表
* SC（sid，cid，score）成绩表
* Teacher（tid，Tname）教师表
## insert多组数据
```python
INSERT INTO [dbo].[Student]
           ([sid]
           ,[Sname]
           ,[Sage]
           ,[Ssex])
     VALUES
           ('20131201','Joker','18','男'),('20131202','Zhang','28','女'),('20131203','Chen','29','女'),('20131204','Song','33','女')
```
```python
INSERT INTO [dbo].[Teacher]
           ([tid]
           ,[Tname])
     VALUES
           ('0001','张三'),('0003','李四'),('0002','王五')
```
```python
INSERT INTO [dbo].[Course]
           ([cid]
           ,[Cname]
           ,[tid])
     VALUES
          ('001','数学','0001'),('002','语文','0002'),('003','英语','0003')
```
```python
INSERT INTO [dbo].[SC]
           ([sid]
           ,[cid]
           ,[Cname])
     VALUES
           ('20131203','001','99'), ('20131203','002','92'), ('20131203','003','91'),('20131204','001','67'),('20131204','002','99'),('20131204','003','88')
```

## 查询课程“001“课程比”002“课程成绩高的所有学生的学号
```python
select * from SC
sid	cid	Cname
20131201  	001       	85        
20131201  	002       	90        
20131201  	003       	91        
20131202  	001       	87        
20131202  	002       	91        
20131202  	003       	68        
20131203  	001       	99        
20131203  	002       	92        
20131203  	003       	91        
20131204  	001       	67        
20131204  	002       	99        
20131204  	003       	88        
```
```python


```
# sql清空表数据操作
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