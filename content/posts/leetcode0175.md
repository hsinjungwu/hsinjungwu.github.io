---
title: "LeetCode 0175－Combine Two Tables"
date: 2020-09-24T20:50:00+08:00
draft: false
dropCap: false
categories:
    - "LeetCode"

---

題目如下：

> Write a SQL query for a report that provides the following information for each person in the Person table, regardless if there is an address for each of those people:
>
> `FirstName, LastName, City, State`

<!--more-->

只求 pass 的解答。不過我很好奇當初我怎麼是選 `MySQL` 不是選 `MS SQL Server`

```sql
# Write your MySQL query statement below
SELECT p.FirstName, p.LastName, a.City, a.State
FROM Person p
LEFT JOIN Address a 
ON p.PersonId = a.PersonId
```
