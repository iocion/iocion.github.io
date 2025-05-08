### sql语法
```sql
create table student(
    sno char(10) primary key,
    sname varchar(20) not null,
    ssex char(2),
    sage smallint,
    sdept char(20)
);
```

```sql
create table student(
	sno char(10),
    sname char(2) not null,
    sage smallint,
    sdept char(20),
    primary key (sno)
);
```

将表中的Sno,Cno属性组定义为码

```sql
create table sc(
	sno char(9) not null,
	cno char(4) not null,
	grade smallint,
    primary key (sno,cno)， /*在表级定义实体完整性*/
    foreign key (sno) references student(sno),/*在表级定义参照完整性*/
    foreign key (cno) references course(cno) /*在表级定义参照完整性*/ 
);
```

三大完整性：实体完整性，参照完整性，用户自定义完整性

级联：cascape 
拒绝执行：no action

#### 属性上的约束条件：

```sql
not null or null
unique /*唯一*/
check /*检查*/
```

```sql
create table dept(
    deptno numeric(2),
    dname char(9) unique not null, /*要求dname列值唯一，且不能取空值*/
    location char(10),
    primary key (deptno)
);
```

```sql
/*check用法*/
create table student(
.....
ssex char(2) check(ssex in('男','女')),
.....   
);
/*like 用法*/
check (ssex='女' or sname not like 'Ms.%') /*定义了元组中sname和ssex两个属性组之间的约束条件*/
```

#### 完整性约束命名子句

```sql
constraint <完整性约束条件名> <完整性约束条件>
```

完整性约束条件包括 not null , unique primary key , foreign key ,check .....

