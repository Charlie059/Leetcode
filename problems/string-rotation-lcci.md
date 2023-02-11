
# 面试题 01.09. String Rotation LCCI - 字符串轮转

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/String Matching-字符串匹配-blue.svg">  


## Description - 题目描述

### EN:
<p>Given two strings, <code>s1</code>&nbsp;and <code>s2</code>, write code to check if <code>s2</code> is a rotation of <code>s1</code> (e.g.,&quot;waterbottle&quot; is a rotation of&quot;erbottlewat&quot;).&nbsp;Can you use&nbsp;only one call to the method that&nbsp;checks if one word is a substring of another?</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>s1 = <span id="example-input-1-1">&quot;waterbottle&quot;</span>, s2 = <span id="example-input-1-2">&quot;</span>erbottlewat<span>&quot;</span>
<strong>Output: </strong><span id="example-output-1">True</span>
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>s1 = &quot;aa&quot;, s2 = &quot;aba&quot;
<strong>Output: </strong>False
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code><font face="monospace">0 &lt;= s1.length, s2.length &lt;=&nbsp;</font>100000</code></li>
</ol>


### ZH-CN:
<p>字符串轮转。给定两个字符串<code>s1</code>和<code>s2</code>，请编写代码检查<code>s2</code>是否为<code>s1</code>旋转而成（比如，<code>waterbottle</code>是<code>erbottlewat</code>旋转后的字符串）。</p>

<p><strong>示例1:</strong></p>

<pre><strong> 输入</strong>：s1 = &quot;waterbottle&quot;, s2 = &quot;erbottlewat&quot;
<strong> 输出</strong>：True
</pre>

<p><strong>示例2:</strong></p>

<pre><strong> 输入</strong>：s1 = &quot;aa&quot;, s2 = &quot;aba&quot;
<strong> 输出</strong>：False
</pre>

<ol>
</ol>

<p><strong>提示：</strong></p>

<ol>
	<li>字符串长度在[0, 100000]范围内。</li>
</ol>

<p><strong>说明:</strong></p>

<ol>
	<li>你能只调用一次检查子串的方法吗？</li>
</ol>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/string-rotation-lcci/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/string-rotation-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 8 ms | 7.6 MB | 2022/09/28 13:08 |

```cpp

class Solution {
public:
    bool isFlipedString(string s1, string s2) {
        if(s1.length() == 0 && s2.length() == 0) return true;
        if(s2.length() == 0) return false;
        s1 += s1;
        return string::npos != s1.find(s2);
    }
};

```
## My Notes - 我的笔记


No notes

