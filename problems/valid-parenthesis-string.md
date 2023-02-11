
# 678. Valid Parenthesis String - 有效的括号字符串

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Stack-栈-blue.svg">   <img src="https://img.shields.io/badge/Greedy-贪心-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a string <code>s</code> containing only three types of characters: <code>&#39;(&#39;</code>, <code>&#39;)&#39;</code> and <code>&#39;*&#39;</code>, return <code>true</code> <em>if</em> <code>s</code> <em>is <strong>valid</strong></em>.</p>

<p>The following rules define a <strong>valid</strong> string:</p>

<ul>
	<li>Any left parenthesis <code>&#39;(&#39;</code> must have a corresponding right parenthesis <code>&#39;)&#39;</code>.</li>
	<li>Any right parenthesis <code>&#39;)&#39;</code> must have a corresponding left parenthesis <code>&#39;(&#39;</code>.</li>
	<li>Left parenthesis <code>&#39;(&#39;</code> must go before the corresponding right parenthesis <code>&#39;)&#39;</code>.</li>
	<li><code>&#39;*&#39;</code> could be treated as a single right parenthesis <code>&#39;)&#39;</code> or a single left parenthesis <code>&#39;(&#39;</code> or an empty string <code>&quot;&quot;</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> s = "()"
<strong>Output:</strong> true
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> s = "(*)"
<strong>Output:</strong> true
</pre><p><strong class="example">Example 3:</strong></p>
<pre><strong>Input:</strong> s = "(*))"
<strong>Output:</strong> true
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>s[i]</code> is <code>&#39;(&#39;</code>, <code>&#39;)&#39;</code> or <code>&#39;*&#39;</code>.</li>
</ul>


### ZH-CN:
<p>给定一个只包含三种字符的字符串：<code>（&nbsp;</code>，<code>）</code>&nbsp;和 <code>*</code>，写一个函数来检验这个字符串是否为有效字符串。有效字符串具有如下规则：</p>

<ol>
	<li>任何左括号 <code>(</code>&nbsp;必须有相应的右括号 <code>)</code>。</li>
	<li>任何右括号 <code>)</code>&nbsp;必须有相应的左括号 <code>(</code>&nbsp;。</li>
	<li>左括号 <code>(</code> 必须在对应的右括号之前 <code>)</code>。</li>
	<li><code>*</code>&nbsp;可以被视为单个右括号 <code>)</code>&nbsp;，或单个左括号 <code>(</code>&nbsp;，或一个空字符串。</li>
	<li>一个空字符串也被视为有效字符串。</li>
</ol>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> &quot;()&quot;
<strong>输出:</strong> True
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> &quot;(*)&quot;
<strong>输出:</strong> True
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> &quot;(*))&quot;
<strong>输出:</strong> True
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>字符串大小将在 [1，100] 范围内。</li>
</ol>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/valid-parenthesis-string/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/valid-parenthesis-string/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 9.4 MB | 2022/12/23 21:57 |

```cpp

class Solution {
public:
    vector<vector<int>> memo;
    bool dfs(const string& s, int idx, int cnt){
        if(cnt < 0) return false;
        if(idx >= s.length()){
            if(cnt == 0) return true;
            return false;
        }

        if(memo[idx][cnt] != -1) return memo[idx][cnt];

        if(s[idx] == '(') return memo[idx][cnt] = dfs(s, idx + 1, cnt + 1);
        else if(s[idx] == ')') return memo[idx][cnt] = dfs(s, idx + 1, cnt - 1);
        else{
            return memo[idx][cnt] = dfs(s, idx + 1, cnt + 1) || dfs(s, idx + 1, cnt - 1) || dfs(s, idx + 1, cnt);
        }
    }
    bool checkValidString(string s) {
        const int n = s.length();
        memo.resize(n, vector<int>(2 * n, -1));
        return dfs(s, 0, 0);
    }
};

```
## My Notes - 我的笔记


No notes

