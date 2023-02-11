
# 1632. Rank Transform of a Matrix - 矩阵转换后的秩

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Greedy-贪心-blue.svg">   <img src="https://img.shields.io/badge/Union Find-并查集-blue.svg">   <img src="https://img.shields.io/badge/Graph-图-blue.svg">   <img src="https://img.shields.io/badge/Topological Sort-拓扑排序-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Matrix-矩阵-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an <code>m x n</code> <code>matrix</code>, return <em>a new matrix </em><code>answer</code><em> where </em><code>answer[row][col]</code><em> is the </em><em><strong>rank</strong> of </em><code>matrix[row][col]</code>.</p>

<p>The <strong>rank</strong> is an <strong>integer</strong> that represents how large an element is compared to other elements. It is calculated using the following rules:</p>

<ul>
	<li>The rank is an integer starting from <code>1</code>.</li>
	<li>If two elements <code>p</code> and <code>q</code> are in the <strong>same row or column</strong>, then:
	<ul>
		<li>If <code>p &lt; q</code> then <code>rank(p) &lt; rank(q)</code></li>
		<li>If <code>p == q</code> then <code>rank(p) == rank(q)</code></li>
		<li>If <code>p &gt; q</code> then <code>rank(p) &gt; rank(q)</code></li>
	</ul>
	</li>
	<li>The <strong>rank</strong> should be as <strong>small</strong> as possible.</li>
</ul>

<p>The test cases are generated so that <code>answer</code> is unique under the given rules.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/18/rank1.jpg" style="width: 442px; height: 162px;" />
<pre>
<strong>Input:</strong> matrix = [[1,2],[3,4]]
<strong>Output:</strong> [[1,2],[2,3]]
<strong>Explanation:</strong>
The rank of matrix[0][0] is 1 because it is the smallest integer in its row and column.
The rank of matrix[0][1] is 2 because matrix[0][1] &gt; matrix[0][0] and matrix[0][0] is rank 1.
The rank of matrix[1][0] is 2 because matrix[1][0] &gt; matrix[0][0] and matrix[0][0] is rank 1.
The rank of matrix[1][1] is 3 because matrix[1][1] &gt; matrix[0][1], matrix[1][1] &gt; matrix[1][0], and both matrix[0][1] and matrix[1][0] are rank 2.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/18/rank2.jpg" style="width: 442px; height: 162px;" />
<pre>
<strong>Input:</strong> matrix = [[7,7],[7,7]]
<strong>Output:</strong> [[1,1],[1,1]]
</pre>

<p><strong class="example">Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/18/rank3.jpg" style="width: 601px; height: 322px;" />
<pre>
<strong>Input:</strong> matrix = [[20,-21,14],[-19,4,19],[22,-47,24],[-19,4,19]]
<strong>Output:</strong> [[4,2,3],[1,3,4],[5,1,6],[1,3,4]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == matrix.length</code></li>
	<li><code>n == matrix[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 500</code></li>
	<li><code>-10<sup>9</sup> &lt;= matrix[row][col] &lt;= 10<sup>9</sup></code></li>
</ul>


### ZH-CN:
<p>给你一个 <code>m x n</code> 的矩阵 <code>matrix</code> ，请你返回一个新的矩阵<em> </em><code>answer</code> ，其中<em> </em><code>answer[row][col]</code> 是 <code>matrix[row][col]</code> 的秩。</p>

<p>每个元素的 <b>秩</b> 是一个整数，表示这个元素相对于其他元素的大小关系，它按照如下规则计算：</p>

<ul>
	<li>秩是从 1 开始的一个整数。</li>
	<li>如果两个元素 <code>p</code> 和 <code>q</code> 在 <strong>同一行</strong> 或者 <strong>同一列</strong> ，那么：
	<ul>
		<li>如果 <code>p < q</code> ，那么 <code>rank(p) < rank(q)</code></li>
		<li>如果 <code>p == q</code> ，那么 <code>rank(p) == rank(q)</code></li>
		<li>如果 <code>p > q</code> ，那么 <code>rank(p) > rank(q)</code></li>
	</ul>
	</li>
	<li><b>秩</b> 需要越 <strong>小</strong> 越好。</li>
</ul>

<p>题目保证按照上面规则 <code>answer</code> 数组是唯一的。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/10/25/rank1.jpg" style="width: 442px; height: 162px;" />
<pre>
<b>输入：</b>matrix = [[1,2],[3,4]]
<b>输出：</b>[[1,2],[2,3]]
<strong>解释：</strong>
matrix[0][0] 的秩为 1 ，因为它是所在行和列的最小整数。
matrix[0][1] 的秩为 2 ，因为 matrix[0][1] > matrix[0][0] 且 matrix[0][0] 的秩为 1 。
matrix[1][0] 的秩为 2 ，因为 matrix[1][0] > matrix[0][0] 且 matrix[0][0] 的秩为 1 。
matrix[1][1] 的秩为 3 ，因为 matrix[1][1] > matrix[0][1]， matrix[1][1] > matrix[1][0] 且 matrix[0][1] 和 matrix[1][0] 的秩都为 2 。
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/10/25/rank2.jpg" style="width: 442px; height: 162px;" />
<pre>
<b>输入：</b>matrix = [[7,7],[7,7]]
<b>输出：</b>[[1,1],[1,1]]
</pre>

<p><strong>示例 3：</strong></p>
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/10/25/rank3.jpg" style="width: 601px; height: 322px;" />
<pre>
<b>输入：</b>matrix = [[20,-21,14],[-19,4,19],[22,-47,24],[-19,4,19]]
<b>输出：</b>[[4,2,3],[1,3,4],[5,1,6],[1,3,4]]
</pre>

<p><strong>示例 4：</strong></p>
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/10/25/rank4.jpg" style="width: 601px; height: 242px;" />
<pre>
<b>输入：</b>matrix = [[7,3,6],[1,4,5],[9,8,2]]
<b>输出：</b>[[5,1,4],[1,2,3],[6,3,1]]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == matrix.length</code></li>
	<li><code>n == matrix[i].length</code></li>
	<li><code>1 <= m, n <= 500</code></li>
	<li><code>-10<sup>9</sup> <= matrix[row][col] <= 10<sup>9</sup></code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/rank-transform-of-a-matrix/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/rank-transform-of-a-matrix/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 164 ms | 64.9 MB | 2023/01/24 14:43 |

```cpp

class Solution {
public: 
//  并查集用于合并行或列相同的元素
    const static int LIM = 512; 
    int unions[LIM*2]; 
    int find(int i){
        if(unions[i] == i)return i; 
        unions[i] = find(unions[i]); 
        return unions[i]; 
    }

    vector<vector<int>> matrixRankTransform(vector<vector<int>>& matrix) {
        int R = matrix.size(), C = matrix[0].size(); 
        vector<vector<int>> res(R, vector<int>(C, 0)); 
        int countR[R], countC[C]; 
        memset(countR, 0, sizeof(countR)); 
        memset(countC, 0, sizeof(countC)); 

        // 按元素大小分别存储元素
        unordered_map<int, vector<int>> ls, pool; 
        for(int r = 0; r<R; r++){
            for(int c = 0; c<C; c++){
                ls[matrix[r][c]].push_back(r*LIM+c); 
            }
        }

        // 初始化并查集
        for(int i = 0; i<LIM*2; i++) unions[i] = i; 

        // 按从小到大的顺序遍历
        int values[ls.size()], i = 0; 
        for(auto p: ls) values[i++] = p.first;
        sort(values, values+ls.size()); 
        for(int val: values){

            // 用并查集合并行和列相同的元素并分组
            for(int pt: ls[val]){
                unions[find(pt/LIM)] = find((pt%LIM)+LIM); 
            }
            pool.clear(); 
            for(int pt: ls[val]){
                pool[find(pt/LIM)].push_back(pt); 
            }

            // 行/列相同的元素，共享相同的rank
            for(pair<int, vector<int>> group: pool){
                int rank = 0; 
                for(int pt: group.second){
                    rank = max(rank, max(countR[pt/LIM], countC[pt%LIM])); 
                }
                rank += 1; 
                for(int pt: group.second){
                    int r = pt/LIM, c = pt%LIM; 
                    countR[r] = countC[c] = res[r][c] = rank; 
                    // 重置并查集
                    unions[r] = r; 
                    unions[c+LIM] = c+LIM; 
                }
            }
        }
        return res; 
    }
}; 


```
## My Notes - 我的笔记


No notes

