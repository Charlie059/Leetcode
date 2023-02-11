
# 331. Verify Preorder Serialization of a Binary Tree - 验证二叉树的前序序列化

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Stack-栈-blue.svg">   <img src="https://img.shields.io/badge/Tree-树-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">   <img src="https://img.shields.io/badge/Binary Tree-二叉树-blue.svg">  


## Description - 题目描述

### EN:
<p>One way to serialize a binary tree is to use <strong>preorder traversal</strong>. When we encounter a non-null node, we record the node&#39;s value. If it is a null node, we record using a sentinel value such as <code>&#39;#&#39;</code>.</p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/12/pre-tree.jpg" style="width: 362px; height: 293px;" />
<p>For example, the above binary tree can be serialized to the string <code>&quot;9,3,4,#,#,1,#,#,2,#,6,#,#&quot;</code>, where <code>&#39;#&#39;</code> represents a null node.</p>

<p>Given a string of comma-separated values <code>preorder</code>, return <code>true</code> if it is a correct preorder traversal serialization of a binary tree.</p>

<p>It is <strong>guaranteed</strong> that each comma-separated value in the string must be either an integer or a character <code>&#39;#&#39;</code> representing null pointer.</p>

<p>You may assume that the input format is always valid.</p>

<ul>
	<li>For example, it could never contain two consecutive commas, such as <code>&quot;1,,3&quot;</code>.</li>
</ul>

<p><strong>Note:&nbsp;</strong>You are not allowed to reconstruct the tree.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> preorder = "9,3,4,#,#,1,#,#,2,#,6,#,#"
<strong>Output:</strong> true
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> preorder = "1,#"
<strong>Output:</strong> false
</pre><p><strong class="example">Example 3:</strong></p>
<pre><strong>Input:</strong> preorder = "9,#,#,1"
<strong>Output:</strong> false
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= preorder.length &lt;= 10<sup>4</sup></code></li>
	<li><code>preorder</code> consist of integers in the range <code>[0, 100]</code> and <code>&#39;#&#39;</code> separated by commas <code>&#39;,&#39;</code>.</li>
</ul>


### ZH-CN:
<p>序列化二叉树的一种方法是使用 <strong>前序遍历 </strong>。当我们遇到一个非空节点时，我们可以记录下这个节点的值。如果它是一个空节点，我们可以使用一个标记值记录，例如 <code>#</code>。</p>

<p><img src="https://assets.leetcode.com/uploads/2021/03/12/pre-tree.jpg" /></p>

<p>例如，上面的二叉树可以被序列化为字符串 <code>"9,3,4,#,#,1,#,#,2,#,6,#,#"</code>，其中 <code>#</code> 代表一个空节点。</p>

<p>给定一串以逗号分隔的序列，验证它是否是正确的二叉树的前序序列化。编写一个在不重构树的条件下的可行算法。</p>

<p><strong>保证</strong> 每个以逗号分隔的字符或为一个整数或为一个表示 <code>null</code> 指针的 <code>'#'</code> 。</p>

<p>你可以认为输入格式总是有效的</p>

<ul>
	<li>例如它永远不会包含两个连续的逗号，比如&nbsp;<code>"1,,3"</code> 。</li>
</ul>

<p><strong>注意：</strong>不允许重建树。</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入: </strong>preorder = <code>"9,3,4,#,#,1,#,#,2,#,6,#,#"</code>
<strong>输出: </strong><code>true</code></pre>

<p><strong>示例&nbsp;2:</strong></p>

<pre>
<strong>输入: </strong>preorder = <code>"1,#"</code>
<strong>输出: </strong><code>false</code>
</pre>

<p><strong>示例 3:</strong></p>

<pre>
<strong>输入: </strong>preorder = <code>"9,#,#,1"</code>
<strong>输出: </strong><code>false</code>
</pre>

<p>&nbsp;</p>

<p><strong>提示:</strong></p>

<ul>
	<li><code>1 &lt;= preorder.length &lt;= 10<sup>4</sup></code></li>
	<li><code>preorder</code>&nbsp;由以逗号&nbsp;<code>“，”</code> 分隔的 <code>[0,100]</code> 范围内的整数和 <code>“#”</code> 组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/verify-preorder-serialization-of-a-binary-tree/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/verify-preorder-serialization-of-a-binary-tree/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 8 ms | 11.3 MB | 2022/10/27 1:03 |

```cpp

class Solution {
public:
    bool isValidSerialization(string preorder) {
        stringstream ss(preorder);
        string s = "";
        vector<string> vec;

        while(getline(ss, s, ',')) vec.emplace_back(s);

        const int n = vec.size();
        deque<string> dq;
        for(int i = 0; i < n; i++){
            dq.push_back(vec[i]);
            // Clear the ##
            while(dq.size() >= 3 && dq[dq.size() - 1] == dq[dq.size() - 2] && dq[dq.size() - 2] == "#" && dq[dq.size() - 3] != "#"){
                dq.pop_back(); dq.pop_back(); dq.pop_back();
                dq.push_back("#");
            }
        }

        return dq.size() == 1 && dq[0] == "#";
    }
};

```
## My Notes - 我的笔记


No notes

