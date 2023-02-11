
# 1750. Minimum Length of String After Deleting Similar Ends - 删除字符串两端相同字符后的最短长度

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Two Pointers-双指针-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a string <code>s</code> consisting only of characters <code>&#39;a&#39;</code>, <code>&#39;b&#39;</code>, and <code>&#39;c&#39;</code>. You are asked to apply the following algorithm on the string any number of times:</p>

<ol>
	<li>Pick a <strong>non-empty</strong> prefix from the string <code>s</code> where all the characters in the prefix are equal.</li>
	<li>Pick a <strong>non-empty</strong> suffix from the string <code>s</code> where all the characters in this suffix are equal.</li>
	<li>The prefix and the suffix should not intersect at any index.</li>
	<li>The characters from the prefix and suffix must be the same.</li>
	<li>Delete both the prefix and the suffix.</li>
</ol>

<p>Return <em>the <strong>minimum length</strong> of </em><code>s</code> <em>after performing the above operation any number of times (possibly zero times)</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;ca&quot;
<strong>Output:</strong> 2
<strong>Explanation: </strong>You can&#39;t remove any characters, so the string stays as is.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;cabaabac&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> An optimal sequence of operations is:
- Take prefix = &quot;c&quot; and suffix = &quot;c&quot; and remove them, s = &quot;abaaba&quot;.
- Take prefix = &quot;a&quot; and suffix = &quot;a&quot; and remove them, s = &quot;baab&quot;.
- Take prefix = &quot;b&quot; and suffix = &quot;b&quot; and remove them, s = &quot;aa&quot;.
- Take prefix = &quot;a&quot; and suffix = &quot;a&quot; and remove them, s = &quot;&quot;.</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aabccabba&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> An optimal sequence of operations is:
- Take prefix = &quot;aa&quot; and suffix = &quot;a&quot; and remove them, s = &quot;bccabb&quot;.
- Take prefix = &quot;b&quot; and suffix = &quot;bb&quot; and remove them, s = &quot;cca&quot;.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>s</code> only consists of characters <code>&#39;a&#39;</code>, <code>&#39;b&#39;</code>, and <code>&#39;c&#39;</code>.</li>
</ul>


### ZH-CN:
<p>给你一个只包含字符 <code>'a'</code>，<code>'b'</code> 和 <code>'c'</code> 的字符串 <code>s</code> ，你可以执行下面这个操作（5 个步骤）任意次：</p>

<ol>
	<li>选择字符串 <code>s</code> 一个 <strong>非空</strong> 的前缀，这个前缀的所有字符都相同。</li>
	<li>选择字符串 <code>s</code> 一个 <strong>非空</strong> 的后缀，这个后缀的所有字符都相同。</li>
	<li>前缀和后缀在字符串中任意位置都不能有交集。</li>
	<li>前缀和后缀包含的所有字符都要相同。</li>
	<li>同时删除前缀和后缀。</li>
</ol>

<p>请你返回对字符串 <code>s</code> 执行上面操作任意次以后（可能 0 次），能得到的 <strong>最短长度</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>s = "ca"
<b>输出：</b>2
<strong>解释：</strong>你没法删除任何一个字符，所以字符串长度仍然保持不变。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>s = "cabaabac"
<b>输出：</b>0
<b>解释：</b>最优操作序列为：
- 选择前缀 "c" 和后缀 "c" 并删除它们，得到 s = "abaaba" 。
- 选择前缀 "a" 和后缀 "a" 并删除它们，得到 s = "baab" 。
- 选择前缀 "b" 和后缀 "b" 并删除它们，得到 s = "aa" 。
- 选择前缀 "a" 和后缀 "a" 并删除它们，得到 s = "" 。</pre>

<p><strong>示例 3：</strong></p>

<pre>
<b>输入：</b>s = "aabccabba"
<b>输出：</b>3
<b>解释：</b>最优操作序列为：
- 选择前缀 "aa" 和后缀 "a" 并删除它们，得到 s = "bccabb" 。
- 选择前缀 "b" 和后缀 "bb" 并删除它们，得到 s = "cca" 。
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= s.length <= 10<sup>5</sup></code></li>
	<li><code>s</code> 只包含字符 <code>'a'</code>，<code>'b'</code> 和 <code>'c'</code> 。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/minimum-length-of-string-after-deleting-similar-ends/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/minimum-length-of-string-after-deleting-similar-ends/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 16 ms | 12.5 MB | 2022/12/27 12:32 |

```cpp

class Solution {
public:
    int minimumLength(string s) {
        const int n = s.length();
        int i = 0, j = n - 1;

        while(i < j){
            if(s[i] == s[j]){
                char c = s[i];
                while(i <= j && s[i] == c) i++;
                while(i <= j && s[j] == c) j--;
            }else break;
        }

        return j - i + 1;
    }
};

```
## My Notes - 我的笔记


No notes

