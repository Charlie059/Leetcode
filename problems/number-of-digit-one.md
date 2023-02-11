
# 233. Number of Digit One - 数字 1 的个数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Recursion-递归-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an integer <code>n</code>, count <em>the total number of digit </em><code>1</code><em> appearing in all non-negative integers less than or equal to</em> <code>n</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 13
<strong>Output:</strong> 6
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 0
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>


### ZH-CN:
<p>给定一个整数 <code>n</code>，计算所有小于等于 <code>n</code> 的非负整数中数字 <code>1</code> 出现的个数。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 13
<strong>输出：</strong>6
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 0
<strong>输出：</strong>0
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 &lt;= n &lt;= 10<sup>9</sup></code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/number-of-digit-one/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/number-of-digit-one/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 5.9 MB | 2022/09/24 22:12 |

```cpp

class Solution {
public:
    int countDigitOne(int n) {
        auto s = to_string(n);
        const int m = s.length();
        vector<vector<int>>dp(m, vector<int>(m, -1));
        function<int(int, int, bool)> f = [&](int i, int cnt1, bool is_limit) -> int {
            if(i == m) return cnt1;
            if(!is_limit && dp[i][cnt1] >= 0) return dp[i][cnt1];

            int res = 0;
            for(int d = 0, up = is_limit ? s[i] - '0' : 9; d <= up; ++d){
                res += f(i + 1, cnt1 + (d == 1), is_limit && d== up);
            }

            if(!is_limit) dp[i][cnt1] = res;
            return res;
        };

        return f(0, 0, true);
    }
};

```
## My Notes - 我的笔记


No notes

