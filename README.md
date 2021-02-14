# Note---Database-System-Concepts

## 第一章 绪论
### 数据、数据库、数据库管理系统、数据库系统的概念
```
数据：描述事务的符号记录称为数据
数据库：数据库是长期存储在计算机内的，有组织的，可共享的数据集合
数据库管理系统：DBMS，是位于用户与操作系统之间的一层数据管理软件，
  用于科学地存储和组织数据，高效地获取和维护数据
数据库系统：指计算机系统中，引入数据库后的系统构成，一般由数据库、
  数据库管理系统（及其开发工具）、应用系统、数据库管理员构成
```
### 使用数据库系统的好处
```
大大提高应用开发的效率，方便用户的使用，减轻数据库系统管理人员维护的负担。
  因为在数据库系统中，应用程序不必考虑数据的定义，存储和数据存取的具体路径，
  这些工作都由DBMS来完成。
```
### 文件系统与数据库系统的区别和联系
```
区别：
  文件系统面向某一应用程序，共享性差，冗余度大，数据独立性差，
  记录内有结构，整体无结构，由应用程序自己控制。数据库系统面向现实世界，
  共享性高，冗余度小，具有较高的物理独立性和一定的逻辑独立性，整体结构化，
  用数据模型描述，由数据库管理系统提供数据的安全性、完整性、并发控制和恢复能力。
联系：
  都是计算机系统中管理数据的软件。解析文件系统是操作系统的重要组成部分，
  而DBMS是独立于操作系统的软件。DBMS是在操作系统的基础上实现的，
  数据库中数据的组织和存储是通过操作系统中的文件系统实现的。
```
### 适合用文件系统而不是数据库系统的应用例子，以及适合用数据库系统的应用例子
```
前者：数据的备份或应用程序中临时数据的存储
后者：几乎所有企业和部门的信息系统都以数据库系统为基础，如人事管理，图书管理系统等
```
### 数据库系统的特点
- 实现整体数据结构化
- 数据共享性高、冗余度低、易扩充。数据不再面向某个应用而是整个系统，可以被多个用户，多种语言共享使用。
- 数据独立性高
- 数据由DBMS统一管理和控制数据库的共享是并发的共享，即多个用户可以同时存取数据库中的数据，甚至可以同时存取同一个数据
### 数据库管理系统主要功能
```
数据库定义、数据存储、数据库运行管理、数据库的建立和维护
```
### 论述概念模型及其作用
```
概念模型，也叫信息模型，是按用户的观点来对数据和信息建模，主要用于数据库设计，
是现实世界到信息世界的第一层抽象，也是数据库设计人员和用户之间交流的语言
```
### 实体、实体型、实体集
- 实体：客观存在并可以相互区分的事物
- 实体型：具有相同属性的实体具有相同的特征和性质，用实体名及其属性名集合来抽象和刻画同类实体
- 实体集：同型实体的集合
### 数据模型的概念、数据模型的作用、数据模型的三个要素
```
数据模型是数据库中用来对现实世界抽象的工具，是数据库中用来提供信息表示和操作手段的形式构架
数据模型通常由数据结构、数据操作、完整性约束三部分组成
```
### 网状、层次数据库的优缺点
```
层次优点：模型简单，对具有一对多关系的部门描述自然、直观、容易理解；对于实体间联系固定的且预定好的应用，性能优于关系模型
层次缺点：现实中很多联系非层次，如多对多，一个结点多个双亲等，只能通过引入冗余数据或虚拟数据来解决；查询子女结点要通过双亲结点
网状优点：更为直接描述现实世界；具有良好的性能，存取效率高
网状缺点：结构复杂，用户不容易使用，由于记录之间的联系是通过存取路径实现的，应用程序在访问数据时必须选择适当的存取路径
  用户必须了解系统结构的细节，加重了编写应用程序的负担
```
### 数据库系统三级模式结构
```
三级模式结构由外模式、模式、内模式组成。
外模式：也叫子模式或用户模式，是数据库用户能够看见和使用的局部数据的逻辑结构和特征的描述，是数据库用户的数据视图
模式：也叫逻辑模式，是数据库中全体数据的逻辑结构和特征的描述，描述的是数据的全局逻辑结构
内模式：也叫存储模式，是数据在数据库系统内部的表示，即对数据的物理结构和存储方式的描述
优点：把数据的具体组织留给DBMS管理，用户能够逻辑抽象地处理数据，不必关心数据在计算机中的表示和存储
  由于外模式/模式印象和模式/内模式印象的存在，保证了数据库系统中的数据能够具有较高的逻辑独立性和物理独立性
```
### 数据定义语言、数据操作语言
```
数据定义语言：DDL，用来定义数据库模式、外模式、内模式的语言
数据操作语言：DML，用来对数据库中的数据进行查询、插入、删除和修改的语言
```
### 数据与程序
```
物理独立性：当数据库的存储结构改变，由数据库管理员对模式/内模式印象做相应改变，使模式保持不变，应用程序也不变，保证了物理独立性
逻辑独立性：当模式改变（如增加新的属性、新的关系），由数据库管理员对外模式/模式印象做相应改变，是外模式保持不变
  应用程序是依据数据的外模式编写的，从而应用程序不必修改，保证数据与程序的逻辑独立性
正因为数据库管理系统在三级模式之间提供的两层印象，保证数据库系统中的数据具有较高的逻辑独立性和物理独立性
```
### 数据库系统的组成
```
由数据库、数据库管理系统、应用系统、数据库管理员、用户组成
```

## 第二章 关系数据库
### 关系名的三个组成部分
```
关系数据结构、关系操作集合和关系完整性约束
```
### 关系数据语言的特点和分类
```
关系代数语言
关系演算语言：元组关系演算语言和域关系演算语言
SQL：具有关系代数和关系演算双重特点的语言
共同特点：都具有完备的表达能力，是非过程化的集合操作语言，功能强，能够嵌入高级语言中使用
```
### 论述关系模型的完整性规则
```
实体完整性规则是指若属性A是基本关系R的主属性，则属性A不能取空值。
若属性F是基本关系R的外码，它与基本关系S的主码相对应，则对于R中每个元组在F上的值必须为：
或者取空值或者等于S中某个元组的主码值，即属性F本身不是主属性，则可以取空值，否则不能取空值。
```
### 等值连接与自然连接的区别和联系
```
连接运算符是“=”的连接运算称为等值连接。它是从关系R与S的广义笛卡尔积中选取A，B属性值相等的元组
自然连接是一种特殊的等值连接，要求两个关系中进行比较的分量必须是相同的属性组，并在结果中将重复的属性列去掉
```
### 关系代数的基本运算
```
基本运算：并、差、笛卡尔积、投影和选择；而交、连接和除均可以用这五种基本运算来表达
```

## 第三章 关系数据库标准语言SQL
### SQL的特点
```
综合统一：集DDL、DML、DCL的功能与一体
高度非过程化：用SQL语言进行数据操作，只需提出做什么，不必指明怎么做，因此无需了解存取路径
  存取路径的选择以及SQL语句的操作过程由系统自动完成
面向集合的操作方式：不仅操作对象、查找结果可以是元组的集合，插入、删除、更新的操作对象也可以是元组的集合
以同一种语法结构提供两种使用方式：SQL既是自含式语言，又是嵌入式语言。
  作为自含式语言，能够独立的用于联机交互的使用方式
  作为嵌入式语言，它能够嵌入到高级语言程序中
语言简洁，易学易用
```
### SQL语句练习
```
有表：S(Sno,Sname,Status,City) P(Pno,Pname,Color,Weight) J(Jno,Jname,City) sPJ(Sno,Pno,Jno,Qty)
分别建表：
  create table S(
    Sno Char(2) unique,
    Sname Char(6),
    Status Char(2),
    City Char(4)
    );
    ……同理建表
```
### 用上面四个表进行下列各项操作
```
求供应工程J1零件的供应商号码Sno:
  select distinct Sno from SPJ where Jno = 'J1';
求供应工程J1零件为红色的供应商号码Sno:
  select distinct Sno from SPJ, P where SPJ.Pno = P.Pno and Jno = 'J1' and color = '红';
求没有使用天津供应商生产的红色零件的工程号Jno:
  select distinct Jno from SPJ where Jno not in 
    (select Jno from SPJ, P, S where S.Sno = SPJ.Sno and P.Pno = SPJ.Pno and S.City = '天津' and Color = '红');
找出没有使用天津产的零件的工程号码：
  select distinct Jno from SPJ, S where S.Sno = SPJ.Sno and S.City <> '天津';
由S5供给J4的零件P6改为由S3供应：
  update SPJ set Sno = 'S3' where Sno = 'S5' and Jno = 'J4' and Pno = 'P6';
```
### 基本表与视图的区别和联系
```
基本表是本身独立存在的表，在SQL中一个关系对应一个表；视图是从一个表或几个基本表导出的表。
视图本身不独立存储在数据库中，是一个虚表，即数据库中只存放视图的定义而不存放视图对应的数据，
这些数据仍存放在导出视图的基本表中。视图在概念上与基本表等同，可以在视图上再定义视图。
```
### 视图的优点
- 简化用户的操作
- 使用户以多种角度看待数据
- 对重构数据库提供一定程度的逻辑独立性
- 能够对机密数据提供安全保护
### 哪类视图可更新，哪类视图不可更新
```
基本表的行列子集视图一般可更新，若视图的属性来自集合函数、表达式，则该视图不可更新
视图是不实际存储数据的虚表，因此对视图的更新，最终转换为对基本表的更新
```
### 视图练习
```
有一个三建工程，建立一个供应情况的视图，包含供应商代码(Sno), 零件代码(Pno), 供应数量(Qty)
create view vsp as select Sno, SPJ.Pno, Qty from SPJ, J where SPJ.Jno = J.Jno and J.Jname = '三建';
找出三建工程项目的各种零件代码及其数量:
  select distinct Pno, Qty from vsp;
找出供应商S1的供应情况:
  select distinct * from vsp where Sno = 'S1';
```

## 第四章 数据库安全性
### 数据库的安全性
```
指保护数据库以防止不合法的使用所造成的数据泄露、更改或破坏
```
### 实现数据库安全性控制的常用方法和技术
```
用户标识和鉴别：该方法由系统提供一定的方式让用户标识自己的名字或身份，
  每次用户要求进入系统时，由系统核对，通过鉴定后才提供系统的使用权。
存取控制：通过用户权限定义和合法权检查确保只有合法权限的用户访问数据库，所有未被授权的人员无法存取数据，
  例如CZ级中的自主存取控制（DAC），B1级中的强制存取控制（MAC）。
视图机制：为不同的用户定义视图，通过视图机制把要保护的数据对无权存取的用户隐藏起来，
  从而自动地对数据提供一定程度的安全保护。
审计：建立审计日志，把用户对数据库的所有操作自动记录下来放入审计日志中，DBA可以利用审计跟踪的信息，
  重现导致数据库现有状况的一系列事件，找出非法存取数据的人、事件和内容等。
数据加密：对存储和传输的数据进行加密处理，从而使得不知道解密算法的人无法获知数据的内容。
```
### 数据库中的自主存取控制和强制存取控制
```
自主存取控制方法：定义各个用户对不同数据对象的存取权限；当用户对数据库访问时首先检查用户的存取权限，
  防止不合法用户对数据库的存取。
强制存取控制方法：每一个数据对象被强制地标以一定的密级，每一个用户也被强制地授予某一个级别的许可证，
  系统规定只有具有某一许可证级别的用户才能存取某一个密级的数据对象。
```
### 关系模式授权练习1
```
学生（学号，姓名，年龄，性别，家庭住址，班级号）
班级（班级号，班级名，班主任，班长）

授予用户U1对两个表的所有权限，并可给其他用户授权：
  grant all privileges on Student, Class to U1 with grant option;
授予用户U2对学生表具有查看权限，对家庭住址具有更新权限：
  grant select, update(家庭住址), delete on Student to U2;
将对班级表查看权限授予所有用户：
  grant select on Class to public;
将对学生表的查询、更新权限授予角色R1：
  grant select, update on Student to R1;
将角色R1授予用户U1，并且U1可继续授权给其他角色：
  grant R1 to U1 with admin option;
```
### 关系模式授权练习2
```
职工（职工号，姓名，年龄，职务，工资，部门号）
部门（部门号，名称，经理名，地址，电话号）

每个职工只对自己的记录有select权限：
  grant select on 职工 when user() = name to all;
用户张新具有修改这两个表的结构的权限：
  grant alter table on 职工，部门 to 张新;
用户周平具有两个表的所有权限，并具有给其他用户授权的权限：
  grant all privileges on 职工，部门 to 周平 with grant option;
用户杨兰具有从每个部门职工中select最高工资，最低工资，平均工资的权限，她不能查看每个人的工资：
  create view 部门工资 as
  select 部门.名称, max(工资), min(工资), avg(工资) from 职工，部门
  where 职工.部门号 = 部门.部门号
  group by 职工.部门号
  
  grant select on 部门工资 to 杨兰;
撤销上述权限：
  revoke select on 部门工资 from 杨兰;
  drop view 部门工资;
```
### 强制存取控制机制中(MAC)主体、客体、敏感度标记的含义
```
主体：系统中的活动实体，既包括DBMS所管理的实际用户，也包括代表用户的各进程
客体：系统中的被动实体，受主体操控，包括文件、基表、索引、视图等；对于主体和客体，
  DBMS为它们每个实例指派一个敏感度标记
敏感度标记：分成若干级别，例如绝密、机密、可信、公开等；主体的敏感度标记称为许可证级别，
  客体的敏感度标记称为密级
```
### 数据库的审计功能
```
审计功能指DBMS的审计模块在用户对数据库执行操作的同时把所有操作自动记录到系统的审计日志中；
任何系统的安全措施都不是完美无缺的，利用数据库的审计功能，DBA可以根据审计跟踪的信息，重现导致数据库
现有状况的一系列事件，找出非法存取数据的人、时间和内容等
```

## 第五章 数据库完整性
### 数据库的完整性
- 指数据的正确性和相容性
### 数据库的完整性与数据库的安全性的区别和联系
```
前者是为了防止数据库中存在不符合语义的数据，防止错误信息的输入和输出，造成无效操作和错误结果；
后者是保护数据库防止恶意的破坏和非法的存取；
总之，安全性措施的防范对象是非法用户和非法操作，完整性措施的防范对象是不合语义的数据
```
### 数据库的完整性约束条件
```
完整性约束条件是指数据库中的数据应该满足的语义约束条件，分为静态列级约束、静态元组约束、静态关系约束、
  动态列级约束、动态元祖约束、动态关系约束。
静态列级约束：是对一个列的取值域的说明，包括：数据类型约束、数据格式约束、取值集合的约束、空值约束等
静态元组约束：规定组成一个元组的各个列之间的约束关系，静态元组约束只局限在单个元组上
静态关系约束：在一个关系的各个元组之间或若干关系之间常常存在各种联系或约束，常见的有：
  实体完整性约束、参照完整性约束、函数依赖约束
动态列级约束：修改列定义或列值时应满足的约束条件，包括修改列定义时的约束、修改列值时的约束
动态元组约束：指修改某个元组的值时需要参照其旧值，并且新旧值之间需要满足某种约束条件
动态关系约束：是加在关系变化前后状态上的限制条件，例如事务一致性、原子性等
```
### 关系数据库管理系统（DBMS）的完整性控制机制具有哪些功能
- 定义功能：提供定义完整性约束条件机制
- 检查功能：检查用户发出的操作请求是否违背了完整性约束条件
- 违约反应：如果发现用户的操作请求使数据违背了完整性约束条件，则采取一定的动作来保证数据的完整性
### RDBMS在实现参照完整性时需考虑哪些方面
```
外码是否可以为空
删除被参照关系的元组时，考虑级联删除、受限删除或置空值删除
在参照关系中插入元组时，考虑受限插入或递归插入
修改关系中主码时，一般不用update语句，而是先删除该元组，再把具有新主码值的元组插入到关系中；
  如果允许修改主码，首先要保证主码的唯一性和非空，否则拒绝修改，还要区分是参照关系还是被参照关系
```
### 关系模式练习
```
职工（职工号，姓名，年龄，职务，工资，部门号）
部门（部门号，名称，经理名，电话）

定义每个模式的主码、定义参照完整性、定义职工年龄不得超过60岁：
create table dept
  (Deptno number(2),
   Dpetname varchar(10),
   Manager varchar(10),
   PhoneNumber char(12),
   constraint pk_sc primary key(Deptno)
  );
create table emp
  (Empno number(4),
   Ename varchar(10),
   Age number(2),
   constraint c1 check(Age <= 60),
   Job varchar(9),
   Sal number(7,2),
   Deptno number(2),
   constraint FK_DEPTNO foreign key(Deptno) references dept(Deptno)
  );
```
### 关系系统中，当操作违反实体完整性、参照完整性和用户定义的完整性约束条件时，一般如何分别进行处理？
```
对于违反实体完整性和用户定义完整性的操作一般都采用拒绝执行的方式进行处理；
而对于违反参照完整性的操作，并不是简单的拒绝执行，有时要根据应用语义执行一些附加的操作，以保证数据库的正确性
```

## 第六章 关系数据理论
### 术语和记号
```
X->Y,但Y不是X的子集，则称X->Y是非平凡的函数依赖；X->Y,且Y是X的子集，则称X->Y是平凡的函数依赖
若X->Y，则X叫做决定因素；若X->Y，Y->X，则记作X<-->Y
在R(U)中，如果X->Y,并且对于X的任何一个真子集X',都有X'->Y,则称Y对X完全函数依赖
若X->Y,但Y不完全函数依赖于X，则称Y对X部分函数依赖
第一范式：若关系模式R的每一个分量是不可再分的数据项，则关系模式R属于1NF
第二范式：若R∈1NF，且每一个非主属性完全函数依赖于码，则R∈2NF（即1NF消除了非主属性对码的部分函数依赖）
第三范式：若R中不存在这样的码X，属性组Y及非主属性Z使得X->Y,Y->Z,Y≠X成立，则称R∈3NF
BCNF：若R∈1NF，X->Y且Y不是X的子集，X含有码，则R∈BCNF
第四范式：若R∈1NF，若对于R的每个非平凡多值依赖X->->Y(Y不是X的子集，Z=U-X-Y不为空)，X都含有码，则称R∈4NF
```
### 下面哪些结论正确，哪些结论错误？对于错误的请给一个反例
```
任何一个二目关系是属于3NF的 √
  正确，因为关系模式中只有两个属性，所以无传递
任何一个二目关系是属于BCNF的 √
  正确，因为若X->Y，且Y不是X的子集时，每个决定因素都包含码，对于二目关系，决定因素必然包含码
```

## 第七章 数据库设计
### 数据库设计过程
```
需求分析->概念结构设计->逻辑结构设计->数据库物理设计->数据库实施->数据库运行和维护；
设计一个完善的数据库应用系统往往是上述六个阶段的不断反复

需求分析：准确了解与分析用户需求（包括数据与处理）
概念结构设计：通过对用户需求进行综合、归纳与抽象，形成一个独立于具体DBMS的概念模型
逻辑结构设计：将概念结构转换为某个DBMS所支持的数据模型，并对其进行优化
数据库物理设计：为逻辑数据模型选取一个最适合应用环境的物理结构（包括存储结构和存取方法）
数据库实施：设计人员运用DBMS提供的数据语言、工具及宿主语言，根据逻辑设计和物理设计的结果建立数据库，
  编制与调试应用程序，组织数据入库，并进行试运行
数据库运行和维护：在数据库系统运行过程中对其进行评价、调整与修改
```
### 数据库设计过程中形成的数据库模式
```
1.在概念设计阶段形成独立于机器特点，独立于各个DBMS产品的概念模式，就是E-R图
2.在逻辑设计阶段将E-R图转换成具体的数据库产品支持的数据模型，如关系模型，形成数据库逻辑模式，
  然后在基本表的基础上再建立必要的视图，形成数据的外模式
3.在物理设计阶段，根据DBMS特点和处理的需要，进行物理存储安排，建立索引，形成数据库内模式
```
### 数据库概念结构的特点和设计策略
```
特点：
（1）能真实、充分地反映现实世界，包括事物和事物之间的联系，能满足用户对数据的处理要求，是对现实世界的一个真实模型
（2）易于理解，可以用它和不熟悉计算机的用户交换意见，用户的积极参与是数据库设计成功的关键
（3）易于更改，当应用环境和应用要求改变时，容易对概念模型修改和扩充
（4）易于向关系、网状、层次等各种数据模型转换

设计策略：
（1）自顶向下，即首先定义全局概念结构的框架，然后逐步细化
（2）自底向上，即首先定义各局部应用的概念结构，然后将他们集成起来，得到全局概念结构
（3）逐步扩张，首先定义最重要的核心概念结构，然后向外扩充，以滚雪球的方式逐步生成其他概念结构，直至总体概念结构
（4）混合策略，即将自顶向下和自底向上相结合，用自顶向下策略设计一个全局概念结构的框架，以它为骨架
    集成由自底向上策略中设计的各局部概念结构
```









