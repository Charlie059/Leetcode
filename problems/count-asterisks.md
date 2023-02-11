
# 2315. Count Asterisks - 统计星号

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a string <code>s</code>, where every <strong>two</strong> consecutive vertical bars <code>&#39;|&#39;</code> are grouped into a <strong>pair</strong>. In other words, the 1<sup>st</sup> and 2<sup>nd</sup> <code>&#39;|&#39;</code> make a pair, the 3<sup>rd</sup> and 4<sup>th</sup> <code>&#39;|&#39;</code> make a pair, and so forth.</p>

<p>Return <em>the number of </em><code>&#39;*&#39;</code><em> in </em><code>s</code><em>, <strong>excluding</strong> the </em><code>&#39;*&#39;</code><em> between each pair of </em><code>&#39;|&#39;</code>.</p>

<p><strong>Note</strong> that each <code>&#39;|&#39;</code> will belong to <strong>exactly</strong> one pair.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;l|*e*et|c**o|*de|&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> The considered characters are underlined: &quot;<u>l</u>|*e*et|<u>c**o</u>|*de|&quot;.
The characters between the first and second &#39;|&#39; are excluded from the answer.
Also, the characters between the third and fourth &#39;|&#39; are excluded from the answer.
There are 2 asterisks considered. Therefore, we return 2.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;iamprogrammer&quot;
<strong>Output:</strong> 0
<strong>Explanation:</strong> In this example, there are no asterisks in s. Therefore, we return 0.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;yo|uar|e**|b|e***au|tifu|l&quot;
<strong>Output:</strong> 5
<strong>Explanation:</strong> The considered characters are underlined: &quot;<u>yo</u>|uar|<u>e**</u>|b|<u>e***au</u>|tifu|<u>l</u>&quot;. There are 5 asterisks considered. Therefore, we return 5.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s</code> consists of lowercase English letters, vertical bars <code>&#39;|&#39;</code>, and asterisks <code>&#39;*&#39;</code>.</li>
	<li><code>s</code> contains an <strong>even</strong> number of vertical bars <code>&#39;|&#39;</code>.</li>
</ul>


### ZH-CN:
<p>给你一个字符串&nbsp;<code>s</code>&nbsp;，每&nbsp;<strong>两个</strong>&nbsp;连续竖线&nbsp;<code>'|'</code>&nbsp;为 <strong>一对</strong>&nbsp;。换言之，第一个和第二个&nbsp;<code>'|'</code>&nbsp;为一对，第三个和第四个&nbsp;<code>'|'</code>&nbsp;为一对，以此类推。</p>

<p>请你返回 <strong>不在</strong> 竖线对之间，<code>s</code>&nbsp;中&nbsp;<code>'*'</code>&nbsp;的数目。</p>

<p><strong>注意</strong>，每个竖线&nbsp;<code>'|'</code>&nbsp;都会 <strong>恰好</strong>&nbsp;属于一个对。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>s = "l|*e*et|c**o|*de|"
<b>输出：</b>2
<b>解释：</b>不在竖线对之间的字符加粗加斜体后，得到字符串："<strong><em>l</em></strong>|*e*et|<strong><em>c**o</em></strong>|*de|" 。
第一和第二条竖线 '|' 之间的字符不计入答案。
同时，第三条和第四条竖线 '|' 之间的字符也不计入答案。
不在竖线对之间总共有 2 个星号，所以我们返回 2 。</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>s = "iamprogrammer"
<b>输出：</b>0
<b>解释：</b>在这个例子中，s 中没有星号。所以返回 0 。
</pre>

<p><strong>示例 3：</strong></p>

<pre><b>输入：</b>s = "yo|uar|e**|b|e***au|tifu|l"
<b>输出：</b>5
<b>解释：</b>需要考虑的字符加粗加斜体后："<strong><em>yo</em></strong>|uar|<strong><em>e**</em></strong>|b|<strong><em>e***au</em></strong>|tifu|<strong><em>l</em></strong>" 。不在竖线对之间总共有 5 个星号。所以我们返回 5 。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 1000</code></li>
	<li><code>s</code>&nbsp;只包含小写英文字母，竖线&nbsp;<code>'|'</code>&nbsp;和星号&nbsp;<code>'*'</code>&nbsp;。</li>
	<li><code>s</code>&nbsp;包含 <strong>偶数</strong>&nbsp;个竖线&nbsp;<code>'|'</code> 。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/count-asterisks/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/count-asterisks/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 6.3 MB | 2023/01/28 22:37 |

```cpp

class Solution {
public:
    int countAsterisks(string s) {
       const int n = s.length(); 
        bool meet = false;
        int ans = 0, tmp = 0;
        for(const char& c: s){
            if(c == '|'){
                meet ? meet = false : meet = true; 
                if(!meet) ans -= tmp;
                tmp = 0;
            }
            if(c == '*'){
                tmp++;
                ans++; 
            }
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

