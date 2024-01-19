---
layout:       post
title:        "MyBatis写入数据库的编码问题"
# subtitle: ""
author:       "Peng"
# header-img: ""
header-style: text
catalog:      true
# lang: en
tags:
    - Java
    - Mybatis
    - Bug
---

### 问题描述
在使用MyBatis向MySQL数据库插入中文数据时，出现了字符编码问题，导致中文字符被转换为问号。问题表现为在数据库中无法正确保存中文字符，而直接在数据库中插入却没有问题。

### 解决方案

**在MyBatis配置文件中添加字符编码参数：**

   在`mybatis-config.xml`文件的数据库连接配置中，确保添加了`useUnicode=true&amp;characterEncoding=utf8`参数。

   ```xml
<dataSource type="POOLED">
    <!-- 其他属性 -->
    <property name="url" value="jdbc:mysql:///db1?useSSL=false&amp;useServerPrepStmts=true&amp;useUnicode=true&amp;characterEncoding=utf8"/>
    <!-- 其他属性 -->
</dataSource>
   ```