
# 2428. Maximum Sum of an Hourglass - 沙漏的最大总和

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Matrix-矩阵-blue.svg">   <img src="https://img.shields.io/badge/Prefix Sum-前缀和-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given an <code>m x n</code> integer matrix <code>grid</code>.</p>

<p>We define an <strong>hourglass</strong> as a part of the matrix with the following form:</p>
<img alt="" src="https://assets.leetcode.com/uploads/2022/08/21/img.jpg" style="width: 243px; height: 243px;" />
<p>Return <em>the <strong>maximum</strong> sum of the elements of an hourglass</em>.</p>

<p><strong>Note</strong> that an hourglass cannot be rotated and must be entirely contained within the matrix.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2022/08/21/1.jpg" style="width: 323px; height: 323px;" />
<pre>
<strong>Input:</strong> grid = [[6,2,1,3],[4,2,1,5],[9,2,8,7],[4,1,2,9]]
<strong>Output:</strong> 30
<strong>Explanation:</strong> The cells shown above represent the hourglass with the maximum sum: 6 + 2 + 1 + 2 + 9 + 2 + 8 = 30.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2022/08/21/2.jpg" style="width: 243px; height: 243px;" />
<pre>
<strong>Input:</strong> grid = [[1,2,3],[4,5,6],[7,8,9]]
<strong>Output:</strong> 35
<strong>Explanation:</strong> There is only one hourglass in the matrix, with the sum: 1 + 2 + 3 + 5 + 7 + 8 + 9 = 35.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>3 &lt;= m, n &lt;= 150</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 10<sup>6</sup></code></li>
</ul>


### ZH-CN:
<p>给你一个大小为 <code>m x n</code> 的整数矩阵 <code>grid</code> 。</p>

<p>按以下形式将矩阵的一部分定义为一个 <strong>沙漏</strong> ：</p>
<img alt="" src="https://assets.leetcode.com/uploads/2022/08/21/img.jpg" style="width: 243px; height: 243px;">
<p>返回沙漏中元素的 <strong>最大</strong> 总和。</p>

<p><strong>注意：</strong>沙漏无法旋转且必须整个包含在矩阵中。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2022/08/21/1.jpg" style="width: 323px; height: 323px;">
<pre><strong>输入：</strong>grid = [[6,2,1,3],[4,2,1,5],[9,2,8,7],[4,1,2,9]]
<strong>输出：</strong>30
<strong>解释：</strong>上图中的单元格表示元素总和最大的沙漏：6 + 2 + 1 + 2 + 9 + 2 + 8 = 30 。
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2022/08/21/2.jpg" style="width: 243px; height: 243px;">
<pre><strong>输入：</strong>grid = [[1,2,3],[4,5,6],[7,8,9]]
<strong>输出：</strong>35
<strong>解释：</strong>上图中的单元格表示元素总和最大的沙漏：1 + 2 + 3 + 5 + 7 + 8 + 9 = 35 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>3 &lt;= m, n &lt;= 150</code></li>
	<li><code>0 &lt;= grid[i][j] &lt;= 10<sup>6</sup></code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/maximum-sum-of-an-hourglass/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/maximum-sum-of-an-hourglass/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 32 ms | 13.9 MB | 2022/10/01 22:42 |

```cpp

class Solution {
public:
    int maxSum(vector<vector<int>>& grid) {
        const int m = grid.size();
        const int n = grid[0].size();
        
        vector<vector<int>> preSum(m, vector<int>(n + 1, 0));
        
        // Init presum
        for(int i = 0; i < m; i++){
            for(int j = 1; j < n + 1; j++){
                preSum[i][j] = grid[i][j - 1] + preSum[i][j - 1];
            }
        }
        int ans = 0;
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n + 1; j++){
                if(i + 2 < m && j + 3 <= n){
                    int firstRow = preSum[i][j + 3] - preSum[i][j];
                    int secondRow = preSum[i + 1][j + 2] - preSum[i + 1][j + 1];
                    int thirdRow = preSum[i + 2][j + 3] - preSum[i + 2][j];
                    ans = max(ans, firstRow + secondRow + thirdRow);
                }
            }
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

