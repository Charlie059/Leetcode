
# 655. Print Binary Tree - 输出二叉树

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Tree-树-blue.svg">   <img src="https://img.shields.io/badge/Depth First Search-深度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Breadth First Search-广度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Binary Tree-二叉树-blue.svg">  


## Description - 题目描述

### EN:
<p>Given the <code>root</code> of a binary tree, construct a <strong>0-indexed</strong> <code>m x n</code> string matrix <code>res</code> that represents a <strong>formatted layout</strong> of the tree. The formatted layout matrix should be constructed using the following rules:</p>

<ul>
	<li>The <strong>height</strong> of the tree is <code>height</code>&nbsp;and the number of rows <code>m</code> should be equal to <code>height + 1</code>.</li>
	<li>The number of columns <code>n</code> should be equal to <code>2<sup>height+1</sup> - 1</code>.</li>
	<li>Place the <strong>root node</strong> in the <strong>middle</strong> of the <strong>top row</strong> (more formally, at location <code>res[0][(n-1)/2]</code>).</li>
	<li>For each node that has been placed in the matrix at position <code>res[r][c]</code>, place its <strong>left child</strong> at <code>res[r+1][c-2<sup>height-r-1</sup>]</code> and its <strong>right child</strong> at <code>res[r+1][c+2<sup>height-r-1</sup>]</code>.</li>
	<li>Continue this process until all the nodes in the tree have been placed.</li>
	<li>Any empty cells should contain the empty string <code>&quot;&quot;</code>.</li>
</ul>

<p>Return <em>the constructed matrix </em><code>res</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/03/print1-tree.jpg" style="width: 141px; height: 181px;" />
<pre>
<strong>Input:</strong> root = [1,2]
<strong>Output:</strong> 
[[&quot;&quot;,&quot;1&quot;,&quot;&quot;],
&nbsp;[&quot;2&quot;,&quot;&quot;,&quot;&quot;]]
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/03/print2-tree.jpg" style="width: 207px; height: 302px;" />
<pre>
<strong>Input:</strong> root = [1,2,3,null,4]
<strong>Output:</strong> 
[[&quot;&quot;,&quot;&quot;,&quot;&quot;,&quot;1&quot;,&quot;&quot;,&quot;&quot;,&quot;&quot;],
&nbsp;[&quot;&quot;,&quot;2&quot;,&quot;&quot;,&quot;&quot;,&quot;&quot;,&quot;3&quot;,&quot;&quot;],
&nbsp;[&quot;&quot;,&quot;&quot;,&quot;4&quot;,&quot;&quot;,&quot;&quot;,&quot;&quot;,&quot;&quot;]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 2<sup>10</sup>]</code>.</li>
	<li><code>-99 &lt;= Node.val &lt;= 99</code></li>
	<li>The depth of the tree will be in the range <code>[1, 10]</code>.</li>
</ul>


### ZH-CN:
<p>给你一棵二叉树的根节点 <code>root</code> ，请你构造一个下标从 <strong>0</strong> 开始、大小为 <code>m x n</code> 的字符串矩阵 <code>res</code> ，用以表示树的 <strong>格式化布局</strong> 。构造此格式化布局矩阵需要遵循以下规则：</p>

<ul>
	<li>树的 <strong>高度</strong> 为 <code>height</code> ，矩阵的行数 <code>m</code> 应该等于 <code>height + 1</code> 。</li>
	<li>矩阵的列数 <code>n</code> 应该等于 <code>2<sup>height+1</sup> - 1</code> 。</li>
	<li><strong>根节点</strong> 需要放置在 <strong>顶行</strong> 的 <strong>正中间</strong> ，对应位置为 <code>res[0][(n-1)/2]</code> 。</li>
	<li>对于放置在矩阵中的每个节点，设对应位置为 <code>res[r][c]</code> ，将其左子节点放置在 <code>res[r+1][c-2<sup>height-r-1</sup>]</code> ，右子节点放置在 <code>res[r+1][c+2<sup>height-r-1</sup>]</code> 。</li>
	<li>继续这一过程，直到树中的所有节点都妥善放置。</li>
	<li>任意空单元格都应该包含空字符串 <code>""</code> 。</li>
</ul>

<p>返回构造得到的矩阵<em> </em><code>res</code> 。</p>

<p>&nbsp;</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/03/print1-tree.jpg" style="width: 141px; height: 181px;" />
<pre>
<strong>输入：</strong>root = [1,2]
<strong>输出：</strong>
[["","1",""],
&nbsp;["2","",""]]
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/03/print2-tree.jpg" style="width: 207px; height: 302px;" />
<pre>
<strong>输入：</strong>root = [1,2,3,null,4]
<strong>输出：</strong>
[["","","","1","","",""],
&nbsp;["","2","","","","3",""],
&nbsp;["","","4","","","",""]]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>树中节点数在范围 <code>[1, 2<sup>10</sup>]</code> 内</li>
	<li><code>-99 &lt;= Node.val &lt;= 99</code></li>
	<li>树的深度在范围 <code>[1, 10]</code> 内</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/print-binary-tree/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/print-binary-tree/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 8.1 MB | 2022/12/23 16:03 |

```cpp

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int height;
    int getHeight(const TreeNode* root) const{
        if(!root) return 0;
        int ans = 0;
        ans = max(getHeight(root->left), getHeight(root->right));
        return ans + 1;
    }

    void dfs(const TreeNode* root, int r, int c, vector<vector<string>>& ans){
        if(!root) return;
        ans[r][c] = to_string(root->val);

        dfs(root->left, r + 1, c - pow(2, height - r - 1), ans);
        dfs(root->right, r + 1, c + pow(2, height - r - 1), ans);
    }
    vector<vector<string>> printTree(TreeNode* root) {
        height = getHeight(root) - 1;
        vector<vector<string>> ans(height + 1, vector<string>(pow(2, height + 1) - 1, ""));
        dfs(root, 0, (ans[0].size() - 1) / 2, ans);
        return ans;
    }

    
};

```
## My Notes - 我的笔记


No notes

