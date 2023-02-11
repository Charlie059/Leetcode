
# 741. Cherry Pickup - 摘樱桃

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Matrix-矩阵-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given an <code>n x n</code> <code>grid</code> representing a field of cherries, each cell is one of three possible integers.</p>

<ul>
	<li><code>0</code> means the cell is empty, so you can pass through,</li>
	<li><code>1</code> means the cell contains a cherry that you can pick up and pass through, or</li>
	<li><code>-1</code> means the cell contains a thorn that blocks your way.</li>
</ul>

<p>Return <em>the maximum number of cherries you can collect by following the rules below</em>:</p>

<ul>
	<li>Starting at the position <code>(0, 0)</code> and reaching <code>(n - 1, n - 1)</code> by moving right or down through valid path cells (cells with value <code>0</code> or <code>1</code>).</li>
	<li>After reaching <code>(n - 1, n - 1)</code>, returning to <code>(0, 0)</code> by moving left or up through valid path cells.</li>
	<li>When passing through a path cell containing a cherry, you pick it up, and the cell becomes an empty cell <code>0</code>.</li>
	<li>If there is no valid path between <code>(0, 0)</code> and <code>(n - 1, n - 1)</code>, then no cherries can be collected.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/12/14/grid.jpg" style="width: 242px; height: 242px;" />
<pre>
<strong>Input:</strong> grid = [[0,1,-1],[1,0,-1],[1,1,1]]
<strong>Output:</strong> 5
<strong>Explanation:</strong> The player started at (0, 0) and went down, down, right right to reach (2, 2).
4 cherries were picked up during this single trip, and the matrix becomes [[0,1,-1],[0,0,-1],[0,0,0]].
Then, the player went left, up, up, left to return home, picking up one more cherry.
The total number of cherries picked up is 5, and this is the maximum possible.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> grid = [[1,1,-1],[1,-1,1],[-1,1,1]]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= n &lt;= 50</code></li>
	<li><code>grid[i][j]</code> is <code>-1</code>, <code>0</code>, or <code>1</code>.</li>
	<li><code>grid[0][0] != -1</code></li>
	<li><code>grid[n - 1][n - 1] != -1</code></li>
</ul>


### ZH-CN:
<p>一个N x N的网格<code>(grid)</code>&nbsp;代表了一块樱桃地，每个格子由以下三种数字的一种来表示：</p>

<ul>
	<li>0 表示这个格子是空的，所以你可以穿过它。</li>
	<li>1 表示这个格子里装着一个樱桃，你可以摘到樱桃然后穿过它。</li>
	<li>-1 表示这个格子里有荆棘，挡着你的路。</li>
</ul>

<p>你的任务是在遵守下列规则的情况下，尽可能的摘到最多樱桃：</p>

<ul>
	<li>从位置&nbsp;(0, 0) 出发，最后到达 (N-1, N-1) ，只能向下或向右走，并且只能穿越有效的格子（即只可以穿过值为0或者1的格子）；</li>
	<li>当到达 (N-1, N-1) 后，你要继续走，直到返回到 (0, 0) ，只能向上或向左走，并且只能穿越有效的格子；</li>
	<li>当你经过一个格子且这个格子包含一个樱桃时，你将摘到樱桃并且这个格子会变成空的（值变为0）；</li>
	<li>如果在 (0, 0) 和 (N-1, N-1) 之间不存在一条可经过的路径，则没有任何一个樱桃能被摘到。</li>
</ul>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入:</strong> grid =
[[0, 1, -1],
 [1, 0, -1],
 [1, 1,  1]]
<strong>输出:</strong> 5
<strong>解释：</strong> 
玩家从（0,0）点出发，经过了向下走，向下走，向右走，向右走，到达了点(2, 2)。
在这趟单程中，总共摘到了4颗樱桃，矩阵变成了[[0,1,-1],[0,0,-1],[0,0,0]]。
接着，这名玩家向左走，向上走，向上走，向左走，返回了起始点，又摘到了1颗樱桃。
在旅程中，总共摘到了5颗樱桃，这是可以摘到的最大值了。
</pre>

<p><strong>说明:</strong></p>

<ul>
	<li><code>grid</code> 是一个&nbsp;<code>N</code> * <code>N</code> 的二维数组，N的取值范围是<code>1 &lt;= N &lt;= 50</code>。</li>
	<li>每一个&nbsp;<code>grid[i][j]</code> 都是集合&nbsp;<code>{-1, 0, 1}</code>其中的一个数。</li>
	<li>可以保证起点&nbsp;<code>grid[0][0]</code>&nbsp;和终点&nbsp;<code>grid[N-1][N-1]</code>&nbsp;的值都不会是 -1。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/cherry-pickup/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/cherry-pickup/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 52 ms | 21.8 MB | 2022/11/12 22:26 |

```cpp

class Solution {
public:
    int cherryPickup(vector<vector<int>>& grid) {
        const int n = grid.size();
        vector<vector<vector<int>>> dp(n, vector<vector<int>>(n, vector<int>(n, INT_MIN)));
        return max(0, dfs(grid, dp, n - 1, n - 1, n - 1, n - 1));
    }

    int dfs(vector<vector<int>>& grid, vector<vector<vector<int>>>& dp, int x1, int y1, int x2, int y2){


        if(x1 < 0 || y1 < 0 || x2 < 0 || y2 < 0) return -1;
        if(grid[x1][y1] == -1 || grid[x2][y2] == -1) return -1;
        
        if(x1 == 0 && y1 == 0) return grid[x1][y1];
        if(dp[x1][y1][x2] != INT_MIN) return dp[x1][y1][x2];

        int ans = INT_MIN;
        ans = max(ans, dfs(grid, dp, x1 - 1, y1, x2 - 1, y2)); 
        ans = max(ans, dfs(grid, dp, x1, y1 - 1, x2, y2 - 1)); 
        ans = max(ans, dfs(grid, dp, x1, y1 - 1, x2 - 1, y2)); 
        ans = max(ans, dfs(grid, dp, x1 - 1, y1, x2, y2 - 1));     

        if(ans < 0){
            dp[x1][y1][x2] = -1;
            return -1;
        }

        ans += grid[x1][y1];
        if(x1 != x2) ans += grid[x2][y2];
        dp[x1][y1][x2] = ans;
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

