
# 369. Plus One Linked List - 给单链表加一

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Linked List-链表-blue.svg">   <img src="https://img.shields.io/badge/Math-数学-blue.svg">  


## Description - 题目描述

### EN:
<p>Given a non-negative integer represented as a linked list of digits, <em>plus one to the integer</em>.</p>

<p>The digits are stored such that the most significant digit is at the <code>head</code> of the list.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> head = [1,2,3]
<strong>Output:</strong> [1,2,4]
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> head = [0]
<strong>Output:</strong> [1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the linked list is in the range <code>[1, 100]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 9</code></li>
	<li>The number represented by the linked list does not contain leading zeros except for the zero itself.&nbsp;</li>
</ul>


### ZH-CN:
<p>给定一个用<strong>链表</strong>表示的非负整数， 然后将这个整数&nbsp;<em>再加上 1</em> 。</p>

<p>这些数字的存储是这样的：最高位有效的数字位于链表的首位<meta charset="UTF-8" />&nbsp;<code>head</code>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入: </strong>head = [1,2,3]
<strong>输出: </strong>[1,2,4]
</pre>

<p><meta charset="UTF-8" /></p>

<p><strong>示例</strong><strong>&nbsp;2:</strong></p>

<pre>
<strong>输入: </strong>head = [0]
<strong>输出: </strong>[1]
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li>链表中的节点数在<meta charset="UTF-8" />&nbsp;<code>[1, 100]</code>&nbsp;的范围内。</li>
	<li><code>0 &lt;= Node.val &lt;= 9</code></li>
	<li>由链表表示的数字不包含前导零，除了零本身。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/plus-one-linked-list/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/plus-one-linked-list/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 8.3 MB | 2022/08/15 15:10 |

```cpp

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:

    ListNode* plusOne(ListNode* head) {
        ListNode * dummmyNode = new ListNode(0);
        dummmyNode->next = head;
        vector<ListNode*> vec;

        while(head){
            vec.emplace_back(head);
            head = head->next;
        }

        const int n = vec.size();
        cout << n << endl;
        int cnt = 0;
        for(int i = n - 1; i >= 0; i--){
            if(vec[i]->val == 9) vec[i]->val = 0;
            else{
                vec[i]->val += 1;
                break;
            }
            cnt++;
        }

        if(cnt == n){
            dummmyNode->val += 1;
            return dummmyNode;
        }
        else return dummmyNode->next;
    }
};

```
## My Notes - 我的笔记


No notes

