<p><h1 align="center">宠物领养救助管理系统</h1></p>


<p align="center">
	<img src="https://img.shields.io/badge/jdk-1.8-orange.svg"/>
    <img src="https://img.shields.io/badge/spring-5.x-lightgrey.svg"/>
    <img src="https://img.shields.io/badge/springmvc-3.x-blue.svg"/>
    <img src="https://img.shields.io/badge/mybatis-5.x-yellow.svg"/>
</p>

## 简介


> 数据字典:
>
> **admin表格**：
>
> | 列名      | 数据类型     | 允许为空 | 说明                            |
> | --------- | ------------ | -------- | ------------------------------- |
> | id        | int          | 否       | 管理员的唯一标识符（自增）      |
> | adminName | varchar(20)  | 否       | 管理员的名字                    |
> | adminPwd  | varchar(20)  | 否       | 密码                            |
> | realName  | varchar(20)  | 否       | 真实的名字                      |
> | telephone | varchar(20)  | 否       | 电话                            |
> | Email     | varchar(20)  | 否       | 电子邮件                        |
> | birthday  | date         | 否       | 生日                            |
> | sex       | varchar(3)   | 否       | 性别                            |
> | pic       | varchar(100) | 是       | 管理员的图片（默认为'a10.png'） |
> | remark    | varchar(255) | 是       | 备注                            |
>
> **adopt_record表格**：
>
> | 列名      | 数据类型 | 允许为空 | 说明                                      |
> | --------- | -------- | -------- | ----------------------------------------- |
> | id        | int      | 否       | 领养记录的唯一标识符（自增）              |
> | user_id   | int      | 否       | 用户表id的外键                            |
> | pet_id    | int      | 否       | 宠物表id的外键                            |
> | adoptTime | date     | 否       | 领养时间                                  |
> | state     | int      | 是       | 是否同意被领养（0不同意，1审核中，2同意） |
>
> **answer表格**：
>
> | 列名       | 数据类型     | 允许为空 | 说明                     |
> | ---------- | ------------ | -------- | ------------------------ |
> | id         | int          | 否       | 回答的唯一标识符（自增） |
> | user_id    | int          | 是       | 用户表id外键             |
> | replay_id  | int          | 是       | 回复的id外键             |
> | comment_id | int          | 否       | 评论的id外键             |
> | answerTime | date         | 否       | 回答时间                 |
> | content    | varchar(255) | 否       | 回答的内容               |
>
> **apply表格**：
>
> | 列名      | 数据类型     | 允许为空 | 说明                     |
> | --------- | ------------ | -------- | ------------------------ |
> | id        | int          | 否       | 申请的唯一标识符（自增） |
> | name      | varchar(10)  | 否       | 姓名                     |
> | email     | varchar(20)  | 否       | 电子邮件                 |
> | age       | int          | 否       | 年龄                     |
> | telephone | varchar(12)  | 否       | 电话                     |
> | message   | varchar(100) | 否       | 申请信息                 |
> | applyTime | date         | 否       | 申请时间                 |
>
> **blog表格**：
>
> | 列名       | 数据类型     | 允许为空 | 说明                     |
> | ---------- | ------------ | -------- | ------------------------ |
> | id         | int          | 否       | 博客的唯一标识符（自增） |
> | actionTime | date         | 否       | 发布时间                 |
> | address    | varchar(100) | 否       | 地址                     |
> | peoples    | varchar(100) | 否       | 相关人物                 |
> | event      | varchar(100) | 否       | 事件                     |
> | title      | varchar(20)  | 否       | 标题                     |
>
> **comment表格**：
>
> | 列名        | 数据类型     | 允许为空 | 说明                     |
> | ----------- | ------------ | -------- | ------------------------ |
> | id          | int          | 否       | 评论的唯一标识符（自增） |
> | user_id     | int          | 是       | 用户表id外键             |
> | admin_id    | int          | 是       | 管理员表id外键           |
> | pet_id      | int          | 是       | 宠物表id外键             |
> | commentTime | date         | 否       | 评论时间                 |
> | content     | varchar(200) | 否       | 评论的内容               |
>
> **pet表格**：
>
> | 列名     | 数据类型     | 允许为空 | 说明                                              |
> | -------- | ------------ | -------- | ------------------------------------------------- |
> | id       | int          | 否       | 宠物的唯一标识符（自增）                          |
> | petName  | varchar(20)  | 否       | 宠物名字                                          |
> | petType  | varchar(20)  | 否       | 宠物类型                                          |
> | sex      | varchar(3)   | 否       | 性别                                              |
> | birthday | date         | 否       | 生日                                              |
> | pic      | varchar(100) | 否       | 头像                                              |
> | state    | int          | 否       | 宠物的状态（0未申请领养，1申请领养中，2已被领养） |
> | remark   | varchar(100) | 是       | 备注                                              |
>
> **users表格**：
>
> | 列名      | 数据类型     | 允许为空 | 说明                                   |
> | --------- | ------------ | -------- | -------------------------------------- |
> | id        | int          | 否       | 用户的唯一标识符（自增）               |
> | userName  | varchar(20)  | 否       | 用户名                                 |
> | password  | varchar(30)  | 否       | 密码                                   |
> | sex       | varchar(2)   | 是       | 性别                                   |
> | age       | int          | 是       | 年龄                                   |
> | telephone | varchar(20)  | 是       | 电话                                   |
> | Email     | varchar(30)  | 是       | 电子邮件                               |
> | address   | varchar(50)  | 是       | 地址                                   |
> | pic       | varchar(100) | 是       | 用户头像（默认为'/images/about1.jpg'） |
> | state     | int          | 是       | 是否有领养宠物的经历                   |
