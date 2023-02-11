
# 面试题 17.06. Number Of 2s In Range LCCI - 2出现的次数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Recursion-递归-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">  


## Description - 题目描述

### EN:
<p>Write a method to count the number of 2s that appear in all the numbers between 0&nbsp;and n (inclusive).</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input: </strong>25
<strong>Output: </strong>9
<strong>Explanation: </strong>(2, 12, 20, 21, 22, 23, 24, 25)(Note that 22 counts for two 2s.)</pre>

<p>Note:</p>

<ul>
	<li><code>n &lt;= 10^9</code></li>
</ul>


### ZH-CN:
<p>编写一个方法，计算从 0 到 n (含 n) 中数字 2 出现的次数。</p>

<p><strong>示例:</strong></p>

<pre><strong>输入: </strong>25
<strong>输出: </strong>9
<strong>解释: </strong>(2, 12, 20, 21, 22, 23, 24, 25)(注意 22 应该算作两次)</pre>

<p>提示：</p>

<ul>
	<li><code>n &lt;= 10^9</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/number-of-2s-in-range-lcci/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/number-of-2s-in-range-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 6 MB | 2022/09/24 22:29 |

```cpp

class Solution {
public:
    int numberOf2sInRange(int n) {
        string s = to_string(n);
        const int m = s.length();

        vector<vector<int>> dp(m, vector<int>(m, -1));

        function<int(int, int, bool)> f = [&](int i, int cnt2, bool is_limit) -> int {
            if(i == m) return cnt2;
            if(!is_limit && dp[i][cnt2] >= 0) return dp[i][cnt2];

            int res = 0;
            for(int d = 0, up = is_limit ? s[i] - '0' : 9; d <= up; ++d){
                res += f(i + 1, cnt2 + (d == 2), is_limit && d == up);
            }
            if(!is_limit) dp[i][cnt2] = res;
            return res;
        };

        return f(0, 0, true);
    }
};

```
## My Notes - 我的笔记


No notes

