---
title: "SQL-1"
date: 2022-08-14T10:40:10+08:00
draft: false
tags: ["数据库"]
categories: ["数据库"]
---
## SQL的连接
SQL的连接可以分为内连接（默认，不需要写 inner join）、左连接(left join/ left outer join)、右连接(right join/ right outer join)、全连接（full join, Mysql不直接支持，可以使用union实现）
左连接就是保留左边表没有与右边表匹配的列，右边表对应的列会被赋空值，右连接同理。

一道简单的用左连接实现的题目示例：
https://leetcode.cn/problems/combine-two-tables/description/

全连接用union的实现
```sql
select t1.c1, t2.c2 
from t1 
left join t2 
on t1.c3 = t2.c3
union
select t1.c1, t2.c2 
from t1 
right join t2 
on t1.c3 = t2.c3    
```

## limit的使用
#### 查找第几大/第几小的元素
下面为查找第二大薪资的示例，使用limit 1, 1即从第二个开始返回一个。需要注意的是使用distinct去重，不然可能出现多个最大值相同的情况，此时如果不去重返回的仍是最大值。
https://leetcode.cn/problems/second-highest-salary/description/

```sql
select distinct salary
from Employee
order by salary desc
limit 1, 1
```
另外一种解法，由于此题目的特殊性（求第二个），因此可以使用max函数来实现
```sql
select max(salary)
from Employee
where salary < (select max(salary)
from Employee)
```
如果要求不存在返回null(只是本题需要),则使用ifNull
```sql
select ifNull(
(select max(salary)
from Employee
where salary < (select max(salary)
from Employee)
)
, 
null
) as SecondHighestSalary
```