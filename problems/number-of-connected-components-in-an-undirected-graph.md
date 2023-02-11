
# 323. Number of Connected Components in an Undirected Graph - 无向图中连通分量的数目

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Depth First Search-深度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Breadth First Search-广度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Union Find-并查集-blue.svg">   <img src="https://img.shields.io/badge/Graph-图-blue.svg">  


## Description - 题目描述

### EN:
<p>You have a graph of <code>n</code> nodes. You are given an integer <code>n</code> and an array <code>edges</code> where <code>edges[i] = [a<sub>i</sub>, b<sub>i</sub>]</code> indicates that there is an edge between <code>a<sub>i</sub></code> and <code>b<sub>i</sub></code> in the graph.</p>

<p>Return <em>the number of connected components in the graph</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/14/conn1-graph.jpg" style="width: 382px; height: 222px;" />
<pre>
<strong>Input:</strong> n = 5, edges = [[0,1],[1,2],[3,4]]
<strong>Output:</strong> 2
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/14/conn2-graph.jpg" style="width: 382px; height: 222px;" />
<pre>
<strong>Input:</strong> n = 5, edges = [[0,1],[1,2],[2,3],[3,4]]
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2000</code></li>
	<li><code>1 &lt;= edges.length &lt;= 5000</code></li>
	<li><code>edges[i].length == 2</code></li>
	<li><code>0 &lt;= a<sub>i</sub> &lt;= b<sub>i</sub> &lt; n</code></li>
	<li><code>a<sub>i</sub> != b<sub>i</sub></code></li>
	<li>There are no repeated edges.</li>
</ul>


### ZH-CN:
<p>你有一个包含&nbsp;<code>n</code> 个节点的图。给定一个整数 <code>n</code> 和一个数组&nbsp;<code>edges</code>&nbsp;，其中&nbsp;<code>edges[i] = [a<sub>i</sub>, b<sub>i</sub>]</code>&nbsp;表示图中&nbsp;<code>a<sub>i</sub></code>&nbsp;和&nbsp;<code>b<sub>i</sub></code>&nbsp;之间有一条边。</p>

<p>返回 <em>图中已连接分量的数目</em>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<p><img src="https://assets.leetcode.com/uploads/2021/03/14/conn1-graph.jpg" /></p>

<pre>
<strong>输入: </strong><code>n = 5</code>, <code>edges = [[0, 1], [1, 2], [3, 4]]</code>
<strong>输出: </strong>2
</pre>

<p><strong>示例 2:</strong></p>

<p><img src="https://assets.leetcode.com/uploads/2021/03/14/conn2-graph.jpg" /></p>

<pre>
<strong>输入: </strong><code>n = 5,</code> <code>edges = [[0,1], [1,2], [2,3], [3,4]]</code>
<strong>输出:&nbsp;&nbsp;</strong>1</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 2000</code></li>
	<li><code>1 &lt;= edges.length &lt;= 5000</code></li>
	<li><code>edges[i].length == 2</code></li>
	<li><code>0 &lt;= a<sub>i</sub>&nbsp;&lt;= b<sub>i</sub>&nbsp;&lt; n</code></li>
	<li><code>a<sub>i</sub>&nbsp;!= b<sub>i</sub></code></li>
	<li><code>edges</code> 中不会出现重复的边</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/number-of-connected-components-in-an-undirected-graph/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 32 ms | 15.5 MB | 2022/10/21 21:42 |

```cpp

class Solution {
public:
    unordered_map<int, vector<int>> hm;
    vector<bool> nodes;
    bool bfs(int currNode){
        if(nodes[currNode] == 1) return false;
        queue<int> que;
        que.push(currNode);

        while(!que.empty()){
            int curr = que.front(); que.pop();

            nodes[curr] = 1; // mark as vistied

            auto neighbor = hm[curr];
            const int n = neighbor.size();

            for(int i = 0 ; i < n; i++){
                if(nodes[neighbor[i]] == 0) que.push(neighbor[i]);
            }
        }
        return true;
    }
    int countComponents(int n, vector<vector<int>>& edges) {
        int ans = 0;
        const int m = edges.size();
        nodes.resize(n, 0);

        // init
        for(int i = 0; i < m; i++){
            hm[edges[i][0]].push_back(edges[i][1]);
            hm[edges[i][1]].push_back(edges[i][0]);
        }

        for(int i = 0; i < m; i++){
            if(bfs(edges[i][0])) ans++;
        }

        for(int i = 0; i < n; i++){
            if(nodes[i] == 0) ans++;
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

