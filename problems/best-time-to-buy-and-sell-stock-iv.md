
# 188. Best Time to Buy and Sell Stock IV - 买卖股票的最佳时机 IV

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given an integer array <code>prices</code> where <code>prices[i]</code> is the price of a given stock on the <code>i<sup>th</sup></code> day, and an integer <code>k</code>.</p>

<p>Find the maximum profit you can achieve. You may complete at most <code>k</code> transactions.</p>

<p><strong>Note:</strong> You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> k = 2, prices = [2,4,1]
<strong>Output:</strong> 2
<strong>Explanation:</strong> Buy on day 1 (price = 2) and sell on day 2 (price = 4), profit = 4-2 = 2.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> k = 2, prices = [3,2,6,5,0,3]
<strong>Output:</strong> 7
<strong>Explanation:</strong> Buy on day 2 (price = 2) and sell on day 3 (price = 6), profit = 6-2 = 4. Then buy on day 5 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= k &lt;= 100</code></li>
	<li><code>1 &lt;= prices.length &lt;= 1000</code></li>
	<li><code>0 &lt;= prices[i] &lt;= 1000</code></li>
</ul>


### ZH-CN:
<p>给定一个整数数组 <code>prices</code> ，它的第<em> </em><code>i</code> 个元素 <code>prices[i]</code> 是一支给定的股票在第 <code>i</code><em> </em>天的价格。</p>

<p>设计一个算法来计算你所能获取的最大利润。你最多可以完成 <strong>k</strong> 笔交易。</p>

<p><strong>注意：</strong>你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>k = 2, prices = [2,4,1]
<strong>输出：</strong>2
<strong>解释：</strong>在第 1 天 (股票价格 = 2) 的时候买入，在第 2 天 (股票价格 = 4) 的时候卖出，这笔交易所能获得利润 = 4-2 = 2 。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>k = 2, prices = [3,2,6,5,0,3]
<strong>输出：</strong>7
<strong>解释：</strong>在第 2 天 (股票价格 = 2) 的时候买入，在第 3 天 (股票价格 = 6) 的时候卖出, 这笔交易所能获得利润 = 6-2 = 4 。
     随后，在第 5 天 (股票价格 = 0) 的时候买入，在第 6 天 (股票价格 = 3) 的时候卖出, 这笔交易所能获得利润 = 3-0 = 3 。</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= k <= 100</code></li>
	<li><code>0 <= prices.length <= 1000</code></li>
	<li><code>0 <= prices[i] <= 1000</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-iv/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 8 ms | 12.1 MB | 2022/09/07 21:28 |

```cpp

class Solution {
public:
    int maxProfit(int k, vector<int>& prices) {
         /*
            2k + 1 State
            (1) dp[i][0]: maxProfit with No Ops
            (2) dp[i][1]: maxProfit with First time buy
            (3) dp[i][2]: maxProfit with First time sell

            dp[i][0] = dp[i-1][0]
            dp[i][j+1] = max(dp[i-1][j+1], dp[i-1][j] - prices[i])
            dp[i][j+2] = max(dp[i-1][j+2], dp[i-1][j+1] + prices[i])


            dp[0][0] = 0
            dp[0][1] = -prices[i]
            dp[0][2] = 0

        */

        const int n = prices.size();
        if(n == 1 || n == 0) return 0;
        vector<vector<int>> dp(2 * k + 1, vector<int>(n, 0));

        // Init
        for(int i = 1; i < 2 * k + 1; i += 2) dp[i][0] = -prices[0];
        

        for(int i = 1; i < n; i++){
            dp[0][i] = dp[0][i-1];
            for(int j = 0; j < 2 * k; j+=2){
                dp[j+1][i] = max(dp[j+1][i-1], dp[j][i-1] - prices[i]);
                dp[j+2][i] = max(dp[j+2][i-1], dp[j+1][i-1] + prices[i]);
            }
        }

        return dp[2*k][n-1];
    }
};

```
## My Notes - 我的笔记


No notes

