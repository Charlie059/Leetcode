
# 2027. Minimum Moves to Convert String - 转换字符串的最少操作次数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Greedy-贪心-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a string <code>s</code> consisting of <code>n</code> characters which are either <code>&#39;X&#39;</code> or <code>&#39;O&#39;</code>.</p>

<p>A <strong>move</strong> is defined as selecting <strong>three</strong> <strong>consecutive characters</strong> of <code>s</code> and converting them to <code>&#39;O&#39;</code>. Note that if a move is applied to the character <code>&#39;O&#39;</code>, it will stay the <strong>same</strong>.</p>

<p>Return <em>the <strong>minimum</strong> number of moves required so that all the characters of </em><code>s</code><em> are converted to </em><code>&#39;O&#39;</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;XXX&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> <u>XXX</u> -&gt; OOO
We select all the 3 characters and convert them in one move.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;XXOX&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> <u>XXO</u>X -&gt; O<u>OOX</u> -&gt; OOOO
We select the first 3 characters in the first move, and convert them to <code>&#39;O&#39;</code>.
Then we select the last 3 characters and convert them so that the final string contains all <code>&#39;O&#39;</code>s.</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;OOOO&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> There are no <code>&#39;X&#39;s</code> in <code>s</code> to convert.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s[i]</code> is either <code>&#39;X&#39;</code> or <code>&#39;O&#39;</code>.</li>
</ul>


### ZH-CN:
<p>给你一个字符串 <code>s</code> ，由 <code>n</code> 个字符组成，每个字符不是 <code>'X'</code> 就是 <code>'O'</code> 。</p>

<p>一次<strong> 操作</strong> 定义为从 <code>s</code> 中选出 <strong>三个连续字符 </strong>并将选中的每个字符都转换为 <code>'O'</code> 。注意，如果字符已经是 <code>'O'</code> ，只需要保持 <strong>不变</strong> 。</p>

<p>返回将 <code>s</code> 中所有字符均转换为 <code>'O'</code> 需要执行的&nbsp;<strong>最少</strong>&nbsp;操作次数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "XXX"
<strong>输出：</strong>1
<strong>解释：<em>XXX</em></strong> -&gt; OOO
一次操作，选中全部 3 个字符，并将它们转换为 <code>'O' 。</code>
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "XXOX"
<strong>输出：</strong>2
<strong>解释：<em>XXO</em></strong>X -&gt; O<em><strong>OOX</strong></em> -&gt; OOOO
第一次操作，选择前 3 个字符，并将这些字符转换为 <code>'O'</code> 。
然后，选中后 3 个字符，并执行转换。最终得到的字符串全由字符 <code>'O'</code> 组成。</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>s = "OOOO"
<strong>输出：</strong>0
<strong>解释：</strong>s 中不存在需要转换的 <code>'X' 。</code>
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>3 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s[i]</code> 为 <code>'X'</code> 或 <code>'O'</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/minimum-moves-to-convert-string/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/minimum-moves-to-convert-string/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 6.3 MB | 2022/12/27 11:53 |

```cpp

class Solution {
public:
    int minimumMoves(string s) {
        const int n = s.length();
        int ans = 0;
        int i;

        for(i = 0; i < n; i++){
            if(s[i] == 'O') continue;
            int j;
            for(j = i; j < n && j - i < 3; j++){}
            i = j - 1;
            ans++;
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

