
# 495. Teemo Attacking - 提莫攻击

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Simulation-模拟-blue.svg">  


## Description - 题目描述

### EN:
<p>Our hero Teemo is attacking an enemy Ashe with poison attacks! When Teemo attacks Ashe, Ashe gets poisoned for a exactly <code>duration</code> seconds. More formally, an attack at second <code>t</code> will mean Ashe is poisoned during the <strong>inclusive</strong> time interval <code>[t, t + duration - 1]</code>. If Teemo attacks again <strong>before</strong> the poison effect ends, the timer for it is <strong>reset</strong>, and the poison effect will end <code>duration</code> seconds after the new attack.</p>

<p>You are given a <strong>non-decreasing</strong> integer array <code>timeSeries</code>, where <code>timeSeries[i]</code> denotes that Teemo attacks Ashe at second <code>timeSeries[i]</code>, and an integer <code>duration</code>.</p>

<p>Return <em>the <strong>total</strong> number of seconds that Ashe is poisoned</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> timeSeries = [1,4], duration = 2
<strong>Output:</strong> 4
<strong>Explanation:</strong> Teemo&#39;s attacks on Ashe go as follows:
- At second 1, Teemo attacks, and Ashe is poisoned for seconds 1 and 2.
- At second 4, Teemo attacks, and Ashe is poisoned for seconds 4 and 5.
Ashe is poisoned for seconds 1, 2, 4, and 5, which is 4 seconds in total.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> timeSeries = [1,2], duration = 2
<strong>Output:</strong> 3
<strong>Explanation:</strong> Teemo&#39;s attacks on Ashe go as follows:
- At second 1, Teemo attacks, and Ashe is poisoned for seconds 1 and 2.
- At second 2 however, Teemo attacks again and resets the poison timer. Ashe is poisoned for seconds 2 and 3.
Ashe is poisoned for seconds 1, 2, and 3, which is 3 seconds in total.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= timeSeries.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= timeSeries[i], duration &lt;= 10<sup>7</sup></code></li>
	<li><code>timeSeries</code> is sorted in <strong>non-decreasing</strong> order.</li>
</ul>


### ZH-CN:
<p>在《英雄联盟》的世界中，有一个叫 “提莫” 的英雄。他的攻击可以让敌方英雄艾希（编者注：寒冰射手）进入中毒状态。</p>

<p>当提莫攻击艾希，艾希的中毒状态正好持续&nbsp;<code>duration</code> 秒。</p>

<p>正式地讲，提莫在 <code>t</code> 发起发起攻击意味着艾希在时间区间 <code>[t, t + duration - 1]</code>（含 <code>t</code> 和 <code>t + duration - 1</code>）处于中毒状态。如果提莫在中毒影响结束 <strong>前</strong> 再次攻击，中毒状态计时器将会 <strong>重置</strong> ，在新的攻击之后，中毒影响将会在 <code>duration</code> 秒后结束。</p>

<p>给你一个 <strong>非递减</strong> 的整数数组 <code>timeSeries</code> ，其中 <code>timeSeries[i]</code> 表示提莫在 <code>timeSeries[i]</code> 秒时对艾希发起攻击，以及一个表示中毒持续时间的整数 <code>duration</code> 。</p>

<p>返回艾希处于中毒状态的 <strong>总</strong> 秒数。</p>
&nbsp;

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>timeSeries = [1,4], duration = 2
<strong>输出：</strong>4
<strong>解释：</strong>提莫攻击对艾希的影响如下：
- 第 1 秒，提莫攻击艾希并使其立即中毒。中毒状态会维持 2 秒，即第 1 秒和第 2 秒。
- 第 4 秒，提莫再次攻击艾希，艾希中毒状态又持续 2 秒，即第 4 秒和第 5 秒。
艾希在第 1、2、4、5 秒处于中毒状态，所以总中毒秒数是 4 。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>timeSeries = [1,2], duration = 2
<strong>输出：</strong>3
<strong>解释：</strong>提莫攻击对艾希的影响如下：
- 第 1 秒，提莫攻击艾希并使其立即中毒。中毒状态会维持 2 秒，即第 1 秒和第 2 秒。
- 第 2 秒，提莫再次攻击艾希，并重置中毒计时器，艾希中毒状态需要持续 2 秒，即第 2 秒和第 3 秒。
艾希在第 1、2、3 秒处于中毒状态，所以总中毒秒数是 3 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= timeSeries.length &lt;= 10<sup>4</sup></code></li>
	<li><code>0 &lt;= timeSeries[i], duration &lt;= 10<sup>7</sup></code></li>
	<li><code>timeSeries</code> 按 <strong>非递减</strong> 顺序排列</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/teemo-attacking/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/teemo-attacking/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 36 ms | 25.2 MB | 2022/11/12 17:45 |

```cpp

class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        const int n = timeSeries.size();

        int exp = 0;
        int ans = 0;
        for(int i = 0; i < n; i++){
            if(exp <= timeSeries[i]){
                exp = timeSeries[i] + duration;
                ans += duration;
            }
            else{
                ans += duration - (exp - timeSeries[i]);
                exp = timeSeries[i] + duration;
            }
        }
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

