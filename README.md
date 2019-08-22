&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ***以下为oracle数据库中sql语句的整理，将持续更新***
01、	如何登陆用户							
```sql
conn 用户名/口令;
```
02、	如何创建用户并设置密码和默认表空间				
```sql
create user 用户名 identified by 口令 dafault tablespace users;
```
03、	如何查看所有表空间						
```sql
select * from dba_tablespace;
```
04、	如何查看当前用户							
```sql
show user;
```
05、	如何查看所有用户							
```sql
select * from all_users;
```
06、	如何修改用户口令							
```sql
alter user 用户名 identified by 新口令;
```
07、	如何锁定用户							
```sql
alter user 用户名 account lock;
```
08、	如何解锁用户							
```sql
alter user 用户名 account unlock;
```
09、	如何删除用户							
```sql
alter user 用户名 cascade;
```
10、	如何给用户授予创建会话权限					
```sql
grant create session to 用户名;
```
11、	如何查看用户权限							
```sql
select * from user_sys_pivs;
```
12、	如何授予用户权限转让权限						
```sql
grant create any table,execute any procedure to 用户名 with admin option;
```
13、	Oracle中的三种权限是什么？					

> 1. connect：分配给普通用户
> 2. resource：分配给设计人员
>  3. dba： 授予系统管理员
> 具体说明请转到[connect、resource和dba三个标准角色权限](https://blog.csdn.net/weixin_43712330/article/details/88255050)

14、	如何创建表空间，并同时创建DBF文件					
```sql
create tablespace 表空间名 datafile '文件路径（绝对路径）.dbf';
```
15、	如何修改表空间的状态，表空间的状态有哪几个			

> 离线、在线、只读、read、write   
```sql
alter tablespace 表空间名 状态名；
```

16、	如何修改表空间文件DBF文件大小					
```sql
alter dataspace datafile '文件路径（绝对路径）.dbf'resize 目标大小；
```
17、	如何添加DBF文件（数据库文件）					
```sql
alter tablespace 表空间名 add datafile '文件路径（绝对路径）.dbf' size 目标大小;
```
18、	如何删除表空间和文件						
```sql
drop tablespace 表空间名 including contents and datafiles;
```
19、	如何查看数据库文件						
```sql
select * from dba_data_files;
```
20、	表空间和数据库文件的关系						

> 一对多

21、	数据库的数据保存在哪里？						

> 保存在dbf文件中

22、	数据库的实体：					

> 表

23、	Oracle的数据类型：						
> 1. number(字节长度)  
> 2. varchar2(字节长度)  
> 3. char(字节长度)默认长度为一个字节  
> 4. date：DD-MM-YY 
> 5. dfile、clob、blob(三种大型对象，大数据类型(能够保存较大文件,最大为4G))

24、	如何创建表？							
```sql
create table 表名(
cid bumber(4),
cname varchar2(100),
cyear number(4),
clen number(1)  
);
```
25、	如何添加数据							
```sql
insert into 表名 values(要添加的数据);
```
26、	如何删除所有的数据						
```sql
delete from 表名;
```
27、	如何添加主键约束							
```sql
alter table 表名 add constraint PK_表名_列名 primary key(列名);
```
28、	如何添加非空约束							
```sql
alter table 表名 add constraint UQ_表名_列名 unique(列名);
```
29、	如何添加不为空，唯一约束							
```sql
alter table 表名 add constraint modify 列名 not null;
```
30、	如何删除表							
```sql
drop table 表名;
```
31、	如何创建带行级约束的表						
```sql
create table 表名(
cid number(4) primary key, 
cname varchar2(100) unique not null,
cyear number(4) not null 
);
```
32、	如何创建自增长的主键						
```sql
create sequence class_test start with 开始值 increment by 增长数值;
```
33、	如何添加外键约束							
```sql
alter table 表名 add constraint FK_表名_列名 foreign key(列名) reference 目标表名(目标列名);
```
34、	如何添加检查约束							
```sql
alter table 表名 add constraint CK_表名_列名 check(检查语句);
```
35、	如何删除约束							
```sql
alter table 表名 drop constraint 约束名;
```
36、	如何添加默认约束，添加了默认约束之后如何添加数据才能正确使用默认约束
```sql
alter table 表名 add modify 列名 default '默认值';
```
37、	如何查看表的所有约束						
```sql
select * from user_constranints where tablename='表名(表名必须全部大写)';
```
38、	如何在建表时添加约束						
```sql
create table 表名(
stuNo number(10) primary key,
cid number(4) constraint FK_STUINFO_cid references classInfo(cid),
stuCarId varchar2(20) constraint CK_STUINFO_stuCarId check(length(stuCarId)=18), 
sex varchar2(4), 
stuAge number(3) constraint CK_STUINFO_stuAge check(stuAge>12 and stuAge<30),
stuTel vaarchar2(15) unique;
```
39、	如何查看表的结构							
```sql
select * from user_tab_columns where talble_name='表名(表名必须全部大写)';
```
40、	如何修改表名							
```sql
alter table 表名 rename to 新名字;
```
41、	如何修改表的列（删除列、添加列）					
```sql
alter table 表名 rename column 列名 to 新名字;
```
42、	SQL语句由哪几部分组成？						

> 1. DCL(Data Control Language):数据控制语言 
> &nbsp; &nbsp; grant&nbsp; &nbsp; &nbsp; revoke
> 2. DDL(Data Definiation Language):数据定语言 
>  &nbsp; &nbsp; create&nbsp; &nbsp; &nbsp; drop&nbsp; &nbsp; &nbsp; truncate
> 3. DML(Data Manipulation Language):数据操作语言  
> &nbsp; &nbsp; insert&nbsp; &nbsp; &nbsp; delete&nbsp; &nbsp; &nbsp; updata&nbsp; &nbsp; &nbsp; select
> 4. TCL(Transcation Contro;Language):事务控制语言 
> &nbsp; &nbsp; rollback&nbsp; &nbsp; &nbsp; commit&nbsp; &nbsp; &nbsp; savepoint

43、	如何参照另一个表建表（要表记录\不要表记录）			
```sql
要记录：
create table 表名 as select * from 参照表名;  
不要记录：
create table 表名 as select * from 参照表名 where 1=0;
```
44、	如何参照另一个表建表并且修改参照表的列名				
```sql
create table 表名 as select 列名1、列名2、列名3...列名n as 新列名n from 参照表名;
```
45、	如何同时想某个表中插入多条记录					
```sql
insert into 表名 
select 5,'女','小花' from dual union --union 连接词
select 5,'女','小红' ;
```
46、	数据更新（更改表中数据）						
```sql
update 表名 set name='张思' where id=8;
```
47、	如何删除指定数据							
```sql
delete from 表名 where tsex='男';
```
48、	dual表的作用							

> Oracle中的一个实际存在的表，任何用户均可访问读取，常在没有任何目标的select语句块中使用(一个神奇的表)

-----------------------------------------------2019/3/8 21:13更新------------------------------------------------------
49、	什么是事务？							
> 事务是最小的工作单位，作为一个整体进行工作保证事务成功或失败称为事务控制

50、	事务的提交与回滚，以及回滚时要注意的地方				
> 事务的提交:commit; 
>  事务的回滚:rollback;      --rollback撤销本次未提交的事务

51、	部分回滚的设置，在部分回滚时跳过若干个时间点直接回滚到很久之前的保存点，这之间的保存点会发生怎么样的变化		
>  如果一个事务中包含多个执行语句，要部分回滚，则用到savepoint。
 例:
```sql
savepoint p1--将当前数据库的数据状态设置为一个保存点
update stuInfo set name='李四' where id=1;
savepoint p2;
delete from stuInfo where id=1;
rollback to savepoint p1;
```
> 如果使用了`rollback`回滚到时间点`p1`处那么在`p1`之后的时间点中的保存点将全部销毁

52、	怎么生成序列	
在设计表的时候需要一个不需要明确意义的列作为主键，这时需要序列。
```sql
create sequence seq_id('序列名');
create sequence seq_id start with 1000 increment by 2;--从某个地方开始自增长的序列 
```
53、	怎么获取当前序列的值						
```sql
select seq_id.curral from dual;
```
54、	如何删除序列						
```sql
drop sequence seq_id(序列名);
```
55、	如何使用序列							
```sql
insert into stuInfo(seq_id.nextval,'张三');
```
56、	基础查询								
```sql
select * from 表名 where 条件; 

查询时进行数学运算  例:
select empno,ename,sal+comm as sal from emp;--其中as可以省略，sal可以任意改变
```
57、	连接操作符有哪几个，作用分别是什么				

> `union`、`union all`、`intersect`、`mius`    
> `union`:连接上下信息,并剔除重复信息    
> `union` all:连接上下信息,不剔除重复信息    
> `intersect`:获得相同的数据    
> `minus`:获得不相同的数据
58、	exists如何使用							
```sql
例:
select * from student where exists 
(select * from classInfo where classInfo.cid=1001 and classInfo.cid=student.cid);
```
59、	内联查询								
```sql
例:
select * from student s inner join classInfo cs on s.cid=cs.cid where cs.cid=1001;
```
60、	左联查询								
```sql
例:
select * from a left join b on a.id=b.id;  
--a,b均为表名 只要a表有，而b可没有对应的记录。此时b表中的所有字段用null代替。
```
61、	右联查询								
```sql
例:
select * from a right join b on a.id=b.id; 
--a,b均为表名 和左外联相反，只要b表有，a表可没有对应的记录。
```
62、	数值函数：floor、trunc、ceil、round的作用以及用法			
```sql
floor:求平均数,忽略小数 
例:
select ename,sal/30 sal,floor(sal/30) 日平均工资 from emp; 
trunc:求平均数,保留两位小数  
例:
select ename,sal/30 sal,trunc(sal/30) 日平均工资 from emp; 
ceil:求平均数,向上取整  
例:
select ename,sal/30 sal,ceil(sal/30) 日平均工资 from emp;  
round:求平均数,四舍五入  
例:
select ename,sal/30 sal,round(sal/30)日平均工资 from emp;
```
63、	聚合函数：max、min、avg、sum的作用及用法				
```sql
max:最大值  
min:最小值 
avg:平均值 
sum:总和   
例:
select max(sal),min(sal),avg(sal),sum(sal) from emp;
--求员工的最高底薪，最低底薪，平均底薪，底薪总和
```
64、	如何查询某例所有的值						
```sql
select all 列名 from 表名;
```
65、	如何过滤重复的数据						
```sql
distinct:过滤重复的数据	
select distinct addr from student;--统计学生来自哪里
```
66、	如何统计共有多少行数据						
```sql
count:总数  
select count(distinct addr) from student;--统计学生来自多少个地区(并去重)
```
67、	例：如何查询学生性别如果是男转换为M如果是女转换为F(两种写法)	
```sql
decode:译码  
例:
select sname,decode(sex,'男','M','F')性别 from student;		
另一种写法:
select sname,case sex when '男' then 'M' when '女' then 'F' end 性别 from student;
```
-----------------------------------------------2019/3/9 16:40更新------------------------------------------------------
68、	分析函数有哪几个？						
> (1)、order by(排序函数,desc 降序,asc升序)
> (2)、rank(排序)
> (3)、DENSE_RANK(排序)
> (4)、 row_number(排序)
> (5)、rownum(分页查询)

69、	升降序排序							

```sql
--升序:
select * from 表名 order by 列名 (asc);
--列名后什么都没有时默认升序排序 
--降序:
select * from 表名 order by 列名 desc;
```

 
70、	row_number()排序						

```sql
--如果字段值相同,序号也不中断:
select row_number over(order by 列名 desc) as 自定义名称 from emp;--(as可省略) 
--效果:1 2 3 4 5 6
```

71、	rank 排序							

```sql
--具有相同的值得排位相同，随后序数跳跃:
select rank() over(order by 列名 desc) as 自定义名称 from emp; 
--效果:1 2 2 4 4 6
```

72、	DENSE_RANK							

```sql
--具有相同的值的排位相同,随后的序号是连续的:
select DENSE_RANK() over(order by sal desc) as 自定义名称 from emp; 
--效果: 1 2 2 3 3 4 4 5
```

73、	分页查询							

```sql
rownum: select * from 列名;--自动生成了rownum并有1-14的值 
select a.*,rownum from (select * from emp) a where rownum<=10;--查询<=10的序列数据
```

74、	分组查询 group by 分组 having 筛选				

```sql
group by  having : select 分组依据,a from 表名 group by 分组依据 having 条件;
--a处可添加计算结果如:sum(),max(),avg()...等
--having 和where类似用法 
--group by 可以去重 
--order by 也是分组的一种，如果同时使用了group by 和 order by 需将'by'后的全部写在from之前 
```

###### 高级查询是基础查询的组合使用
75、	连接查询							

```sql
例:
select * from stuInfo sf,score sc,course cs where sc.courseid=cs.cid and
sc.stuid=sf.stuid and sc.score<60 and cs.cname='html网页设计';
```

76、	<补充>日期数据类型的使用					

> 日期数据类型的使用呢，已经有很多大神们都总结过了，我也就不再过多的说明
> 详见:https://blog.csdn.net/qq_33573235/article/details/78154928

```sql
date数据类型查入数据时:
insert into 表名 values(to_date('2018-1-25','YYYY-MM-DD'));
date数据类型查询某个月份时:
select * from 表名 where to_number(to_char(sdate,'MM'))='3';--查询三月份的数据
```

77、	<补充>修改字段数据类型						

```sql
alter table tablename modify filedname varchar2(20);
```
-----------------------------------------------2019/3/14 20:00更新------------------------------------------------------

截至到2019/3/14 20:00呢，这个关于Oracle数据库sql语句的更新也差不多就要结束了，各位路过的大神们如果对本篇文章有看法的话欢迎提出来，让我继续改进或者高兴一会。初次接触数据库还有很多不懂的地方，希望以后可以把数据库了解的更清楚一点吧。


<br /><br /><br />
### &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 拜拜了您嘞*★,°*:.☆(￣▽￣)/$:*.°★* 。

<br />
我“胡汉三”又回来了，突然发现还有些没写完的...来吧<br />
78、<补充>模糊查询

```sql
select * from student where sname like '%所查询字符%';
--‘%’ 是有字符但是不用去管他是啥，可以放到前面也可以放到后面

select * from 表名 where 列名 like '张__';--'张'的后面是两个'_'
--两个‘_’代表着两个不知道是啥的字符，啥都行,但是必须是两个,‘_’的数量多少都行,放前放后也都可以

2019-3-15 20:20    --这更新时间选的真好
```
### &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 溜了溜了★,°*:.☆(￣▽￣)/$:*.°★* 。
