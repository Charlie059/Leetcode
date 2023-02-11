
# 1138. Alphabet Board Path - 字母板上的路径

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>On an alphabet board, we start at position <code>(0, 0)</code>, corresponding to character&nbsp;<code>board[0][0]</code>.</p>

<p>Here, <code>board = [&quot;abcde&quot;, &quot;fghij&quot;, &quot;klmno&quot;, &quot;pqrst&quot;, &quot;uvwxy&quot;, &quot;z&quot;]</code>, as shown in the diagram below.</p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2019/07/28/azboard.png" style="width: 250px; height: 317px;" /></p>

<p>We may make the following moves:</p>

<ul>
	<li><code>&#39;U&#39;</code> moves our position up one row, if the position exists on the board;</li>
	<li><code>&#39;D&#39;</code> moves our position down one row, if the position exists on the board;</li>
	<li><code>&#39;L&#39;</code> moves our position left one column, if the position exists on the board;</li>
	<li><code>&#39;R&#39;</code> moves our position right one column, if the position exists on the board;</li>
	<li><code>&#39;!&#39;</code>&nbsp;adds the character <code>board[r][c]</code> at our current position <code>(r, c)</code>&nbsp;to the&nbsp;answer.</li>
</ul>

<p>(Here, the only positions that exist on the board are positions with letters on them.)</p>

<p>Return a sequence of moves that makes our answer equal to <code>target</code>&nbsp;in the minimum number of moves.&nbsp; You may return any path that does so.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> target = "leet"
<strong>Output:</strong> "DDR!UURRR!!DDD!"
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> target = "code"
<strong>Output:</strong> "RR!DDRR!UUL!R!"
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= target.length &lt;= 100</code></li>
	<li><code>target</code> consists only of English lowercase letters.</li>
</ul>

### ZH-CN:
<p>我们从一块字母板上的位置&nbsp;<code>(0, 0)</code>&nbsp;出发，该坐标对应的字符为&nbsp;<code>board[0][0]</code>。</p>

<p>在本题里，字母板为<code>board = ["abcde", "fghij", "klmno", "pqrst", "uvwxy", "z"]</code>，如下所示。</p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2019/07/28/azboard.png" style="width: 300px;" /></p>

<p>我们可以按下面的指令规则行动：</p>

<ul>
	<li>如果方格存在，<code>'U'</code>&nbsp;意味着将我们的位置上移一行；</li>
	<li>如果方格存在，<code>'D'</code>&nbsp;意味着将我们的位置下移一行；</li>
	<li>如果方格存在，<code>'L'</code>&nbsp;意味着将我们的位置左移一列；</li>
	<li>如果方格存在，<code>'R'</code>&nbsp;意味着将我们的位置右移一列；</li>
	<li><code>'!'</code>&nbsp;会把在我们当前位置 <code>(r, c)</code> 的字符&nbsp;<code>board[r][c]</code>&nbsp;添加到答案中。</li>
</ul>

<p>（注意，字母板上只存在有字母的位置。）</p>

<p>返回指令序列，用最小的行动次数让答案和目标&nbsp;<code>target</code>&nbsp;相同。你可以返回任何达成目标的路径。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>target = "leet"
<strong>输出：</strong>"DDR!UURRR!!DDD!"
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>target = "code"
<strong>输出：</strong>"RR!DDRR!UUL!R!"
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= target.length &lt;= 100</code></li>
	<li><code>target</code>&nbsp;仅含有小写英文字母。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/alphabet-board-path/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/alphabet-board-path/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 12 ms | 11.6 MB | 2023/02/11 12:18 |

```cpp

class Solution {
public:
    vector<vector<int>> dirs = {{0, 1}, {0, -1}, {1, 0}, {-1, 0}};

    pair<string, vector<int>> bfs(int x, int y, int idx, const string& s,vector<vector<char>>& graph, vector<vector<int>>& vis){
        const int m = graph.size();
        const int n = graph[0].size();

        queue<pair<vector<int>, string>> q;
        q.push({{x, y}, ""});

        while(!q.empty()){
            auto p = q.front(); q.pop();
            x = p.first[0], y = p.first[1];
            char c = graph[x][y];
            string str = p.second;

            if(c == s[idx])   return {str + '!', {x, y}};

            for(int i = 0; i < 4; i++){
                int dx = x + dirs[i][0];
                int dy = y + dirs[i][1];

                if(0 <= dx && dx < m && 0 <= dy && dy < n){
                    if(dx == 5 && dy != 0) continue;
                    if(vis[dx][dy]) continue;

                    if(i == 0) q.push({{dx, dy}, str + 'R'});
                    else if(i == 1) q.push({{dx, dy}, str + 'L'});
                    else if(i == 2) q.push({{dx, dy}, str + 'D'});
                    else if(i == 3) q.push({{dx, dy}, str + 'U'});
                    vis[dx][dy] = 1;
                }
            }
        }
        return {};
    }

    string alphabetBoardPath(string target) {
        const int n = target.length();

        vector<vector<char>> graph = {
            {'a', 'b', 'c', 'd', 'e'},
            {'f', 'g', 'h', 'i', 'j'},
            {'k', 'l', 'm', 'n', 'o'},
            {'p', 'q', 'r', 's', 't'},
            {'u', 'v', 'w', 'x', 'y'},
            {'z', '*', '*', '*', '*'},
        };

        string ans = "";
        int x = 0, y = 0;
        for(int i = 0; i < n; i++){
            vector<vector<int>> vis(graph.size(), vector<int>(graph[0].size(), 0));
            auto p = bfs(x, y, i, target, graph, vis);
            // Update x and y
            x = p.second[0];
            y = p.second[1];

            // Update ans
            ans += p.first;
        }
        return ans;
    }
};


```
## My Notes - 我的笔记


No notes

