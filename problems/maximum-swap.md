
# 670. Maximum Swap - 最大交换

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Greedy-贪心-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given an integer <code>num</code>. You can swap two digits at most once to get the maximum valued number.</p>

<p>Return <em>the maximum valued number you can get</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> num = 2736
<strong>Output:</strong> 7236
<strong>Explanation:</strong> Swap the number 2 and the number 7.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> num = 9973
<strong>Output:</strong> 9973
<strong>Explanation:</strong> No swap.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= num &lt;= 10<sup>8</sup></code></li>
</ul>


### ZH-CN:
<p>给定一个非负整数，你<strong>至多</strong>可以交换一次数字中的任意两位。返回你能得到的最大值。</p>

<p><strong>示例 1 :</strong></p>

<pre>
<strong>输入:</strong> 2736
<strong>输出:</strong> 7236
<strong>解释:</strong> 交换数字2和数字7。
</pre>

<p><strong>示例 2 :</strong></p>

<pre>
<strong>输入:</strong> 9973
<strong>输出:</strong> 9973
<strong>解释:</strong> 不需要交换。
</pre>

<p><strong>注意:</strong></p>

<ol>
	<li>给定数字的范围是&nbsp;[0, 10<sup>8</sup>]</li>
</ol>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/maximum-swap/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/maximum-swap/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 5.9 MB | 2022/09/18 11:53 |

```cpp

class Solution {
public:
    int maximumSwap(int num) {
        string numStr = to_string(num);
        const int n = numStr.length();
        vector<int> vec(n, 0);
        int curMax = 0, curIdx = 0;
        for(int i = n - 1; i >= 0; i--){
            if(numStr[i] - '0' > curMax){
                curMax = numStr[i] - '0';
                curIdx = i;
            }
            vec[i] = curIdx;
        }
        string currMax = numStr;
        for(int i = 0; i < n; i++){
            string buf = numStr;
            swap(buf[i], buf[vec[i]]);
            if(strcmp(buf.c_str(), currMax.c_str()) > 0){
                currMax = buf;
            }
        }
                
        return stoi(currMax);
    }
};

```
## My Notes - 我的笔记


No notes

