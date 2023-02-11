
# 1758. Minimum Changes To Make Alternating Binary String - 生成交替二进制字符串的最少操作数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a string <code>s</code> consisting only of the characters <code>&#39;0&#39;</code> and <code>&#39;1&#39;</code>. In one operation, you can change any <code>&#39;0&#39;</code> to <code>&#39;1&#39;</code> or vice versa.</p>

<p>The string is called alternating if no two adjacent characters are equal. For example, the string <code>&quot;010&quot;</code> is alternating, while the string <code>&quot;0100&quot;</code> is not.</p>

<p>Return <em>the <strong>minimum</strong> number of operations needed to make</em> <code>s</code> <em>alternating</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;0100&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> If you change the last character to &#39;1&#39;, s will be &quot;0101&quot;, which is alternating.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;10&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> s is already alternating.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;1111&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> You need two operations to reach &quot;0101&quot; or &quot;1010&quot;.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s[i]</code> is either <code>&#39;0&#39;</code> or <code>&#39;1&#39;</code>.</li>
</ul>


### ZH-CN:
<p>给你一个仅由字符 <code>'0'</code> 和 <code>'1'</code> 组成的字符串 <code>s</code> 。一步操作中，你可以将任一 <code>'0'</code> 变成 <code>'1'</code> ，或者将 <code>'1'</code> 变成 <code>'0'</code> 。</p>

<p><strong>交替字符串</strong> 定义为：如果字符串中不存在相邻两个字符相等的情况，那么该字符串就是交替字符串。例如，字符串 <code>"010"</code> 是交替字符串，而字符串 <code>"0100"</code> 不是。</p>

<p>返回使 <code>s</code> 变成 <strong>交替字符串</strong> 所需的 <strong>最少</strong> 操作数。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = "0100"
<strong>输出：</strong>1
<strong>解释：</strong>如果将最后一个字符变为 '1' ，s 就变成 "0101" ，即符合交替字符串定义。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>s = "10"
<strong>输出：</strong>0
<strong>解释：</strong>s 已经是交替字符串。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>s = "1111"
<strong>输出：</strong>2
<strong>解释：</strong>需要 2 步操作得到 "0101" 或 "1010" 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s[i]</code> 是 <code>'0'</code> 或 <code>'1'</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/minimum-changes-to-make-alternating-binary-string/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/minimum-changes-to-make-alternating-binary-string/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 6.8 MB | 2022/11/28 13:05 |

```cpp

class Solution {
public:
    int minOperations(string s) {
        const int n = s.length();
        int l = 0, r = 0;
        bool s0 = 0, s1 = 1;
        for(int i = 0; i < n; i++){
            if(s0 != s[i] - '0') l++;
            if(s1 != s[i] - '0') r++;
            s0 = !s0;
            s1 = !s1;
        }

        
        
        return min(l, r);
    }
};

```
## My Notes - 我的笔记


No notes

