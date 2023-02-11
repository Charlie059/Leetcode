
# 面试题 01.02. Check Permutation LCCI - 判定是否互为字符重排

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Sorting-排序-blue.svg">  


## Description - 题目描述

### EN:
<p>Given two strings,write a method to decide if one is a permutation of the other.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><code>s1</code> = &quot;abc&quot;, <code>s2</code> = &quot;bca&quot;
<strong>Output: </strong>true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><code>s1</code> = &quot;abc&quot;, <code>s2</code> = &quot;bad&quot;
<strong>Output: </strong>false
</pre>

<p><strong>Note:</strong></p>

<ol>
	<li><code>0 &lt;= len(s1) &lt;= 100 </code></li>
	<li><code>0 &lt;= len(s2) &lt;= 100</code></li>
</ol>


### ZH-CN:
<p>给定两个由小写字母组成的字符串 <code>s1</code> 和 <code>s2</code>，请编写一个程序，确定其中一个字符串的字符重新排列后，能否变成另一个字符串。</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入:</strong> <code>s1</code> = "abc", <code>s2</code> = "bca"
<strong>输出:</strong> true 
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入:</strong> <code>s1</code> = "abc", <code>s2</code> = "bad"
<strong>输出:</strong> false
</pre>

<p><strong>说明：</strong></p>

<ul>
	<li><code>0 &lt;= len(s1) &lt;= 100 </code></li>
	<li><code>0 &lt;= len(s2) &lt;= 100 </code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/check-permutation-lcci/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/check-permutation-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 5.8 MB | 2022/09/27 0:35 |

```cpp

class Solution {
public:
    bool CheckPermutation(string s1, string s2) {
        sort(s1.begin(), s1.end());
        sort(s2.begin(), s2.end());
        return s1 == s2;
    }
};

```
## My Notes - 我的笔记


No notes

