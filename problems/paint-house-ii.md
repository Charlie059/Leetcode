
# 265. Paint House II - 粉刷房子 II

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">  


## Description - 题目描述

### EN:
<p>There are a row of <code>n</code> houses, each house can be painted with one of the <code>k</code> colors. The cost of painting each house with a certain color is different. You have to paint all the houses such that no two adjacent houses have the same color.</p>

<p>The cost of painting each house with a certain color is represented by an <code>n x k</code> cost matrix costs.</p>

<ul>
	<li>For example, <code>costs[0][0]</code> is the cost of painting house <code>0</code> with color <code>0</code>; <code>costs[1][2]</code> is the cost of painting house <code>1</code> with color <code>2</code>, and so on...</li>
</ul>

<p>Return <em>the minimum cost to paint all houses</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> costs = [[1,5,3],[2,9,4]]
<strong>Output:</strong> 5
<strong>Explanation:</strong>
Paint house 0 into color 0, paint house 1 into color 2. Minimum cost: 1 + 4 = 5; 
Or paint house 0 into color 2, paint house 1 into color 0. Minimum cost: 3 + 2 = 5.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> costs = [[1,3],[2,4]]
<strong>Output:</strong> 5
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>costs.length == n</code></li>
	<li><code>costs[i].length == k</code></li>
	<li><code>1 &lt;= n &lt;= 100</code></li>
	<li><code>2 &lt;= k &lt;= 20</code></li>
	<li><code>1 &lt;= costs[i][j] &lt;= 20</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you solve it in <code>O(nk)</code> runtime?</p>


### ZH-CN:
<p>假如有一排房子共有&nbsp;<code>n</code>&nbsp;幢，每个房子可以被粉刷成 <code>k</code>&nbsp;种颜色中的一种。房子粉刷成不同颜色的花费成本也是不同的。你需要粉刷所有的房子并且使其相邻的两个房子颜色不能相同。</p>

<p>每个房子粉刷成不同颜色的花费以一个 <code>n x k</code> 的矩阵表示。</p>

<ul>
	<li>例如，<code>costs[0][0]</code> 表示第 <code>0</code>&nbsp;幢房子粉刷成 <code>0</code> 号颜色的成本；<code>costs[1][2]</code>&nbsp;表示第 <code>1</code> 幢房子粉刷成 <code>2</code> 号颜色的成本，以此类推。</li>
</ul>

<p>返回 <em>粉刷完所有房子的最低成本</em>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入: </strong>costs = [[1,5,3],[2,9,4]]
<strong>输出: </strong>5
<strong>解释: 
</strong>将房子 0 刷成 0 号颜色，房子 1 刷成 2 号颜色。花费: 1 + 4 = 5; 
或者将 房子 0 刷成 2 号颜色，房子 1 刷成 0 号颜色。花费: 3 + 2 = 5. </pre>

<p><strong>示例&nbsp;<strong>2:</strong></strong></p>

<pre>
<strong>输入:</strong> costs = [[1,3],[2,4]]
<strong>输出:</strong> 5
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>costs.length == n</code></li>
	<li><code>costs[i].length == k</code></li>
	<li><code>1 &lt;= n &lt;= 100</code></li>
	<li><code>2 &lt;= k &lt;= 20</code></li>
	<li><code>1 &lt;= costs[i][j] &lt;= 20</code></li>
</ul>

<p>&nbsp;</p>

<p><strong>进阶：</strong>您能否在&nbsp;<code>O(nk)</code> 的时间复杂度下解决此问题？</p>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/paint-house-ii/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/paint-house-ii/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 20 ms | 11.5 MB | 2022/11/15 14:58 |

```cpp

class Solution {
public:
    int minCostII(vector<vector<int>>& costs) {
        const int n = costs.size();
        const int numOfK = costs[0].size();

        vector<vector<int>> dp(n, vector<int>(numOfK, 0));

        for(int k = 0; k < numOfK; k++) dp[0][k] = costs[0][k];

        for(int i = 1; i < n; i++){
            for(int k = 0; k < numOfK; k++){
                int tmp = INT_MAX;
                for(int j = 0; j < numOfK; j++){
                    if(j != k) tmp = min(tmp, dp[i-1][j]);
                }
                dp[i][k] = tmp + costs[i][k];
            }
        }

        return *min_element(dp[n - 1].begin(), dp[n - 1].end());
    }
};

```
## My Notes - 我的笔记


No notes

