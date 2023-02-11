
# 777. Swap Adjacent in LR String - 在LR字符串中交换相邻字符

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Two Pointers-双指针-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>In a string composed of <code>&#39;L&#39;</code>, <code>&#39;R&#39;</code>, and <code>&#39;X&#39;</code> characters, like <code>&quot;RXXLRXRXL&quot;</code>, a move consists of either replacing one occurrence of <code>&quot;XL&quot;</code> with <code>&quot;LX&quot;</code>, or replacing one occurrence of <code>&quot;RX&quot;</code> with <code>&quot;XR&quot;</code>. Given the starting string <code>start</code> and the ending string <code>end</code>, return <code>True</code> if and only if there exists a sequence of moves to transform one string to the other.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> start = &quot;RXXLRXRXL&quot;, end = &quot;XRLXXRRLX&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> We can transform start to end following these steps:
RXXLRXRXL -&gt;
XRXLRXRXL -&gt;
XRLXRXRXL -&gt;
XRLXXRRXL -&gt;
XRLXXRRLX
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> start = &quot;X&quot;, end = &quot;L&quot;
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= start.length&nbsp;&lt;= 10<sup>4</sup></code></li>
	<li><code>start.length == end.length</code></li>
	<li>Both <code>start</code> and <code>end</code> will only consist of characters in <code>&#39;L&#39;</code>, <code>&#39;R&#39;</code>, and&nbsp;<code>&#39;X&#39;</code>.</li>
</ul>


### ZH-CN:
<p>在一个由 <code>&#39;L&#39;</code> , <code>&#39;R&#39;</code> 和 <code>&#39;X&#39;</code> 三个字符组成的字符串（例如<code>&quot;RXXLRXRXL&quot;</code>）中进行移动操作。一次移动操作指用一个<code>&quot;LX&quot;</code>替换一个<code>&quot;XL&quot;</code>，或者用一个<code>&quot;XR&quot;</code>替换一个<code>&quot;RX&quot;</code>。现给定起始字符串<code>start</code>和结束字符串<code>end</code>，请编写代码，当且仅当存在一系列移动操作使得<code>start</code>可以转换成<code>end</code>时， 返回<code>True</code>。</p>

<p>&nbsp;</p>

<p><strong>示例 :</strong></p>

<pre><strong>输入:</strong> start = &quot;RXXLRXRXL&quot;, end = &quot;XRLXXRRLX&quot;
<strong>输出:</strong> True
<strong>解释:</strong>
我们可以通过以下几步将start转换成end:
RXXLRXRXL -&gt;
XRXLRXRXL -&gt;
XRLXRXRXL -&gt;
XRLXXRRXL -&gt;
XRLXXRRLX
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= len(start) = len(end) &lt;= 10000</code>。</li>
	<li><code>start</code>和<code>end</code>中的字符串仅限于<code>&#39;L&#39;</code>, <code>&#39;R&#39;</code>和<code>&#39;X&#39;</code>。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/swap-adjacent-in-lr-string/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/swap-adjacent-in-lr-string/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 7.6 MB | 2022/10/01 12:50 |

```cpp

class Solution {
public:
    bool canTransform(string start, string end) {
        const size_t n = start.size();
        string a, b;
        for(size_t i = 0; i < n; i++){
            if(start[i] != 'X') a += start[i];
            if(end[i] != 'X') b += end[i];
        }
        if(a != b) return false;

        // 双指针- i指向start[0], 就指向end[0];
        size_t i = 0, j = 0;
        while(i < n && j < n){ // 如果超界,结束
            // 跳过X
            while(i < n && start[i] == 'X') i++;
            while(j < n && end[j] == 'X') j++;
            if(i < j && start[i] == end[j] && end[j] == 'L') return false; // 当i != j时
            if(i > j && start[i] == end[j] && end[j] == 'R') return false;
            i++, j++;
        }
        return true;
    }
};

```
## My Notes - 我的笔记


No notes

