
# 1663. Smallest String With A Given Numeric Value - 具有给定数值的最小字符串

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Greedy-贪心-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>The <strong>numeric value</strong> of a <strong>lowercase character</strong> is defined as its position <code>(1-indexed)</code> in the alphabet, so the numeric value of <code>a</code> is <code>1</code>, the numeric value of <code>b</code> is <code>2</code>, the numeric value of <code>c</code> is <code>3</code>, and so on.</p>

<p>The <strong>numeric value</strong> of a <strong>string</strong> consisting of lowercase characters is defined as the sum of its characters&#39; numeric values. For example, the numeric value of the string <code>&quot;abe&quot;</code> is equal to <code>1 + 2 + 5 = 8</code>.</p>

<p>You are given two integers <code>n</code> and <code>k</code>. Return <em>the <strong>lexicographically smallest string</strong> with <strong>length</strong> equal to <code>n</code> and <strong>numeric value</strong> equal to <code>k</code>.</em></p>

<p>Note that a string <code>x</code> is lexicographically smaller than string <code>y</code> if <code>x</code> comes before <code>y</code> in dictionary order, that is, either <code>x</code> is a prefix of <code>y</code>, or if <code>i</code> is the first position such that <code>x[i] != y[i]</code>, then <code>x[i]</code> comes before <code>y[i]</code> in alphabetic order.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 3, k = 27
<strong>Output:</strong> &quot;aay&quot;
<strong>Explanation:</strong> The numeric value of the string is 1 + 1 + 25 = 27, and it is the smallest string with such a value and length equal to 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 5, k = 73
<strong>Output:</strong> &quot;aaszz&quot;
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>n &lt;= k &lt;= 26 * n</code></li>
</ul>


### ZH-CN:
<p><strong>小写字符 </strong>的 <strong>数值</strong> 是它在字母表中的位置（从 <code>1</code> 开始），因此 <code>a</code> 的数值为 <code>1</code> ，<code>b</code> 的数值为 <code>2</code> ，<code>c</code> 的数值为 <code>3</code> ，以此类推。</p>

<p>字符串由若干小写字符组成，<strong>字符串的数值</strong> 为各字符的数值之和。例如，字符串 <code>"abe"</code> 的数值等于 <code>1 + 2 + 5 = 8</code> 。</p>

<p>给你两个整数 <code>n</code> 和 <code>k</code> 。返回 <strong>长度</strong> 等于 <code>n</code> 且 <strong>数值</strong> 等于 <code>k</code> 的 <strong>字典序最小</strong> 的字符串。</p>

<p>注意，如果字符串 <code>x</code> 在字典排序中位于 <code>y</code> 之前，就认为 <code>x</code> 字典序比 <code>y</code> 小，有以下两种情况：</p>

<ul>
	<li><code>x</code> 是 <code>y</code> 的一个前缀；</li>
	<li>如果 <code>i</code> 是 <code>x[i] != y[i]</code> 的第一个位置，且 <code>x[i]</code> 在字母表中的位置比 <code>y[i]</code> 靠前。</li>
</ul>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 3, k = 27
<strong>输出：</strong>"aay"
<strong>解释：</strong>字符串的数值为 1 + 1 + 25 = 27，它是数值满足要求且长度等于 3 字典序最小的字符串。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 5, k = 73
<strong>输出：</strong>"aaszz"
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= n <= 10<sup>5</sup></code></li>
	<li><code>n <= k <= 26 * n</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/smallest-string-with-a-given-numeric-value/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/smallest-string-with-a-given-numeric-value/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 44 ms | 43.6 MB | 2023/01/25 16:45 |

```cpp

class Solution {
public:
    string getSmallestString(int n, int k) {
        k -= n;
        vector<int> vec(n, 1);

        for(int i = n - 1; i >= 0 && k > 0; i--){
            if(k >= 25){
                vec[i] += 25;
                k -= 25;
            }else if(k > 0){
                vec[i] += k;
                k = 0;
            }
        }

        string ans;
        for(int i = 0; i < n; i++) ans += vec[i] - 1 + 'a';
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

