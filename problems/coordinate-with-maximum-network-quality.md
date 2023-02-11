
# 1620. Coordinate With Maximum Network Quality - 网络信号最好的坐标

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Enumeration-枚举-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given an array of network towers <code>towers</code>, where <code>towers[i] = [x<sub>i</sub>, y<sub>i</sub>, q<sub>i</sub>]</code> denotes the <code>i<sup>th</sup></code> network tower with location <code>(x<sub>i</sub>, y<sub>i</sub>)</code> and quality factor <code>q<sub>i</sub></code>. All the coordinates are <strong>integral coordinates</strong> on the X-Y plane, and the distance between the two coordinates is the <strong>Euclidean distance</strong>.</p>

<p>You are also given an integer <code>radius</code> where a tower is <strong>reachable</strong> if the distance is <strong>less than or equal to</strong> <code>radius</code>. Outside that distance, the signal becomes garbled, and the tower is <strong>not reachable</strong>.</p>

<p>The signal quality of the <code>i<sup>th</sup></code> tower at a coordinate <code>(x, y)</code> is calculated with the formula <code>&lfloor;q<sub>i</sub> / (1 + d)&rfloor;</code>, where <code>d</code> is the distance between the tower and the coordinate. The <strong>network quality</strong> at a coordinate is the sum of the signal qualities from all the <strong>reachable</strong> towers.</p>

<p>Return <em>the array </em><code>[c<sub>x</sub>, c<sub>y</sub>]</code><em> representing the <strong>integral</strong> coordinate </em><code>(c<sub>x</sub>, c<sub>y</sub>)</code><em> where the <strong>network quality</strong> is maximum. If there are multiple coordinates with the same <strong>network quality</strong>, return the lexicographically minimum <strong>non-negative</strong> coordinate.</em></p>

<p><strong>Note:</strong></p>

<ul>
	<li>A coordinate <code>(x1, y1)</code> is lexicographically smaller than <code>(x2, y2)</code> if either:

	<ul>
		<li><code>x1 &lt; x2</code>, or</li>
		<li><code>x1 == x2</code> and <code>y1 &lt; y2</code>.</li>
	</ul>
	</li>
	<li><code>&lfloor;val&rfloor;</code> is the greatest integer less than or equal to <code>val</code> (the floor function).</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/22/untitled-diagram.png" style="width: 176px; height: 176px;" />
<pre>
<strong>Input:</strong> towers = [[1,2,5],[2,1,7],[3,1,9]], radius = 2
<strong>Output:</strong> [2,1]
<strong>Explanation:</strong> At coordinate (2, 1) the total quality is 13.
- Quality of 7 from (2, 1) results in &lfloor;7 / (1 + sqrt(0)&rfloor; = &lfloor;7&rfloor; = 7
- Quality of 5 from (1, 2) results in &lfloor;5 / (1 + sqrt(2)&rfloor; = &lfloor;2.07&rfloor; = 2
- Quality of 9 from (3, 1) results in &lfloor;9 / (1 + sqrt(1)&rfloor; = &lfloor;4.5&rfloor; = 4
No other coordinate has a higher network quality.</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> towers = [[23,11,21]], radius = 9
<strong>Output:</strong> [23,11]
<strong>Explanation:</strong> Since there is only one tower, the network quality is highest right at the tower&#39;s location.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> towers = [[1,2,13],[2,1,7],[0,1,9]], radius = 2
<strong>Output:</strong> [1,2]
<strong>Explanation:</strong> Coordinate (1, 2) has the highest network quality.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= towers.length &lt;= 50</code></li>
	<li><code>towers[i].length == 3</code></li>
	<li><code>0 &lt;= x<sub>i</sub>, y<sub>i</sub>, q<sub>i</sub> &lt;= 50</code></li>
	<li><code>1 &lt;= radius &lt;= 50</code></li>
</ul>


### ZH-CN:
<p>给你一个数组 <code>towers</code>&nbsp;和一个整数 <code>radius</code> 。</p>

<p>数组&nbsp; <code>towers</code>&nbsp; 中包含一些网络信号塔，其中&nbsp;<code>towers[i] = [x<sub>i</sub>, y<sub>i</sub>, q<sub>i</sub>]</code>&nbsp;表示第&nbsp;<code>i</code>&nbsp;个网络信号塔的坐标是&nbsp;<code>(x<sub>i</sub>, y<sub>i</sub>)</code>&nbsp;且信号强度参数为&nbsp;<code>q<sub>i</sub></code><sub>&nbsp;</sub>。所有坐标都是在&nbsp; X-Y 坐标系内的&nbsp;<strong>整数</strong>&nbsp;坐标。两个坐标之间的距离用 <strong>欧几里得距离</strong>&nbsp;计算。</p>

<p>整数&nbsp;<code>radius</code>&nbsp;表示一个塔 <strong>能到达&nbsp;</strong>的 <strong>最远距离</strong>&nbsp;。如果一个坐标跟塔的距离在 <code>radius</code>&nbsp;以内，那么该塔的信号可以到达该坐标。在这个范围以外信号会很微弱，所以 <code>radius</code>&nbsp;以外的距离该塔是 <strong>不能到达的</strong>&nbsp;。</p>

<p>如果第 <code>i</code>&nbsp;个塔能到达 <code>(x, y)</code>&nbsp;，那么该塔在此处的信号为&nbsp;<code>⌊q<sub>i</sub> / (1 + d)⌋</code>&nbsp;，其中&nbsp;<code>d</code>&nbsp;是塔跟此坐标的距离。一个坐标的 <b>信号强度</b> 是所有 <strong>能到达&nbsp;</strong>该坐标的塔的信号强度之和。</p>

<p>请你返回数组 <code>[c<sub>x</sub>, c<sub>y</sub>]</code> ，表示 <strong>信号强度</strong> 最大的 <strong>整数</strong> 坐标点&nbsp;<code>(c<sub>x</sub>, c<sub>y</sub>)</code> 。如果有多个坐标网络信号一样大，请你返回字典序最小的 <strong>非负</strong> 坐标。</p>

<p><strong>注意：</strong></p>

<ul>
	<li>坐标&nbsp;<code>(x1, y1)</code>&nbsp;字典序比另一个坐标&nbsp;<code>(x2, y2)</code> 小，需满足以下条件之一：

	<ul>
		<li>要么&nbsp;<code>x1 &lt; x2</code>&nbsp;，</li>
		<li>要么&nbsp;<code>x1 == x2</code> 且&nbsp;<code>y1 &lt; y2</code>&nbsp;。</li>
	</ul>
	</li>
	<li><code>⌊val⌋</code>&nbsp;表示小于等于&nbsp;<code>val</code>&nbsp;的最大整数（向下取整函数）。</li>
</ul>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/10/17/untitled-diagram.png" style="width: 176px; height: 176px;" />
<pre>
<b>输入：</b>towers = [[1,2,5],[2,1,7],[3,1,9]], radius = 2
<b>输出：</b>[2,1]
<strong>解释：</strong>
坐标 (2, 1) 信号强度之和为 13
- 塔 (2, 1) 强度参数为 7 ，在该点强度为 ⌊7 / (1 + sqrt(0)⌋ = ⌊7⌋ = 7
- 塔 (1, 2) 强度参数为 5 ，在该点强度为 ⌊5 / (1 + sqrt(2)⌋ = ⌊2.07⌋ = 2
- 塔 (3, 1) 强度参数为 9 ，在该点强度为 ⌊9 / (1 + sqrt(1)⌋ = ⌊4.5⌋ = 4
没有别的坐标有更大的信号强度。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>towers = [[23,11,21]], radius = 9
<b>输出：</b>[23,11]
<strong>解释：</strong>由于仅存在一座信号塔，所以塔的位置信号强度最大。</pre>

<p><strong>示例 3：</strong></p>

<pre>
<b>输入：</b>towers = [[1,2,13],[2,1,7],[0,1,9]], radius = 2
<b>输出：</b>[1,2]
<strong>解释：</strong>坐标 (1, 2) 的信号强度最大。</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= towers.length &lt;= 50</code></li>
	<li><code>towers[i].length == 3</code></li>
	<li><code>0 &lt;= x<sub>i</sub>, y<sub>i</sub>, q<sub>i</sub> &lt;= 50</code></li>
	<li><code>1 &lt;= radius &lt;= 50</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/coordinate-with-maximum-network-quality/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/coordinate-with-maximum-network-quality/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 76 ms | 8.6 MB | 2022/11/01 23:20 |

```cpp

class Solution {
public:
    vector<int> bestCoordinate(vector<vector<int>>& towers, int radius) {
        // Get the max x and y
        const int n = towers.size();
        int maxX = INT_MIN, maxY = INT_MIN;
        for(int i = 0; i < n; i++){
            maxX = max(maxX, towers[i][0]);
            maxY = max(maxY, towers[i][1]);          
        }

        int x = 0, y = 0;
        int maxQuilty = 0;
        for(int i = 0; i <= maxX; i++){
            for(int j = 0; j <= maxY; j++){
                int quilty = 0;
                for(int k = 0; k < n; k++){
                    int squareDist = (towers[k][0] - i) * (towers[k][0] - i) + (towers[k][1] - j) * (towers[k][1] - j);
                    if(squareDist <= radius * radius){
                        double dist = sqrt((double)squareDist);
                        quilty += floor((double)towers[k][2] / (1 + dist));
                    }
                }

                if(quilty > maxQuilty){
                    x = i;
                    y = j;
                    maxQuilty = quilty;
                }
            }
        }
        return {x, y};
    }
};

```
## My Notes - 我的笔记


No notes

