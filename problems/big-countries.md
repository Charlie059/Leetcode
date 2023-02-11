
# 595. Big Countries - 大的国家

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Database-数据库-blue.svg">  


## Description - 题目描述

### EN:
<p>Table: <code>World</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | int     |
+-------------+---------+
name is the primary key column for this table.
Each row of this table gives information about the name of a country, the continent to which it belongs, its area, the population, and its GDP value.
</pre>

<p>&nbsp;</p>

<p>A country is <strong>big</strong> if:</p>

<ul>
	<li>it has an area of at least&nbsp;three million (i.e., <code>3000000 km<sup>2</sup></code>), or</li>
	<li>it has a population of at least&nbsp;twenty-five million (i.e., <code>25000000</code>).</li>
</ul>

<p>Write an SQL query to report the name, population, and area of the <strong>big countries</strong>.</p>

<p>Return the result table in <strong>any order</strong>.</p>

<p>The query result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
World table:
+-------------+-----------+---------+------------+--------------+
| name        | continent | area    | population | gdp          |
+-------------+-----------+---------+------------+--------------+
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |
+-------------+-----------+---------+------------+--------------+
<strong>Output:</strong> 
+-------------+------------+---------+
| name        | population | area    |
+-------------+------------+---------+
| Afghanistan | 25500100   | 652230  |
| Algeria     | 37100000   | 2381741 |
+-------------+------------+---------+
</pre>


### ZH-CN:
<p><code>World</code> 表：</p>

<div class="top-view__1vxA">
<div class="original__bRMd">
<div>
<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | int     |
+-------------+---------+
name 是这张表的主键。
这张表的每一行提供：国家名称、所属大陆、面积、人口和 GDP 值。
</pre>

<p>&nbsp;</p>

<p>如果一个国家满足下述两个条件之一，则认为该国是 <strong>大国</strong> ：</p>

<ul>
	<li>面积至少为 300 万平方公里（即，<code>3000000 km<sup>2</sup></code>），或者</li>
	<li>人口至少为 2500 万（即 <code>25000000</code>）</li>
</ul>

<p>编写一个 SQL 查询以报告 <strong>大国</strong> 的国家名称、人口和面积。</p>

<p>按 <strong>任意顺序</strong> 返回结果表。</p>

<p>查询结果格式如下例所示。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre>
<strong>输入：</strong>
World 表：
+-------------+-----------+---------+------------+--------------+
| name        | continent | area    | population | gdp          |
+-------------+-----------+---------+------------+--------------+
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |
+-------------+-----------+---------+------------+--------------+
<strong>输出：</strong>
+-------------+------------+---------+
| name        | population | area    |
+-------------+------------+---------+
| Afghanistan | 25500100   | 652230  |
| Algeria     | 37100000   | 2381741 |
+-------------+------------+---------+
</pre>
</div>
</div>
</div>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/big-countries/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/big-countries/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| mysql  | 231 ms | 0 B | 2023/01/07 13:03 |

```mysql

# Write your MySQL query statement below
SELECT name, population, area FROM World WHERE area >= 3000000 OR population >= 25000000

```
## My Notes - 我的笔记


No notes

