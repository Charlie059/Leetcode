
# 584. Find Customer Referee - 寻找用户推荐人

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Database-数据库-blue.svg">  


## Description - 题目描述

### EN:
<p>Table: <code>Customer</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+
id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.
</pre>

<p>&nbsp;</p>

<p>Write an SQL query to report the names of the customer that are <strong>not referred by</strong> the customer with <code>id = 2</code>.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The query result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Customer table:
+----+------+------------+
| id | name | referee_id |
+----+------+------------+
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |
+----+------+------------+
<strong>Output:</strong> 
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+
</pre>


### ZH-CN:
<p>给定表 <code>customer</code> ，里面保存了所有客户信息和他们的推荐人。</p>

<pre>
+------+------+-----------+
| id   | name | referee_id|
+------+------+-----------+
|    1 | Will |      NULL |
|    2 | Jane |      NULL |
|    3 | Alex |         2 |
|    4 | Bill |      NULL |
|    5 | Zack |         1 |
|    6 | Mark |         2 |
+------+------+-----------+
</pre>

<p>写一个查询语句，返回一个客户列表，列表中客户的推荐人的编号都 <strong>不是 </strong>2。</p>

<p>对于上面的示例数据，结果为：</p>

<pre>
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+
</pre>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/find-customer-referee/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/find-customer-referee/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| mysql  | 438 ms | 0 B | 2023/01/08 20:35 |

```mysql

# Write your MySQL query statement below
SELECT name
FROM Customer as c
WHERE c.referee_id != 2 OR c.referee_id IS NULL
; 

```
## My Notes - 我的笔记


No notes

