
# 28. Find the Index of the First Occurrence in a String - 找出字符串中第一个匹配项的下标

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Two Pointers-双指针-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/String Matching-字符串匹配-blue.svg">  


## Description - 题目描述

### EN:
<p>Given two strings <code>needle</code> and <code>haystack</code>, return the index of the first occurrence of <code>needle</code> in <code>haystack</code>, or <code>-1</code> if <code>needle</code> is not part of <code>haystack</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> haystack = &quot;sadbutsad&quot;, needle = &quot;sad&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> &quot;sad&quot; occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> haystack = &quot;leetcode&quot;, needle = &quot;leeto&quot;
<strong>Output:</strong> -1
<strong>Explanation:</strong> &quot;leeto&quot; did not occur in &quot;leetcode&quot;, so we return -1.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= haystack.length, needle.length &lt;= 10<sup>4</sup></code></li>
	<li><code>haystack</code> and <code>needle</code> consist of only lowercase English characters.</li>
</ul>


### ZH-CN:
<p>给你两个字符串&nbsp;<code>haystack</code> 和 <code>needle</code> ，请你在 <code>haystack</code> 字符串中找出 <code>needle</code> 字符串的第一个匹配项的下标（下标从 0 开始）。如果&nbsp;<code>needle</code> 不是 <code>haystack</code> 的一部分，则返回&nbsp; <code>-1</code><strong> </strong>。</p>

<p>&nbsp;</p>

<p><strong class="example">示例 1：</strong></p>

<pre>
<strong>输入：</strong>haystack = "sadbutsad", needle = "sad"
<strong>输出：</strong>0
<strong>解释：</strong>"sad" 在下标 0 和 6 处匹配。
第一个匹配项的下标是 0 ，所以返回 0 。
</pre>

<p><strong class="example">示例 2：</strong></p>

<pre>
<strong>输入：</strong>haystack = "leetcode", needle = "leeto"
<strong>输出：</strong>-1
<strong>解释：</strong>"leeto" 没有在 "leetcode" 中出现，所以返回 -1 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= haystack.length, needle.length &lt;= 10<sup>4</sup></code></li>
	<li><code>haystack</code> 和 <code>needle</code> 仅由小写英文字符组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 6.1 MB | 2023/01/24 15:06 |

```cpp

class Solution {
public:
    vector<int> KMPBuild(const string &p){
        const int m = p.length();
        vector<int> next{0, 0};
        for(int i = 1, j = 0; i < m; i++){
            while(j > 0 && p[i] != p[j]) j = next[j];
            if(p[i] == p[j]) j++;
            next.emplace_back(j);
        }
        return next;
    }

    vector<int> KMPMatch(const string & s, const string& p){
        vector<int> next(KMPBuild(p));
        vector<int> ans;

        const int n = s.length();
        const int m = p.length();
        for(int i = 0, j = 0; i < n; i++){
            while(j > 0 && s[i] != p[j]) j = next[j];
            if(s[i] == p[j]) j++;
            if(j == m){
                ans.emplace_back(i - m + 1);
                j = next[j];
            }
        }
        return ans;
    }

    int strStr(string haystack, string needle) {
        vector<int> ans = KMPMatch(haystack, needle);
        if(ans.size() == 0) return -1;
        else return ans[0];
    }
};

```
## My Notes - 我的笔记


No notes

