
# 1360. Number of Days Between Two Dates - 日期之间隔几天

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>Write a program to count the number of days between two dates.</p>

<p>The two dates are given as strings, their format is <code>YYYY-MM-DD</code>&nbsp;as shown in the examples.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> date1 = "2019-06-29", date2 = "2019-06-30"
<strong>Output:</strong> 1
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> date1 = "2020-01-15", date2 = "2019-12-31"
<strong>Output:</strong> 15
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The given dates are valid&nbsp;dates between the years <code>1971</code> and <code>2100</code>.</li>
</ul>


### ZH-CN:
<p>请你编写一个程序来计算两个日期之间隔了多少天。</p>

<p>日期以字符串形式给出，格式为&nbsp;<code>YYYY-MM-DD</code>，如示例所示。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>date1 = &quot;2019-06-29&quot;, date2 = &quot;2019-06-30&quot;
<strong>输出：</strong>1
</pre>

<p><strong>示例 2：</strong></p>

<pre><strong>输入：</strong>date1 = &quot;2020-01-15&quot;, date2 = &quot;2019-12-31&quot;
<strong>输出：</strong>15
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>给定的日期是&nbsp;<code>1971</code>&nbsp;年到 <code>2100</code>&nbsp;年之间的有效日期。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/number-of-days-between-two-dates/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/number-of-days-between-two-dates/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 5.8 MB | 2022/08/23 16:13 |

```cpp

class Solution {
public:
    bool isLeapYear(int year){
        return (0 == year % 4 && 0 != year % 100) || 0 == year % 400;
    }
    int daysBetweenDates(string date1, string date2) {
        if(strcmp(date1.c_str(), date2.c_str()) > 0) return daysBetweenDates(date2, date1);
        vector<int> month = {0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
        
        int year1, month1, day1;
        sscanf(date1.c_str(), "%d-%d-%d", &year1, &month1, &day1);
        int year2, month2, day2;
        sscanf(date2.c_str(), "%d-%d-%d", &year2, &month2, &day2);

        int days = 0;
        // Get the gap of years
        for(int year = year1; year < year2; year++) days += isLeapYear(year) ? 366 : 365;

        // Get the gap of month and days
        for(int i = 1; i < month1; i++) day1 += month[i] + (2 == i && isLeapYear(year1));
        for(int i = 1; i < month2; i++) day2 += month[i] + (2 == i && isLeapYear(year2));

        return days + day2 - day1;
    }
};

```
## My Notes - 我的笔记


No notes

