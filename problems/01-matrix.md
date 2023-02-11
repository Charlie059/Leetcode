
# 542. 01 Matrix - 01 矩阵

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Breadth First Search-广度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">   <img src="https://img.shields.io/badge/Matrix-矩阵-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an <code>m x n</code> binary matrix <code>mat</code>, return <em>the distance of the nearest </em><code>0</code><em> for each cell</em>.</p>

<p>The distance between two adjacent cells is <code>1</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/24/01-1-grid.jpg" style="width: 253px; height: 253px;" />
<pre>
<strong>Input:</strong> mat = [[0,0,0],[0,1,0],[0,0,0]]
<strong>Output:</strong> [[0,0,0],[0,1,0],[0,0,0]]
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/04/24/01-2-grid.jpg" style="width: 253px; height: 253px;" />
<pre>
<strong>Input:</strong> mat = [[0,0,0],[0,1,0],[1,1,1]]
<strong>Output:</strong> [[0,0,0],[0,1,0],[1,2,1]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 10<sup>4</sup></code></li>
	<li><code>1 &lt;= m * n &lt;= 10<sup>4</sup></code></li>
	<li><code>mat[i][j]</code> is either <code>0</code> or <code>1</code>.</li>
	<li>There is at least one <code>0</code> in <code>mat</code>.</li>
</ul>


### ZH-CN:
<p>给定一个由 <code>0</code> 和 <code>1</code> 组成的矩阵 <code>mat</code> ，请输出一个大小相同的矩阵，其中每一个格子是 <code>mat</code> 中对应位置元素到最近的 <code>0</code> 的距离。</p>

<p>两个相邻元素间的距离为 <code>1</code> 。</p>

<p> </p>

<p><b>示例 1：</b></p>

<p><img alt="" src="https://pic.leetcode-cn.com/1626667201-NCWmuP-image.png" style="width: 150px; " /></p>

<pre>
<strong>输入：</strong>mat =<strong> </strong>[[0,0,0],[0,1,0],[0,0,0]]
<strong>输出：</strong>[[0,0,0],[0,1,0],[0,0,0]]
</pre>

<p><b>示例 2：</b></p>

<p><img alt="" src="https://pic.leetcode-cn.com/1626667205-xFxIeK-image.png" style="width: 150px; " /></p>

<pre>
<b>输入：</b>mat =<b> </b>[[0,0,0],[0,1,0],[1,1,1]]
<strong>输出：</strong>[[0,0,0],[0,1,0],[1,2,1]]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == mat.length</code></li>
	<li><code>n == mat[i].length</code></li>
	<li><code>1 <= m, n <= 10<sup>4</sup></code></li>
	<li><code>1 <= m * n <= 10<sup>4</sup></code></li>
	<li><code>mat[i][j] is either 0 or 1.</code></li>
	<li><code>mat</code> 中至少有一个 <code>0 </code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/01-matrix/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/01-matrix/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 64 ms | 26.8 MB | 2022/09/29 10:15 |

```cpp

class Solution {
public:
    vector<vector<int>> updateMatrix(vector<vector<int>>& mat) {
        const int m = mat.size();
        const int n = mat[0].size();

        vector<vector<int>> ans(m, vector<int>(n, INT_MAX / 2));

        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(mat[i][j] == 0) ans[i][j] = 0;
            }
        }

        // left and up
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(i - 1 >= 0) ans[i][j] = min(ans[i - 1][j] + 1, ans[i][j]);
                if(j - 1 >= 0) ans[i][j] = min(ans[i][j - 1] + 1, ans[i][j]);
            }
        }

        // left and down
        for(int i = m - 1; i >= 0; i--){
            for(int j = 0; j < n; j++){
                if(i + 1 < m) ans[i][j] = min(ans[i + 1][j] + 1, ans[i][j]);
                if(j - 1 >= 0) ans[i][j] = min(ans[i][j - 1] + 1, ans[i][j]);
            }
        }

        // right and up
        for(int i = 0; i < m; i++){
            for(int j = n - 1; j >= 0; j--){
                if(i - 1 >= 0) ans[i][j] = min(ans[i - 1][j] + 1, ans[i][j]);
                if(j + 1 < n) ans[i][j] = min(ans[i][j + 1] + 1, ans[i][j]);
            }
        }

        // right and down
        for(int i = m - 1; i >= 0; i--){
            for(int j = n - 1; j >= 0; j--){
                if(i + 1 > m) ans[i][j] = min(ans[i + 1][j] + 1, ans[i][j]);
                if(j + 1 < n) ans[i][j] = min(ans[i][j + 1] + 1, ans[i][j]);
            }
        }

        return ans;

    }
};

```
## My Notes - 我的笔记


No notes

