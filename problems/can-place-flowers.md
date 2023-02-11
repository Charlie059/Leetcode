
# 605. Can Place Flowers - 种花问题

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Greedy-贪心-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">  


## Description - 题目描述

### EN:
<p>You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in <strong>adjacent</strong> plots.</p>

<p>Given an integer array <code>flowerbed</code> containing <code>0</code>&#39;s and <code>1</code>&#39;s, where <code>0</code> means empty and <code>1</code> means not empty, and an integer <code>n</code>, return <em>if</em> <code>n</code> new flowers can be planted in the <code>flowerbed</code> without violating the no-adjacent-flowers rule.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> flowerbed = [1,0,0,0,1], n = 1
<strong>Output:</strong> true
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> flowerbed = [1,0,0,0,1], n = 2
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= flowerbed.length &lt;= 2 * 10<sup>4</sup></code></li>
	<li><code>flowerbed[i]</code> is <code>0</code> or <code>1</code>.</li>
	<li>There are no two adjacent flowers in <code>flowerbed</code>.</li>
	<li><code>0 &lt;= n &lt;= flowerbed.length</code></li>
</ul>


### ZH-CN:
<p>假设有一个很长的花坛，一部分地块种植了花，另一部分却没有。可是，花不能种植在相邻的地块上，它们会争夺水源，两者都会死去。</p>

<p>给你一个整数数组  <code>flowerbed</code> 表示花坛，由若干 <code>0</code> 和 <code>1</code> 组成，其中 <code>0</code> 表示没种植花，<code>1</code> 表示种植了花。另有一个数 <code>n</code><strong> </strong>，能否在不打破种植规则的情况下种入 <code>n</code><strong> </strong>朵花？能则返回 <code>true</code> ，不能则返回 <code>false</code>。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>flowerbed = [1,0,0,0,1], n = 1
<strong>输出：</strong>true
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>flowerbed = [1,0,0,0,1], n = 2
<strong>输出：</strong>false
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= flowerbed.length <= 2 * 10<sup>4</sup></code></li>
	<li><code>flowerbed[i]</code> 为 <code>0</code> 或 <code>1</code></li>
	<li><code>flowerbed</code> 中不存在相邻的两朵花</li>
	<li><code>0 <= n <= flowerbed.length</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/can-place-flowers/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/can-place-flowers/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 16 ms | 19.6 MB | 2022/09/17 21:32 |

```cpp

class Solution {
public:
    bool canPlaceFlowers(vector<int>& flowerbed, int n) {
        const int m = flowerbed.size();
        if(m == 1) return flowerbed[0] == 0 ? n - 1 <= 0: n <= 0;
        for(int i = 0; i < m; i++){
            if(i == 0){
                if(flowerbed[i] == 0 && i + 1 < m && flowerbed[i + 1] == 0){
                    n--;
                    flowerbed[0] = 1;
                }
            }else if(i == m - 1){
                if(flowerbed[i] == 0 && i - 2 >= 0 && flowerbed[i - 1] == 0){
                    n--;
                    flowerbed[i - 1] = 1;
                }
            }else{
                if(flowerbed[i] == 0 && i - 1 >= 0 && i + 1 < m && flowerbed[i - 1] == 0 && flowerbed[i + 1] == 0){
                    n--;
                    flowerbed[i] = 1;
                }
            }
        }
        return n <= 0;
    }
};

```
## My Notes - 我的笔记


No notes

