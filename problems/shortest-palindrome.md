
# 214. Shortest Palindrome - 最短回文串

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/String Matching-字符串匹配-blue.svg">   <img src="https://img.shields.io/badge/Hash Function-哈希函数-blue.svg">   <img src="https://img.shields.io/badge/Rolling Hash-滚动哈希-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a string <code>s</code>. You can convert <code>s</code> to a <span data-keyword="palindrome-string">palindrome</span> by adding characters in front of it.</p>

<p>Return <em>the shortest palindrome you can find by performing this transformation</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> s = "aacecaaa"
<strong>Output:</strong> "aaacecaaa"
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> s = "abcd"
<strong>Output:</strong> "dcbabcd"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= s.length &lt;= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> consists of lowercase English letters only.</li>
</ul>


### ZH-CN:
<p>给定一个字符串 <em><strong>s</strong></em>，你可以通过在字符串前面添加字符将其转换为回文串。找到并返回可以用这种方式转换的最短回文串。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>s = "aacecaaa"
<strong>输出：</strong>"aaacecaaa"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>s = "abcd"
<strong>输出：</strong>"dcbabcd"
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= s.length <= 5 * 10<sup>4</sup></code></li>
	<li><code>s</code> 仅由小写英文字母组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/shortest-palindrome/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/shortest-palindrome/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 8.5 MB | 2022/07/27 15:56 |

```cpp

class Solution {
public:
    int KMPBuild(const string &p){
        const int m = p.length();
        vector<int> next{0, 0};
        for(int i = 1, j = 0; i < m; ++i){
            while(j > 0 && p[i] != p[j]) j = next[j];

            if(p[i] == p[j]){
                ++j;
            }
            next.push_back(j);
        }
        return next[next.size() - 1];
    }

    string shortestPalindrome(string s) {
        if(s == ""){
            return "";
        }
        string reverse_str(s.rbegin(), s.rend());
        string pattern = s + '#' + reverse_str;
        int max_len = KMPBuild(pattern);
        return reverse_str.substr(0, reverse_str.size() - max_len) + s;
    }
};

```
## My Notes - 我的笔记


No notes

