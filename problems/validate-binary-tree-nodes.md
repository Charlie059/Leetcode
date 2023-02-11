
# 1361. Validate Binary Tree Nodes - 验证二叉树

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Tree-树-blue.svg">   <img src="https://img.shields.io/badge/Depth First Search-深度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Breadth First Search-广度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Union Find-并查集-blue.svg">   <img src="https://img.shields.io/badge/Graph-图-blue.svg">   <img src="https://img.shields.io/badge/Binary Tree-二叉树-blue.svg">  


## Description - 题目描述

### EN:
<p>You have <code>n</code> binary tree nodes numbered from <code>0</code> to <code>n - 1</code> where node <code>i</code> has two children <code>leftChild[i]</code> and <code>rightChild[i]</code>, return <code>true</code> if and only if <strong>all</strong> the given nodes form <strong>exactly one</strong> valid binary tree.</p>

<p>If node <code>i</code> has no left child then <code>leftChild[i]</code> will equal <code>-1</code>, similarly for the right child.</p>

<p>Note that the nodes have no values and that we only use the node numbers in this problem.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/08/23/1503_ex1.png" style="width: 195px; height: 287px;" />
<pre>
<strong>Input:</strong> n = 4, leftChild = [1,-1,3,-1], rightChild = [2,-1,-1,-1]
<strong>Output:</strong> true
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/08/23/1503_ex2.png" style="width: 183px; height: 272px;" />
<pre>
<strong>Input:</strong> n = 4, leftChild = [1,-1,3,-1], rightChild = [2,3,-1,-1]
<strong>Output:</strong> false
</pre>

<p><strong class="example">Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/08/23/1503_ex3.png" style="width: 82px; height: 174px;" />
<pre>
<strong>Input:</strong> n = 2, leftChild = [1,0], rightChild = [-1,-1]
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == leftChild.length == rightChild.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>4</sup></code></li>
	<li><code>-1 &lt;= leftChild[i], rightChild[i] &lt;= n - 1</code></li>
</ul>


### ZH-CN:
<p>二叉树上有 <code>n</code>&nbsp;个节点，按从&nbsp;<code>0</code>&nbsp;到 <code>n - 1</code>&nbsp;编号，其中节点&nbsp;<code>i</code>&nbsp;的两个子节点分别是&nbsp;<code>leftChild[i]</code>&nbsp;和&nbsp;<code>rightChild[i]</code>。</p>

<p>只有 <strong>所有</strong> 节点能够形成且 <strong>只</strong> 形成 <strong>一颗</strong>&nbsp;有效的二叉树时，返回&nbsp;<code>true</code>；否则返回 <code>false</code>。</p>

<p>如果节点&nbsp;<code>i</code>&nbsp;没有左子节点，那么&nbsp;<code>leftChild[i]</code>&nbsp;就等于&nbsp;<code>-1</code>。右子节点也符合该规则。</p>

<p>注意：节点没有值，本问题中仅仅使用节点编号。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/02/23/1503_ex1.png" style="height: 287px; width: 195px;"></strong></p>

<pre><strong>输入：</strong>n = 4, leftChild = [1,-1,3,-1], rightChild = [2,-1,-1,-1]
<strong>输出：</strong>true
</pre>

<p><strong>示例 2：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/02/23/1503_ex2.png" style="height: 272px; width: 183px;"></strong></p>

<pre><strong>输入：</strong>n = 4, leftChild = [1,-1,3,-1], rightChild = [2,3,-1,-1]
<strong>输出：</strong>false
</pre>

<p><strong>示例 3：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/02/23/1503_ex3.png" style="height: 174px; width: 82px;"></strong></p>

<pre><strong>输入：</strong>n = 2, leftChild = [1,0], rightChild = [-1,-1]
<strong>输出：</strong>false
</pre>

<p><strong>示例 4：</strong></p>

<p><strong><img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/02/23/1503_ex4.png" style="height: 191px; width: 470px;"></strong></p>

<pre><strong>输入：</strong>n = 6, leftChild = [1,-1,-1,4,-1,-1], rightChild = [2,-1,-1,5,-1,-1]
<strong>输出：</strong>false
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10^4</code></li>
	<li><code>leftChild.length == rightChild.length == n</code></li>
	<li><code>-1 &lt;= leftChild[i], rightChild[i] &lt;= n - 1</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/validate-binary-tree-nodes/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/validate-binary-tree-nodes/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 52 ms | 35.5 MB | 2022/08/23 21:48 |

```cpp

class Solution {
public:
    bool validateBinaryTreeNodes(int n, vector<int>& leftChild, vector<int>& rightChild) {
        vector<int> indeg(n, 0);

        for(int i = 0; i < n; i++){
            if(leftChild[i] != -1) indeg[leftChild[i]] += 1;
            if(rightChild[i] != -1) indeg[rightChild[i]] += 1;
        }

        int root = -1;
        int cnt = 0;
        for(int i = 0; i < n; i++){
            if(indeg[i] == 0){
                root = i;
                cnt++;
            }
        }

        if(cnt != 1) return false;

        unordered_set<int> seen;
        queue<int> q;
        seen.insert(root);
        q.push(root);

        while(!q.empty()){
            int u = q.front();
            q.pop();

            if(leftChild[u] != - 1){
                if(seen.count(leftChild[u])) return false;
                seen.insert(leftChild[u]);
                q.push(leftChild[u]);
            }

            if(rightChild[u] != - 1){
                if(seen.count(rightChild[u])) return false;
                seen.insert(rightChild[u]);
                q.push(rightChild[u]);
            }
        }

        return seen.size() == n;
    }
};

```
## My Notes - 我的笔记


No notes

