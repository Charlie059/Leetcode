
# 539. Minimum Time Difference - 最小时间差

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Sorting-排序-blue.svg">  


## Description - 题目描述

### EN:
Given a list of 24-hour clock time points in <strong>&quot;HH:MM&quot;</strong> format, return <em>the minimum <b>minutes</b> difference between any two time-points in the list</em>.
<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> timePoints = ["23:59","00:00"]
<strong>Output:</strong> 1
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> timePoints = ["00:00","23:59","00:00"]
<strong>Output:</strong> 0
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= timePoints.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>timePoints[i]</code> is in the format <strong>&quot;HH:MM&quot;</strong>.</li>
</ul>


### ZH-CN:
<p>给定一个 24 小时制（小时:分钟 <strong>"HH:MM"</strong>）的时间列表，找出列表中任意两个时间的最小时间差并以分钟数表示。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>timePoints = ["23:59","00:00"]
<strong>输出：</strong>1
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>timePoints = ["00:00","23:59","00:00"]
<strong>输出：</strong>0
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 &lt;= timePoints.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>timePoints[i]</code> 格式为 <strong>"HH:MM"</strong></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/minimum-time-difference/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/minimum-time-difference/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 13 MB | 2022/07/23 23:10 |

```cpp

class Solution {
public:
    int convertToMins(string time){
        int hours = stoi(time.substr(0, 2));
        int mins = stoi(time.substr(3, 2));
        return hours * 60 + mins;
    }
    int findMinDifference(vector<string>& timePoints) {
        const int n = timePoints.size();
        vector<int>times(n, 0);
        for(int i = 0; i < n; i++){
            times[i] = convertToMins(timePoints[i]);
        }

        sort(times.begin(), times.end());
        int ans = INT_MAX;

        for(int i = 0; i < n - 1; i++){
            ans = min(ans, abs(times[i] - times[i + 1]));
        }

        ans = min(ans, abs(times[0] - times[n - 1] + 1440));
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

