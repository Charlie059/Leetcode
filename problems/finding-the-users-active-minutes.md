
# 1817. Finding the Users Active Minutes - 查找用户活跃分钟数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given the logs for users&#39; actions on LeetCode, and an integer <code>k</code>. The logs are represented by a 2D integer array <code>logs</code> where each <code>logs[i] = [ID<sub>i</sub>, time<sub>i</sub>]</code> indicates that the user with <code>ID<sub>i</sub></code> performed an action at the minute <code>time<sub>i</sub></code>.</p>

<p><strong>Multiple users</strong> can perform actions simultaneously, and a single user can perform <strong>multiple actions</strong> in the same minute.</p>

<p>The <strong>user active minutes (UAM)</strong> for a given user is defined as the <strong>number of unique minutes</strong> in which the user performed an action on LeetCode. A minute can only be counted once, even if multiple actions occur during it.</p>

<p>You are to calculate a <strong>1-indexed</strong> array <code>answer</code> of size <code>k</code> such that, for each <code>j</code> (<code>1 &lt;= j &lt;= k</code>), <code>answer[j]</code> is the <strong>number of users</strong> whose <strong>UAM</strong> equals <code>j</code>.</p>

<p>Return <i>the array </i><code>answer</code><i> as described above</i>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> logs = [[0,5],[1,2],[0,2],[0,5],[1,3]], k = 5
<strong>Output:</strong> [0,2,0,0,0]
<strong>Explanation:</strong>
The user with ID=0 performed actions at minutes 5, 2, and 5 again. Hence, they have a UAM of 2 (minute 5 is only counted once).
The user with ID=1 performed actions at minutes 2 and 3. Hence, they have a UAM of 2.
Since both users have a UAM of 2, answer[2] is 2, and the remaining answer[j] values are 0.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> logs = [[1,1],[2,2],[2,3]], k = 4
<strong>Output:</strong> [1,1,0,0]
<strong>Explanation:</strong>
The user with ID=1 performed a single action at minute 1. Hence, they have a UAM of 1.
The user with ID=2 performed actions at minutes 2 and 3. Hence, they have a UAM of 2.
There is one user with a UAM of 1 and one with a UAM of 2.
Hence, answer[1] = 1, answer[2] = 1, and the remaining values are 0.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= logs.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= ID<sub>i</sub> &lt;= 10<sup>9</sup></code></li>
	<li><code>1 &lt;= time<sub>i</sub> &lt;= 10<sup>5</sup></code></li>
	<li><code>k</code> is in the range <code>[The maximum <strong>UAM</strong> for a user, 10<sup>5</sup>]</code>.</li>
</ul>


### ZH-CN:
<p>给你用户在 LeetCode 的操作日志，和一个整数 <code>k</code> 。日志用一个二维整数数组 <code>logs</code> 表示，其中每个 <code>logs[i] = [ID<sub>i</sub>, time<sub>i</sub>]</code> 表示 ID 为 <code>ID<sub>i</sub></code> 的用户在 <code>time<sub>i</sub></code> 分钟时执行了某个操作。</p>

<p><strong>多个用户 </strong>可以同时执行操作，单个用户可以在同一分钟内执行 <strong>多个操作</strong> 。</p>

<p>指定用户的<strong> 用户活跃分钟数（user active minutes，UAM）</strong> 定义为用户对 LeetCode 执行操作的 <strong>唯一分钟数</strong> 。 即使一分钟内执行多个操作，也只能按一分钟计数。</p>

<p>请你统计用户活跃分钟数的分布情况，统计结果是一个长度为 <code>k</code> 且 <strong>下标从 1 开始计数</strong> 的数组 <code>answer</code> ，对于每个 <code>j</code>（<code>1 <= j <= k</code>），<code>answer[j]</code> 表示 <strong>用户活跃分钟数</strong> 等于 <code>j</code> 的用户数。</p>

<p>返回上面描述的答案数组<i> </i><code>answer</code><i> </i>。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>logs = [[0,5],[1,2],[0,2],[0,5],[1,3]], k = 5
<strong>输出：</strong>[0,2,0,0,0]
<strong>解释：</strong>
ID=0 的用户执行操作的分钟分别是：5 、2 和 5 。因此，该用户的用户活跃分钟数为 2（分钟 5 只计数一次）
ID=1 的用户执行操作的分钟分别是：2 和 3 。因此，该用户的用户活跃分钟数为 2
2 个用户的用户活跃分钟数都是 2 ，answer[2] 为 2 ，其余 answer[j] 的值都是 0
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>logs = [[1,1],[2,2],[2,3]], k = 4
<strong>输出：</strong>[1,1,0,0]
<strong>解释：</strong>
ID=1 的用户仅在分钟 1 执行单个操作。因此，该用户的用户活跃分钟数为 1
ID=2 的用户执行操作的分钟分别是：2 和 3 。因此，该用户的用户活跃分钟数为 2
1 个用户的用户活跃分钟数是 1 ，1 个用户的用户活跃分钟数是 2 
因此，answer[1] = 1 ，answer[2] = 1 ，其余的值都是 0
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= logs.length <= 10<sup>4</sup></code></li>
	<li><code>0 <= ID<sub>i</sub> <= 10<sup>9</sup></code></li>
	<li><code>1 <= time<sub>i</sub> <= 10<sup>5</sup></code></li>
	<li><code>k</code> 的取值范围是 <code>[用户的最大用户活跃分钟数, 10<sup>5</sup>]</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/finding-the-users-active-minutes/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/finding-the-users-active-minutes/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| javascript  | 188 ms | 60.9 MB | 2023/01/19 14:32 |

```javascript

/**
 * @param {number[][]} logs
 * @param {number} k
 * @return {number[]}
 */
var findingUsersActiveMinutes = function(logs, k) {
    const mp = new Map();
    const ans = new Array(k).fill(0);

    for(const [UID, time] of logs){
        if(!mp.has(UID)) mp.set(UID, new Set());
        mp.get(UID).add(time);
    }

    for(const st of mp.values()) ans[st.size - 1]++;
    
    return ans;
};

```
## My Notes - 我的笔记


No notes

