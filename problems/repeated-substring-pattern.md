
# 459. Repeated Substring Pattern - 重复的子字符串

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/String Matching-字符串匹配-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a string <code>s</code>, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abab&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> It is the substring &quot;ab&quot; twice.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;aba&quot;
<strong>Output:</strong> false
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcabcabcabc&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> It is the substring &quot;abc&quot; four times or the substring &quot;abcabc&quot; twice.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code> consists of lowercase English letters.</li>
</ul>


### ZH-CN:
<p>给定一个非空的字符串<meta charset="UTF-8" />&nbsp;<code>s</code>&nbsp;，检查是否可以通过由它的一个子串重复多次构成。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> s = "abab"
<strong>输出:</strong> true
<strong>解释:</strong> 可由子串 "ab" 重复两次构成。
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> s = "aba"
<strong>输出:</strong> false
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入:</strong> s = "abcabcabcabc"
<strong>输出:</strong> true
<strong>解释:</strong> 可由子串 "abc" 重复四次构成。 (或子串 "abcabc" 重复两次构成。)
</pre>

<p>&nbsp;</p>

<p><b>提示：</b></p>

<p><meta charset="UTF-8" /></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>4</sup></code></li>
	<li><code>s</code>&nbsp;由小写英文字母组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/repeated-substring-pattern/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/repeated-substring-pattern/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 32 ms | 21.8 MB | 2022/07/27 10:32 |

```cpp

class Solution {
public:

    vector<int> KMPBuild(const string & s){
        vector<int> next{0, 0};
        const int n = s.length();

        for(int i = 1, j = 0; i < n; i++){
            while(j > 0 && s[i] != s[j]) j = next[j];
            if(s[i] == s[j]) j++;
            next.emplace_back(j);
        }
        return next;
    }

    bool KMPMatch(const string & s, const string & p){
        vector<int> next(KMPBuild(p));
        const int n = s.length();
        const int m = p.length();

        for(int i = 0, j = 0; i < n; i++){
            while(j > 0 && s[i] != p[j]) j = next[j];
            if(s[i] == p[j]) j++;
            if(j == m) return true;
        }

        return false;
    }
    bool repeatedSubstringPattern(string s) {
        string str = s + s;
        string t =  str.substr(1, str.length() - 2);
        return KMPMatch(t, s);
    }
};

//https://leetcode.cn/problems/repeated-substring-pattern/solution/jian-dan-ming-liao-guan-yu-javaliang-xing-dai-ma-s/

```
## My Notes - 我的笔记


No notes

