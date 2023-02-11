
# 401. Binary Watch - 二进制手表

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Bit Manipulation-位运算-blue.svg">   <img src="https://img.shields.io/badge/Backtracking-回溯-blue.svg">  


## Description - 题目描述

### EN:
<p>A binary watch has 4 LEDs on the top to represent the hours (0-11), and 6 LEDs on the bottom to represent&nbsp;the minutes (0-59). Each LED represents a zero or one, with the least significant bit on the right.</p>

<ul>
	<li>For example, the below binary watch reads <code>&quot;4:51&quot;</code>.</li>
</ul>

<p><img alt="" src="https://assets.leetcode.com/uploads/2021/04/08/binarywatch.jpg" style="width: 500px; height: 500px;" /></p>

<p>Given an integer <code>turnedOn</code> which represents the number of LEDs that are currently on (ignoring the PM), return <em>all possible times the watch could represent</em>. You may return the answer in <strong>any order</strong>.</p>

<p>The hour must not contain a leading zero.</p>

<ul>
	<li>For example, <code>&quot;01:00&quot;</code> is not valid. It should be <code>&quot;1:00&quot;</code>.</li>
</ul>

<p>The minute must be consist of two digits and may contain a leading zero.</p>

<ul>
	<li>For example, <code>&quot;10:2&quot;</code> is not valid. It should be <code>&quot;10:02&quot;</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> turnedOn = 1
<strong>Output:</strong> ["0:01","0:02","0:04","0:08","0:16","0:32","1:00","2:00","4:00","8:00"]
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> turnedOn = 9
<strong>Output:</strong> []
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= turnedOn &lt;= 10</code></li>
</ul>


### ZH-CN:
<p>二进制手表顶部有 4 个 LED 代表<strong> 小时（0-11）</strong>，底部的 6 个 LED 代表<strong> 分钟（0-59）</strong>。每个 LED 代表一个 0 或 1，最低位在右侧。</p>

<ul>
	<li>例如，下面的二进制手表读取 <code>"3:25"</code> 。</li>
</ul>

<p><img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2021/03/29/binary_clock_samui_moon.jpg" style="height: 300px; width" /></p>

<p><small><em>（图源：<a href="https://commons.m.wikimedia.org/wiki/File:Binary_clock_samui_moon.jpg">WikiMedia - Binary clock samui moon.jpg</a> ，许可协议：<a href="https://creativecommons.org/licenses/by-sa/3.0/deed.en">Attribution-ShareAlike 3.0 Unported (CC BY-SA 3.0)</a> ）</em></small></p>

<p>给你一个整数 <code>turnedOn</code> ，表示当前亮着的 LED 的数量，返回二进制手表可以表示的所有可能时间。你可以 <strong>按任意顺序</strong> 返回答案。</p>

<p>小时不会以零开头：</p>

<ul>
	<li>例如，<code>"01:00"</code> 是无效的时间，正确的写法应该是 <code>"1:00"</code> 。</li>
</ul>

<p>分钟必须由两位数组成，可能会以零开头：</p>

<ul>
	<li>例如，<code>"10:2"</code> 是无效的时间，正确的写法应该是 <code>"10:02"</code> 。</li>
</ul>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>turnedOn = 1
<strong>输出：</strong>["0:01","0:02","0:04","0:08","0:16","0:32","1:00","2:00","4:00","8:00"]
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>turnedOn = 9
<strong>输出：</strong>[]
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>0 <= turnedOn <= 10</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/binary-watch/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/binary-watch/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 348 ms | 34.5 MB | 2022/08/26 14:59 |

```cpp

class Solution {
public:
    unordered_set<string> ans;
    void backTracking(int turnedOn, vector<int>& hours, vector<int>& mins, int hourStart, int minStart, int currHours, int currMins){
        if(turnedOn == 0 && currHours <= 11 && currMins <= 59){
            string a = "";
            if(currMins < 10) a = to_string(currHours) + ":0" + to_string(currMins);
            else a = to_string(currHours) + ":" + to_string(currMins);
            ans.emplace(a);
            return;
        }

        for(int i = hourStart; i < hours.size(); i++){
            if(currHours > 11) break;
            currHours += hours[i];
            turnedOn -= 1;
            backTracking(turnedOn, hours, mins, i + 1, minStart, currHours, currMins);
            turnedOn += 1;
            currHours -= hours[i];

            for(int j = minStart; j < mins.size(); j++){
                if(currMins > 59) break;
                currMins += mins[j];
                turnedOn -= 1;
                backTracking(turnedOn, hours, mins, hourStart, j + 1, currHours, currMins);
                turnedOn += 1;
                currMins -= mins[j];
            }
        }
    }
    vector<string> readBinaryWatch(int turnedOn) {
        vector<int> hours = {1, 2, 4, 8};
        vector<int> mins = {1, 2, 4, 8, 16, 32};
        backTracking(turnedOn, hours, mins, 0, 0, 0, 0);
        vector<string> res = {ans.begin(), ans.end()};
        return res;
    }
};

```
## My Notes - 我的笔记


No notes

