
# 686. Repeated String Match - 重复叠加字符串匹配

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/String Matching-字符串匹配-blue.svg">  


## Description - 题目描述

### EN:
<p>Given two strings <code>a</code> and <code>b</code>, return <em>the minimum number of times you should repeat string </em><code>a</code><em> so that string</em> <code>b</code> <em>is a substring of it</em>. If it is impossible for <code>b</code>​​​​​​ to be a substring of <code>a</code> after repeating it, return <code>-1</code>.</p>

<p><strong>Notice:</strong> string <code>&quot;abc&quot;</code> repeated 0 times is <code>&quot;&quot;</code>, repeated 1 time is <code>&quot;abc&quot;</code> and repeated 2 times is <code>&quot;abcabc&quot;</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> a = &quot;abcd&quot;, b = &quot;cdabcdab&quot;
<strong>Output:</strong> 3
<strong>Explanation:</strong> We return 3 because by repeating a three times &quot;ab<strong>cdabcdab</strong>cd&quot;, b is a substring of it.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> a = &quot;a&quot;, b = &quot;aa&quot;
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= a.length, b.length &lt;= 10<sup>4</sup></code></li>
	<li><code>a</code> and <code>b</code> consist of lowercase English letters.</li>
</ul>


### ZH-CN:
<p>给定两个字符串&nbsp;<code>a</code> 和 <code>b</code>，寻找重复叠加字符串 <code>a</code> 的最小次数，使得字符串 <code>b</code> 成为叠加后的字符串 <code>a</code> 的子串，如果不存在则返回 <code>-1</code>。</p>

<p><strong>注意：</strong>字符串 <code>&quot;abc&quot;</code>&nbsp;重复叠加 0 次是 <code>&quot;&quot;</code>，重复叠加 1 次是&nbsp;<code>&quot;abc&quot;</code>，重复叠加 2 次是&nbsp;<code>&quot;abcabc&quot;</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>a = &quot;abcd&quot;, b = &quot;cdabcdab&quot;
<strong>输出：</strong>3
<strong>解释：</strong>a 重复叠加三遍后为 &quot;ab<strong>cdabcdab</strong>cd&quot;, 此时 b 是其子串。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>a = &quot;a&quot;, b = &quot;aa&quot;
<strong>输出：</strong>2
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>a = &quot;a&quot;, b = &quot;a&quot;
<strong>输出：</strong>1
</pre>

<p><strong>示例 4：</strong></p>

<pre><strong>输入：</strong>a = &quot;abc&quot;, b = &quot;wxyz&quot;
<strong>输出：</strong>-1
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= a.length &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= b.length &lt;= 10<sup>4</sup></code></li>
	<li><code>a</code> 和 <code>b</code> 由小写英文字母组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/repeated-string-match/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/repeated-string-match/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 8.4 MB | 2022/07/27 0:10 |

```cpp

class Solution {
public:
    vector<int> KMPBuild(string & a){
        vector<int> next {0, 0};
        const int n = a.length();

        for(int i = 1, j = 0; i < n; i++){
            while(j > 0 && a[i] != a[j]) j = next[j];
            if(a[i] == a[j]) j++;
            next.emplace_back(j);
        }
        return next;
    }


    bool KMPMatch(string & a, string & b){
        vector<int> next (KMPBuild(b));
        vector<int> ans;
        const int n = a.length();
        const int m = b.length();

        for(int i = 0, j = 0; i < n; i++){
            while(j > 0 && a[i] != b[j]) j = next[j];
            if(a[i] == b[j]) j++;
            if(j == m){
                return true;
            }
        }
        return false;;
    }

    int repeatedStringMatch(string a, string b) {
        const int n = a.length();
        const int m = b.length();
        int cnt = 1;
        string s = a;
        if(n < m){
            for(;;){
                if(a.length() >= m) break;
                a += s;
            }
        }
        while(true){
            if(a.length() > 2 * n + m) break;
            if(KMPMatch(a, b)){
                return a.length() / n;
            }
            cnt++;
            a += s;
        }
        return -1;
    }
    //@John Jiang 因为一个完整的B可能首部用到A的一部分，尾部用到A的一部分，像这样A'[AA....AA]A' , [ ] 内必然<=B的长度，故总长<=2*A+B
};

```
## My Notes - 我的笔记


No notes

