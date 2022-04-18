# 10道myql查询面试题目
## 创建表结构sql
```
create table student(
id int unsigned primary key auto_increment,
name char(10) not null
);
insert into student(name) values('张三'),('李四');

create table course(
id int unsigned primary key auto_increment,
name char(20) not null
);
insert into course(name) values('语文'),('数学');

create table student_course(
sid int unsigned,
cid int unsigned,
score int unsigned not null,
foreign key (sid) references student(id),
foreign key (cid) references course(id),
primary key(sid, cid)
);
insert into student_course values(1,1,80),(1,2,90),(2,1,90),(2,2,70);

```
## 问题1

```
查询student表中重名的学生，结果包含id和name，按name,id升序
-- 解法一
-- SELECT s.id , s.name
-- FROM student s
-- WHERE ((SELECT COUNT(*) FROM student WHERE name=s.name)>1)
-- ORDER BY s.name,s.id ASC

-- 解法二
-- SELECT s.id , s.name
-- FROM student s
-- WHERE s.name IN (SELECT name FROM student GROUP BY name HAVING (COUNT(*)>1))
-- ORDER BY s.name,s.id ASC
```

## 问题2
```
-- 在student_course表中查询平均分不及格的学生，列出学生id和平均分

SELECT sc.sid, AVG(sc.score) AS averagescore 
FROM student_course sc
GROUP BY sc.sid HAVING averagescore < 81
```

## 问题3
```
-- 在student_course表中查询每门课成绩都不低于80的学生id
-- 取反思想
-- SELECT DISTINCT sc.sid
-- FROM student_course sc
-- WHERE sc.sid NOT IN (SELECT sid FROM student_course WHERE score<80)

```

## 问题4
```
-- 查询每个学生的总成绩，结果列出学生姓名和总成绩 
-- 如果使用下面的sql会过滤掉没有成绩的人


SELECT s.name,SUM(sc.score) as scores
FROM student_course sc LEFT JOIN student s on sc.sid = s.id
GROUP BY sc.sid ORDER BY scores ASC

```

## 问题5
```
-- 总成绩最高的学生，结果列出学生id和总成绩 下面的sql效率很低，因为要重复计算所有的总成绩。

SELECT s.name,SUM(sc.score) as scores
FROM student_course sc LEFT JOIN student s on sc.sid = s.id
GROUP BY sc.sid ORDER BY scores DESC limit 1

```
## 问题6
```
-- 在student_course表查询课程1成绩第2高的学生，如果第2高的不止一个则列出所有的学生

-- 第二高可不一定是第二名，重点运用子查询

SELECT * FROM student_course s WHERE s.cid = 1 and s.score =
(SELECT sc.score
FROM student_course sc 
WHERE sc.cid = 1 ORDER BY score DESC LIMIT 1 offset 1)

```

## 问题7
```

```





