
# 1037. Valid Boomerang - 有效的回旋镖

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Geometry-几何-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an array <code>points</code> where <code>points[i] = [x<sub>i</sub>, y<sub>i</sub>]</code> represents a point on the <strong>X-Y</strong> plane, return <code>true</code> <em>if these points are a <strong>boomerang</strong></em>.</p>

<p>A <strong>boomerang</strong> is a set of three points that are <strong>all distinct</strong> and <strong>not in a straight line</strong>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> points = [[1,1],[2,3],[3,2]]
<strong>Output:</strong> true
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> points = [[1,1],[2,2],[3,3]]
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>points.length == 3</code></li>
	<li><code>points[i].length == 2</code></li>
	<li><code>0 &lt;= x<sub>i</sub>, y<sub>i</sub> &lt;= 100</code></li>
</ul>


### ZH-CN:
<p>给定一个数组<meta charset="UTF-8" />&nbsp;<code>points</code>&nbsp;，其中<meta charset="UTF-8" />&nbsp;<code>points[i] = [x<sub>i</sub>, y<sub>i</sub>]</code>&nbsp;表示 <strong>X-Y</strong> 平面上的一个点，<em>如果这些点构成一个&nbsp;</em><strong>回旋镖</strong>&nbsp;则返回&nbsp;<code>true</code>&nbsp;。</p>

<p><strong>回旋镖</strong>&nbsp;定义为一组三个点，这些点&nbsp;<strong>各不相同</strong>&nbsp;且&nbsp;<strong>不在一条直线上</strong>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>points = [[1,1],[2,3],[3,2]]
<strong>输出：</strong>true
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>points = [[1,1],[2,2],[3,3]]
<strong>输出：</strong>false</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>
<meta charset="UTF-8" />

<ul>
	<li><code>points.length == 3</code></li>
	<li><code>points[i].length == 2</code></li>
	<li><code>0 &lt;= x<sub>i</sub>, y<sub>i</sub>&nbsp;&lt;= 100</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/valid-boomerang/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/valid-boomerang/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 10 MB | 2022/06/07 17:16 |

```cpp

class Solution {
public:
    bool isBoomerang(vector<vector<int>>& points) {
        int k1 = (points[1][1] - points[0][1]) * (points[2][0] - points[0][0]);
        int k2 = (points[2][1] - points[0][1]) * (points[1][0] - points[0][0]);
        return (k1 != k2);
    }
};

```
## My Notes - 我的笔记


No notes

