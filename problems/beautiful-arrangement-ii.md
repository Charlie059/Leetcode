
# 667. Beautiful Arrangement II - 优美的排列 II

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">  


## Description - 题目描述

### EN:
<p>Given two integers <code>n</code> and <code>k</code>, construct a list <code>answer</code> that contains <code>n</code> different positive integers ranging from <code>1</code> to <code>n</code> and obeys the following requirement:</p>

<ul>
	<li>Suppose this list is <code>answer =&nbsp;[a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub>, ... , a<sub>n</sub>]</code>, then the list <code>[|a<sub>1</sub> - a<sub>2</sub>|, |a<sub>2</sub> - a<sub>3</sub>|, |a<sub>3</sub> - a<sub>4</sub>|, ... , |a<sub>n-1</sub> - a<sub>n</sub>|]</code> has exactly <code>k</code> distinct integers.</li>
</ul>

<p>Return <em>the list</em> <code>answer</code>. If there multiple valid answers, return <strong>any of them</strong>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 3, k = 1
<strong>Output:</strong> [1,2,3]
Explanation: The [1,2,3] has three different positive integers ranging from 1 to 3, and the [1,1] has exactly 1 distinct integer: 1
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 3, k = 2
<strong>Output:</strong> [1,3,2]
Explanation: The [1,3,2] has three different positive integers ranging from 1 to 3, and the [2,1] has exactly 2 distinct integers: 1 and 2.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt; n &lt;= 10<sup>4</sup></code></li>
</ul>


### ZH-CN:
<p>给你两个整数 <code>n</code> 和 <code>k</code> ，请你构造一个答案列表 <code>answer</code> ，该列表应当包含从 <code>1</code> 到 <code>n</code> 的 <code>n</code> 个不同正整数，并同时满足下述条件：</p>

<ul>
	<li>假设该列表是 <code>answer = [a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub>, ... , a<sub>n</sub>]</code> ，那么列表 <code>[|a<sub>1</sub> - a<sub>2</sub>|, |a<sub>2</sub> - a<sub>3</sub>|, |a<sub>3</sub> - a<sub>4</sub>|, ... , |a<sub>n-1</sub> - a<sub>n</sub>|]</code> 中应该有且仅有 <code>k</code> 个不同整数。</li>
</ul>

<p>返回列表 <code>answer</code> 。如果存在多种答案，只需返回其中 <strong>任意一种</strong> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 3, k = 1
<strong>输出：</strong>[1, 2, 3]
<strong>解释：</strong>[1, 2, 3] 包含 3 个范围在 1-3 的不同整数，并且 [1, 1] 中有且仅有 1 个不同整数：1
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 3, k = 2
<strong>输出：</strong>[1, 3, 2]
<strong>解释：</strong>[1, 3, 2] 包含 3 个范围在 1-3 的不同整数，并且 [2, 1] 中有且仅有 2 个不同整数：1 和 2
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= k < n <= 10<sup>4</sup></code></li>
</ul>

<p> </p>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/beautiful-arrangement-ii/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/beautiful-arrangement-ii/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 7.3 MB | 2022/12/11 21:08 |

```cpp

class Solution {
public:
    vector<int> constructArray(int n, int k) {
        int a = 1, b = n;
        vector<int> ans(n);

        for(int i = 0; i < k; i++)  ans[i] = i % 2 == 0 ? a++ : b--;
        
        if(k % 2 == 0) for(int i = k; i < n; i++) ans[i] = ans[i - 1] - 1;
        else for(int i = k; i < n; i++) ans[i] = ans[i - 1] + 1;
        
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

