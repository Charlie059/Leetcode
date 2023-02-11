
# 275. H-Index II - H 指数 II

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Binary Search-二分查找-blue.svg">  


## Description - 题目描述

### EN:
<p>Given an array of integers <code>citations</code> where <code>citations[i]</code> is the number of citations a researcher received for their <code>i<sup>th</sup></code> paper and <code>citations</code>&nbsp;is sorted in an <strong>ascending order</strong>, return compute the researcher&#39;s <code>h</code><strong>-index</strong>.</p>

<p>According to the <a href="https://en.wikipedia.org/wiki/H-index" target="_blank">definition of h-index on Wikipedia</a>: A scientist has an index <code>h</code> if <code>h</code> of their <code>n</code> papers have at least <code>h</code> citations each, and the other <code>n &minus; h</code> papers have no more than <code>h</code> citations each.</p>

<p>If there are several possible values for <code>h</code>, the maximum one is taken as the <code>h</code><strong>-index</strong>.</p>

<p>You must write an algorithm that runs in logarithmic time.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> citations = [0,1,3,5,6]
<strong>Output:</strong> 3
<strong>Explanation:</strong> [0,1,3,5,6] means the researcher has 5 papers in total and each of them had received 0, 1, 3, 5, 6 citations respectively.
Since the researcher has 3 papers with at least 3 citations each and the remaining two with no more than 3 citations each, their h-index is 3.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> citations = [1,2,100]
<strong>Output:</strong> 2
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == citations.length</code></li>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= citations[i] &lt;= 1000</code></li>
	<li><code>citations</code> is sorted in <strong>ascending order</strong>.</li>
</ul>


### ZH-CN:
<p>给你一个整数数组 <code>citations</code> ，其中 <code>citations[i]</code> 表示研究者的第 <code>i</code> 篇论文被引用的次数，<code>citations</code> 已经按照 <strong>升序排列 </strong>。计算并返回该研究者的 <strong><code>h</code><em> </em>指数</strong>。</p>

<p><a href="https://baike.baidu.com/item/h-index/3991452?fr=aladdin" target="_blank">h 指数的定义</a>：h 代表“高引用次数”（high citations），一名科研人员的 h 指数是指他（她）的 （<code>n</code> 篇论文中）<strong>总共</strong>有 <code>h</code> 篇论文分别被引用了<strong>至少</strong> <code>h</code> 次。且其余的 <em><code>n - h</code> </em>篇论文每篇被引用次数 <strong>不超过 </strong><em><code>h</code> </em>次。</p>

<p><strong>提示：</strong>如果 <code>h</code><em> </em>有多种可能的值，<strong><code>h</code> 指数 </strong>是其中最大的那个。</p>

<p>请你设计并实现对数时间复杂度的算法解决此问题。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入<code>：</code></strong><code>citations = [0,1,3,5,6]</code>
<strong>输出：</strong>3 
<strong>解释：</strong>给定数组表示研究者总共有 <code>5</code> 篇论文，每篇论文相应的被引用了 0<code>, 1, 3, 5, 6</code> 次。
     由于研究者有 <code>3 </code>篇论文每篇<strong> 至少 </strong>被引用了 <code>3</code> 次，其余两篇论文每篇被引用<strong> 不多于</strong> <code>3</code> 次，所以她的<em> h </em>指数是 <code>3</code> 。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>citations = [1,2,100]
<strong>输出：</strong>2
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>n == citations.length</code></li>
	<li><code>1 <= n <= 10<sup>5</sup></code></li>
	<li><code>0 <= citations[i] <= 1000</code></li>
	<li><code>citations</code> 按 <strong>升序排列</strong></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/h-index-ii/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/h-index-ii/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 16 ms | 18.1 MB | 2022/06/21 11:31 |

```cpp

class Solution {
public:
    int hIndex(vector<int>& citations) {
        int n = citations.size();
        // sort(citations.begin(), citations.end());

        int h = 0;
        int i = n - 1;

        while(i >= 0 && citations[i] > h){
                h++;
                i--;
        }

        return h;
    }
};

```
## My Notes - 我的笔记


No notes

