
# 面试题 08.06. Hanota LCCI - 汉诺塔问题

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Recursion-递归-blue.svg">   <img src="https://img.shields.io/badge/Array-数组-blue.svg">  


## Description - 题目描述

### EN:
<p>In the classic problem of the Towers of Hanoi, you have 3 towers and N disks of different sizes which can slide onto any tower. The puzzle starts with disks sorted in ascending order of size from top to bottom (i.e., each disk sits on top of an even larger one). You have the following constraints:</p>

<p>(1) Only one disk can be moved at a time.<br />
(2) A disk is slid off the top of one tower onto another tower.<br />
(3) A disk cannot be placed on top of a smaller disk.</p>

<p>Write a program to move the disks from the first tower to the last using stacks.</p>

<p><strong>Example1:</strong></p>

<pre>
<strong> Input</strong>: A = [2, 1, 0], B = [], C = []
<strong> Output</strong>: C = [2, 1, 0]
</pre>

<p><strong>Example2:</strong></p>

<pre>
<strong> Input</strong>: A = [1, 0], B = [], C = []
<strong> Output</strong>: C = [1, 0]
</pre>

<p><strong>Note:</strong></p>

<ol>
	<li><code>A.length &lt;= 14</code></li>
</ol>


### ZH-CN:
<p>在经典汉诺塔问题中，有 3 根柱子及 N 个不同大小的穿孔圆盘，盘子可以滑入任意一根柱子。一开始，所有盘子自上而下按升序依次套在第一根柱子上(即每一个盘子只能放在更大的盘子上面)。移动圆盘时受到以下限制:<br>
(1) 每次只能移动一个盘子;<br>
(2) 盘子只能从柱子顶端滑出移到下一根柱子;<br>
(3) 盘子只能叠在比它大的盘子上。</p>

<p>请编写程序，用栈将所有盘子从第一根柱子移到最后一根柱子。</p>

<p>你需要原地修改栈。</p>

<p><strong>示例1:</strong></p>

<pre><strong> 输入</strong>：A = [2, 1, 0], B = [], C = []
<strong> 输出</strong>：C = [2, 1, 0]
</pre>

<p><strong>示例2:</strong></p>

<pre><strong> 输入</strong>：A = [1, 0], B = [], C = []
<strong> 输出</strong>：C = [1, 0]
</pre>

<p><strong>提示:</strong></p>

<ol>
	<li>A中盘子的数目不大于14个。</li>
</ol>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/hanota-lcci/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/hanota-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 6.6 MB | 2022/08/21 9:44 |

```cpp

class Solution {
public:
    void hanota(vector<int>& A, vector<int>& B, vector<int>& C) {
        const int n = A.size();
        move(n, A, B, C);
    }

    void move(int n, vector<int>& A, vector<int>& B, vector<int>& C){
        if(n == 1){
            C.emplace_back(A.back());
            A.pop_back();
            return;
        }

        move(n - 1, A, C, B);
        C.emplace_back(A.back());
        A.pop_back();
        move(n - 1, B, A, C);
    }
};

```
## My Notes - 我的笔记


No notes

