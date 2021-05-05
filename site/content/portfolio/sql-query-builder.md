---
title: "SQL Query Builder"
date: 2018-09-13T12:00:00-07:00
type: portfolio
image: "images/projects/sql-query-builder.jpg"
category: ["C# Library"]
github_url: https://github.com/CarsonTolleshaug/SqlQueryBuilder
---

`SqlQueryBuilder` is a .NET nuget package library for writing SQL statements 
in **fluent-style** native C# syntax. Ideally, it would be used in conjunction 
with an ORM like [Dapper](https://www.learndapper.com/) that takes strings for 
a sql query.

The syntax looks like the following:

```C#
string query = new Select("*").From("MyTable").Where("Id = 14").ToString();
```

---

*This project is not being actively worked on.*