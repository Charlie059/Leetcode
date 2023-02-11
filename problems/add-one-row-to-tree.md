
# 623. Add One Row to Tree - 在二叉树中增加一行

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Tree-树-blue.svg">   <img src="https://img.shields.io/badge/Depth First Search-深度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Breadth First Search-广度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Binary Tree-二叉树-blue.svg">  


## Description - 题目描述

### EN:
<p>Given the <code>root</code> of a binary tree and two integers <code>val</code> and <code>depth</code>, add a row of nodes with value <code>val</code> at the given depth <code>depth</code>.</p>

<p>Note that the <code>root</code> node is at depth <code>1</code>.</p>

<p>The adding rule is:</p>

<ul>
	<li>Given the integer <code>depth</code>, for each not null tree node <code>cur</code> at the depth <code>depth - 1</code>, create two tree nodes with value <code>val</code> as <code>cur</code>&#39;s left subtree root and right subtree root.</li>
	<li><code>cur</code>&#39;s original left subtree should be the left subtree of the new left subtree root.</li>
	<li><code>cur</code>&#39;s original right subtree should be the right subtree of the new right subtree root.</li>
	<li>If <code>depth == 1</code> that means there is no depth <code>depth - 1</code> at all, then create a tree node with value <code>val</code> as the new root of the whole original tree, and the original tree is the new root&#39;s left subtree.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/15/addrow-tree.jpg" style="width: 500px; height: 231px;" />
<pre>
<strong>Input:</strong> root = [4,2,6,3,1,5], val = 1, depth = 2
<strong>Output:</strong> [4,1,1,2,null,null,6,3,1,5]
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/11/add2-tree.jpg" style="width: 500px; height: 277px;" />
<pre>
<strong>Input:</strong> root = [4,2,null,3,1], val = 1, depth = 3
<strong>Output:</strong> [4,2,null,1,1,3,null,null,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li>The depth of the tree is in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
	<li><code>-10<sup>5</sup> &lt;= val &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= depth &lt;= the depth of tree + 1</code></li>
</ul>


### ZH-CN:
<p>给定一个二叉树的根&nbsp;<code>root</code>&nbsp;和两个整数 <code>val</code> 和&nbsp;<code>depth</code>&nbsp;，在给定的深度&nbsp;<code>depth</code>&nbsp;处添加一个值为 <code>val</code> 的节点行。</p>

<p>注意，根节点&nbsp;<code>root</code>&nbsp;位于深度&nbsp;<code>1</code>&nbsp;。</p>

<p>加法规则如下:</p>

<ul>
	<li>给定整数&nbsp;<code>depth</code>，对于深度为&nbsp;<code>depth - 1</code> 的每个非空树节点 <code>cur</code> ，创建两个值为 <code>val</code> 的树节点作为 <code>cur</code> 的左子树根和右子树根。</li>
	<li><code>cur</code> 原来的左子树应该是新的左子树根的左子树。</li>
	<li><code>cur</code> 原来的右子树应该是新的右子树根的右子树。</li>
	<li>如果 <code>depth == 1 </code>意味着&nbsp;<code>depth - 1</code>&nbsp;根本没有深度，那么创建一个树节点，值 <code>val </code>作为整个原始树的新根，而原始树就是新根的左子树。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<p><img src="https://assets.leetcode.com/uploads/2021/03/15/addrow-tree.jpg" style="height: 231px; width: 500px;" /></p>

<pre>
<strong>输入:</strong> root = [4,2,6,3,1,5], val = 1, depth = 2
<strong>输出:</strong> [4,1,1,2,null,null,6,3,1,5]</pre>

<p><strong>示例 2:</strong></p>

<p><img src="https://assets.leetcode.com/uploads/2021/03/11/add2-tree.jpg" style="height: 277px; width: 500px;" /></p>

<pre>
<strong>输入:</strong> root = [4,2,null,3,1], val = 1, depth = 3
<strong>输出:</strong>  [4,2,null,1,1,3,null,null,1]
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li>节点数在&nbsp;<code>[1, 10<sup>4</sup>]</code>&nbsp;范围内</li>
	<li>树的深度在&nbsp;<code>[1, 10<sup>4</sup>]</code>范围内</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
	<li><code>-10<sup>5</sup>&nbsp;&lt;= val &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= depth &lt;= the depth of tree + 1</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/add-one-row-to-tree/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/add-one-row-to-tree/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 16 ms | 25.5 MB | 2022/09/19 11:06 |

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

    vector<vector<TreeNode*>> bfs(TreeNode* root){
        queue<TreeNode*> que;
        que.push(root);
        vector<vector<TreeNode*>> ans;

        while(!que.empty()){
            const int n = que.size();
            vector<TreeNode*> tmp;

            for(int i = 0; i < n; i++){
                TreeNode* node = que.front(); que.pop();
                tmp.emplace_back(node);
                if(node->left) que.push(node->left);
                if(node->right) que.push(node->right);
            }
            ans.emplace_back(tmp);
        }
        return ans;
    }
    TreeNode* addOneRow(TreeNode* root, int val, int depth) {
        if(depth == 1){
            TreeNode * head = new TreeNode(val);
            head->left = root;
            return head;
        }

        vector<vector<TreeNode*>> levels = bfs(root);
        // Get the root level of depth
        vector<TreeNode*> level = levels[depth - 2];
        const int n = level.size();
        for(int i = 0; i < n; i++){
            TreeNode* node = level[i];
            TreeNode* l = new TreeNode(val);
            TreeNode* r = new TreeNode(val);

            l->left = node->left;
            r->right = node->right;

            node->left = l;
            node->right = r;
        }

        return root;
    }
};

```
## My Notes - 我的笔记


No notes

