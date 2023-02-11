
# 2287. Rearrange Characters to Make Target String - 重排字符形成目标字符串

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Counting-计数-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given two <strong>0-indexed</strong> strings <code>s</code> and <code>target</code>. You can take some letters from <code>s</code> and rearrange them to form new strings.</p>

<p>Return<em> the <strong>maximum</strong> number of copies of </em><code>target</code><em> that can be formed by taking letters from </em><code>s</code><em> and rearranging them.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;ilovecodingonleetcode&quot;, target = &quot;code&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong>
For the first copy of &quot;code&quot;, take the letters at indices 4, 5, 6, and 7.
For the second copy of &quot;code&quot;, take the letters at indices 17, 18, 19, and 20.
The strings that are formed are &quot;ecod&quot; and &quot;code&quot; which can both be rearranged into &quot;code&quot;.
We can make at most two copies of &quot;code&quot;, so we return 2.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abcba&quot;, target = &quot;abc&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong>
We can make one copy of &quot;abc&quot; by taking the letters at indices 0, 1, and 2.
We can make at most one copy of &quot;abc&quot;, so we return 1.
Note that while there is an extra &#39;a&#39; and &#39;b&#39; at indices 3 and 4, we cannot reuse the letter &#39;c&#39; at index 2, so we cannot make a second copy of &quot;abc&quot;.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;abbaccaddaeea&quot;, target = &quot;aaaaa&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong>
We can make one copy of &quot;aaaaa&quot; by taking the letters at indices 0, 3, 6, 9, and 12.
We can make at most one copy of &quot;aaaaa&quot;, so we return 1.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>1 &lt;= target.length &lt;= 10</code></li>
	<li><code>s</code> and <code>target</code> consist of lowercase English letters.</li>
</ul>


### ZH-CN:
<p>给你两个下标从 <strong>0</strong> 开始的字符串 <code>s</code> 和 <code>target</code> 。你可以从 <code>s</code> 取出一些字符并将其重排，得到若干新的字符串。</p>

<p>从 <code>s</code> 中取出字符并重新排列，返回可以形成 <code>target</code> 的 <strong>最大</strong> 副本数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>s = "ilovecodingonleetcode", target = "code"
<strong>输出：</strong>2
<strong>解释：</strong>
对于 "code" 的第 1 个副本，选取下标为 4 、5 、6 和 7 的字符。
对于 "code" 的第 2 个副本，选取下标为 17 、18 、19 和 20 的字符。
形成的字符串分别是 "ecod" 和 "code" ，都可以重排为 "code" 。
可以形成最多 2 个 "code" 的副本，所以返回 2 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>s = "abcba", target = "abc"
<strong>输出：</strong>1
<strong>解释：</strong>
选取下标为 0 、1 和 2 的字符，可以形成 "abc" 的 1 个副本。 
可以形成最多 1 个 "abc" 的副本，所以返回 1 。
注意，尽管下标 3 和 4 分别有额外的 'a' 和 'b' ，但不能重用下标 2 处的 'c' ，所以无法形成 "abc" 的第 2 个副本。
</pre>

<p><strong>示例 3：</strong></p>

<pre><strong>输入：</strong>s = "abbaccaddaeea", target = "aaaaa"
<strong>输出：</strong>1
<strong>解释：</strong>
选取下标为 0 、3 、6 、9 和 12 的字符，可以形成 "aaaaa" 的 1 个副本。
可以形成最多 1 个 "aaaaa" 的副本，所以返回 1 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 100</code></li>
	<li><code>1 &lt;= target.length &lt;= 10</code></li>
	<li><code>s</code> 和 <code>target</code> 由小写英文字母组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/rearrange-characters-to-make-target-string/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/rearrange-characters-to-make-target-string/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 6.1 MB | 2023/01/12 14:58 |

```cpp

class Solution {
public:
    int rearrangeCharacters(string s, string target) {
        vector<int> hm(26, 0);
        for(const char c: s) hm[c - 'a']++;

        int ans = 0;
        while(true){
            for(const char c: target){
                if(hm[c - 'a'] > 0) hm[c - 'a']--;
                else return ans;
            }
            ans++;
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

