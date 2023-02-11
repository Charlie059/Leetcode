
# 553. Optimal Division - 最优除法

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">   <img src="https://img.shields.io/badge/Dynamic Programming-动态规划-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given an integer array <code>nums</code>. The adjacent integers in <code>nums</code> will perform the float division.</p>

<ul>
	<li>For example, for <code>nums = [2,3,4]</code>, we will evaluate the expression <code>&quot;2/3/4&quot;</code>.</li>
</ul>

<p>However, you can add any number of parenthesis at any position to change the priority of operations. You want to add these parentheses such the value of the expression after the evaluation is maximum.</p>

<p>Return <em>the corresponding expression that has the maximum value in string format</em>.</p>

<p><strong>Note:</strong> your expression should not contain redundant parenthesis.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [1000,100,10,2]
<strong>Output:</strong> &quot;1000/(100/10/2)&quot;
<strong>Explanation:</strong> 1000/(100/10/2) = 1000/((100/10)/2) = 200
However, the bold parenthesis in &quot;1000/(<strong>(</strong>100/10<strong>)</strong>/2)&quot; are redundant since they do not influence the operation priority.
So you should return &quot;1000/(100/10/2)&quot;.
Other cases:
1000/(100/10)/2 = 50
1000/(100/(10/2)) = 50
1000/100/10/2 = 0.5
1000/100/(10/2) = 2
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,3,4]
<strong>Output:</strong> &quot;2/(3/4)&quot;
<strong>Explanation:</strong> (2/(3/4)) = 8/3 = 2.667
It can be shown that after trying all possibilities, we cannot get an expression with evaluation greater than 2.667
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10</code></li>
	<li><code>2 &lt;= nums[i] &lt;= 1000</code></li>
	<li>There is only one optimal division for the given input.</li>
</ul>


### ZH-CN:
<p>给定一正整数数组<strong> </strong><code>nums</code><strong>，</strong><code>nums</code> 中的相邻整数将进行浮点除法。例如，&nbsp;[2,3,4] -&gt; 2 / 3 / 4 。</p>

<ul>
	<li>例如，<code>nums = [2,3,4]</code>，我们将求表达式的值&nbsp;<code>"2/3/4"</code>。</li>
</ul>

<p>但是，你可以在任意位置添加任意数目的括号，来改变算数的优先级。你需要找出怎么添加括号，以便计算后的表达式的值为最大值。</p>

<p>以字符串格式返回具有最大值的对应表达式。</p>

<p><strong>注意：</strong>你的表达式不应该包含多余的括号。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入:</strong> [1000,100,10,2]
<strong>输出:</strong> "1000/(100/10/2)"
<strong>解释: </strong>1000/(100/10/2) = 1000/((100/10)/2) = 200
但是，以下加粗的括号 "1000/(<strong>(</strong>100/10<strong>)</strong>/2)" 是冗余的，
因为他们并不影响操作的优先级，所以你需要返回 "1000/(100/10/2)"。

其他用例:
1000/(100/10)/2 = 50
1000/(100/(10/2)) = 50
1000/100/10/2 = 0.5
1000/100/(10/2) = 2
</pre>

<p>&nbsp;</p>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入:</strong> nums = [2,3,4]
<strong>输出:</strong> "2/(3/4)"
<strong>解释:</strong> (2/(3/4)) = 8/3 = 2.667
可以看出，在尝试了所有的可能性之后，我们无法得到一个结果大于 2.667 的表达式。
</pre>

<p>&nbsp;</p>

<p><strong>说明:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10</code></li>
	<li><code>2 &lt;= nums[i] &lt;= 1000</code></li>
	<li>对于给定的输入只有一种最优除法。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/optimal-division/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/optimal-division/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 7.6 MB | 2022/07/23 23:36 |

```cpp

class Solution {
public:
    string optimalDivision(vector<int>& nums) {
        const int n = nums.size();
        if(n == 1){
            return to_string(nums[0]);
        }else if(n == 2){
            return to_string(nums[0]) + "/" + to_string(nums[1]);
        }

        string ans = to_string(nums[0]) + "/(" + to_string(nums[1]);
        for(int i = 2; i < n; i++){
            ans.append("/" + to_string(nums[i]));
        }
        ans.append(")");
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

