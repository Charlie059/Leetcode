
# 490. The Maze - 迷宫

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Depth First Search-深度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Breadth First Search-广度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Graph-图-blue.svg">  


## Description - 题目描述

### EN:
<p>There is a ball in a <code>maze</code> with empty spaces (represented as <code>0</code>) and walls (represented as <code>1</code>). The ball can go through the empty spaces by rolling <strong>up, down, left or right</strong>, but it won&#39;t stop rolling until hitting a wall. When the ball stops, it could choose the next direction.</p>

<p>Given the <code>m x n</code> <code>maze</code>, the ball&#39;s <code>start</code> position and the <code>destination</code>, where <code>start = [start<sub>row</sub>, start<sub>col</sub>]</code> and <code>destination = [destination<sub>row</sub>, destination<sub>col</sub>]</code>, return <code>true</code> if the ball can stop at the destination, otherwise return <code>false</code>.</p>

<p>You may assume that <strong>the borders of the maze are all walls</strong> (see examples).</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/31/maze1-1-grid.jpg" style="width: 573px; height: 573px;" />
<pre>
<strong>Input:</strong> maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
<strong>Output:</strong> true
<strong>Explanation:</strong> One possible way is : left -&gt; down -&gt; left -&gt; down -&gt; right -&gt; down -&gt; right.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/31/maze1-2-grid.jpg" style="width: 573px; height: 573px;" />
<pre>
<strong>Input:</strong> maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [3,2]
<strong>Output:</strong> false
<strong>Explanation:</strong> There is no way for the ball to stop at the destination. Notice that you can pass through the destination but you cannot stop there.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> maze = [[0,0,0,0,0],[1,1,0,0,1],[0,0,0,0,0],[0,1,0,0,1],[0,1,0,0,0]], start = [4,3], destination = [0,1]
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == maze.length</code></li>
	<li><code>n == maze[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 100</code></li>
	<li><code>maze[i][j]</code> is <code>0</code> or <code>1</code>.</li>
	<li><code>start.length == 2</code></li>
	<li><code>destination.length == 2</code></li>
	<li><code>0 &lt;= start<sub>row</sub>, destination<sub>row</sub> &lt;= m</code></li>
	<li><code>0 &lt;= start<sub>col</sub>, destination<sub>col</sub> &lt;= n</code></li>
	<li>Both the ball and the destination exist in an empty space, and they will not be in the same position initially.</li>
	<li>The maze contains <strong>at least 2 empty spaces</strong>.</li>
</ul>


### ZH-CN:
由空地（用 <code>0</code> 表示）和墙（用 <code>1</code> 表示）组成的迷宫 <code>maze</code> 中有一个球。球可以途经空地向<strong> 上、下、左、右 </strong>四个方向滚动，且在遇到墙壁前不会停止滚动。当球停下时，可以选择向下一个方向滚动。
<div class="top-view__1vxA">
<div class="original__bRMd">
<div>
<p>给你一个大小为 <code>m x n</code> 的迷宫 <code>maze</code> ，以及球的初始位置 <code>start</code> 和目的地 <code>destination</code> ，其中 <code>start = [start<sub>row</sub>, start<sub>col</sub>]</code> 且 <code>destination = [destination<sub>row</sub>, destination<sub>col</sub>]</code> 。请你判断球能否在目的地停下：如果可以，返回 <code>true</code> ；否则，返回 <code>false</code> 。</p>

<p>你可以 <strong>假定迷宫的边缘都是墙壁</strong>（参考示例）。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/31/maze1-1-grid.jpg" style="width: 573px; height: 573px;" />
<pre>
<strong>输入：</strong>maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
<strong>输出：</strong>true
<strong>解释：</strong>一种可能的路径是 : 左 -> 下 -> 左 -> 下 -> 右 -> 下 -> 右。
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/31/maze1-2-grid.jpg" style="width: 573px; height: 573px;" />
<pre>
<strong>输入：</strong>maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [3,2]
<strong>输出：</strong>false
<strong>解释：</strong>不存在能够使球停在目的地的路径。注意，球可以经过目的地，但无法在那里停驻。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>maze = [[0,0,0,0,0],[1,1,0,0,1],[0,0,0,0,0],[0,1,0,0,1],[0,1,0,0,0]], start = [4,3], destination = [0,1]
<strong>输出：</strong>false
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>m == maze.length</code></li>
	<li><code>n == maze[i].length</code></li>
	<li><code>1 <= m, n <= 100</code></li>
	<li><code>maze[i][j]</code> is <code>0</code> or <code>1</code>.</li>
	<li><code>start.length == 2</code></li>
	<li><code>destination.length == 2</code></li>
	<li><code>0 <= start<sub>row</sub>, destination<sub>row</sub> <= m</code></li>
	<li><code>0 <= start<sub>col</sub>, destination<sub>col</sub> <= n</code></li>
	<li>球和目的地都在空地上，且初始时它们不在同一位置</li>
	<li>迷宫 <strong>至少包括 2 块空地</strong></li>
</ul>
</div>
</div>
</div>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/the-maze/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/the-maze/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 60 ms | 53.5 MB | 2022/08/22 22:35 |

```cpp

class Solution {
public:
    bool dfs(vector<vector<int>>& maze, vector<int> start, vector<int>& destination, vector<vector<bool>> & visited){
        if(visited[start[0]][start[1]]) return false;
        if(start[0] == destination[0] && start[1] == destination[1]) return true;

        // Mark vistied to be true
        visited[start[0]][start[1]] = true;
        
        // Right
        int right = start[1] + 1, left = start[1] - 1, up = start[0] - 1, down = start[0] + 1;
        while(right < maze[0].size() && maze[start[0]][right] == 0) right++;
        if(dfs(maze, {start[0], right - 1}, destination, visited)) return true;

        while(left >= 0 && maze[start[0]][left] == 0) left--;
        if(dfs(maze, {start[0], left + 1}, destination, visited)) return true;

        while(up >= 0 && maze[up][start[1]] == 0) up--;
        if(dfs(maze, {up + 1, start[1]}, destination, visited)) return true;

        while(down < maze.size() && maze[down][start[1]] == 0) down++;
        if(dfs(maze, {down - 1, start[1]}, destination, visited)) return true;

        return false;
    }
    bool hasPath(vector<vector<int>>& maze, vector<int>& start, vector<int>& destination) {
        const int m = maze.size();
        const int n = maze[0].size();
        vector<vector<bool>> visited(m, vector<bool>(n, false));
        return dfs(maze, start, destination, visited);
    }
};

```
## My Notes - 我的笔记


No notes

