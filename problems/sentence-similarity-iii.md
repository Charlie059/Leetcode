
# 1813. Sentence Similarity III - 句子相似性 III

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Two Pointers-双指针-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>A sentence is a list of words that are separated by a single space with no leading or trailing spaces. For example, <code>&quot;Hello World&quot;</code>, <code>&quot;HELLO&quot;</code>, <code>&quot;hello world hello world&quot;</code> are all sentences. Words consist of <strong>only</strong> uppercase and lowercase English letters.</p>

<p>Two sentences <code>sentence1</code> and <code>sentence2</code> are <strong>similar</strong> if it is possible to insert an arbitrary sentence <strong>(possibly empty)</strong> inside one of these sentences such that the two sentences become equal. For example, <code>sentence1 = &quot;Hello my name is Jane&quot;</code> and <code>sentence2 = &quot;Hello Jane&quot;</code> can be made equal by inserting <code>&quot;my name is&quot;</code> between <code>&quot;Hello&quot;</code> and <code>&quot;Jane&quot;</code> in <code>sentence2</code>.</p>

<p>Given two sentences <code>sentence1</code> and <code>sentence2</code>, return <code>true</code> <em>if </em><code>sentence1</code> <em>and </em><code>sentence2</code> <em>are similar.</em> Otherwise, return <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> sentence1 = &quot;My name is Haley&quot;, sentence2 = &quot;My Haley&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> sentence2 can be turned to sentence1 by inserting &quot;name is&quot; between &quot;My&quot; and &quot;Haley&quot;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> sentence1 = &quot;of&quot;, sentence2 = &quot;A lot of words&quot;
<strong>Output:</strong> false
<strong>Explanation: </strong>No single sentence can be inserted inside one of the sentences to make it equal to the other.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> sentence1 = &quot;Eating right now&quot;, sentence2 = &quot;Eating&quot;
<strong>Output:</strong> true
<strong>Explanation:</strong> sentence2 can be turned to sentence1 by inserting &quot;right now&quot; at the end of the sentence.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= sentence1.length, sentence2.length &lt;= 100</code></li>
	<li><code>sentence1</code> and <code>sentence2</code> consist of lowercase and uppercase English letters and spaces.</li>
	<li>The words in <code>sentence1</code> and <code>sentence2</code> are separated by a single space.</li>
</ul>


### ZH-CN:
<p>一个句子是由一些单词与它们之间的单个空格组成，且句子的开头和结尾没有多余空格。比方说，<code>"Hello World"</code> ，<code>"HELLO"</code> ，<code>"hello world hello world"</code> 都是句子。每个单词都 <strong>只</strong> 包含大写和小写英文字母。</p>

<p>如果两个句子 <code>sentence1</code> 和 <code>sentence2</code> ，可以通过往其中一个句子插入一个任意的句子（<strong>可以是空句子</strong>）而得到另一个句子，那么我们称这两个句子是 <strong>相似的</strong> 。比方说，<code>sentence1 = "Hello my name is Jane"</code> 且 <code>sentence2 = "Hello Jane"</code> ，我们可以往 <code>sentence2</code> 中 <code>"Hello"</code> 和 <code>"Jane"</code> 之间插入 <code>"my name is"</code> 得到 <code>sentence1</code> 。</p>

<p>给你两个句子 <code>sentence1</code> 和 <code>sentence2</code> ，如果<em> </em><code>sentence1</code> 和<em> </em><code>sentence2</code> 是相似的，请你返回 <code>true</code> ，否则返回 <code>false</code> 。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre><b>输入：</b>sentence1 = "My name is Haley", sentence2 = "My Haley"
<b>输出：</b>true
<b>解释：</b>可以往 sentence2 中 "My" 和 "Haley" 之间插入 "name is" ，得到 sentence1 。
</pre>

<p><strong>示例 2：</strong></p>

<pre><b>输入：</b>sentence1 = "of", sentence2 = "A lot of words"
<b>输出：</b>false
<strong>解释：</strong>没法往这两个句子中的一个句子只插入一个句子就得到另一个句子。
</pre>

<p><strong>示例 3：</strong></p>

<pre><b>输入：</b>sentence1 = "Eating right now", sentence2 = "Eating"
<b>输出：</b>true
<b>解释：</b>可以往 sentence2 的结尾插入 "right now" 得到 sentence1 。
</pre>

<p><strong>示例 4：</strong></p>

<pre><b>输入：</b>sentence1 = "Luky", sentence2 = "Lucccky"
<b>输出：</b>false
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= sentence1.length, sentence2.length &lt;= 100</code></li>
	<li><code>sentence1</code> 和 <code>sentence2</code> 都只包含大小写英文字母和空格。</li>
	<li><code>sentence1</code> 和 <code>sentence2</code> 中的单词都只由单个空格隔开。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/sentence-similarity-iii/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/sentence-similarity-iii/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 6.5 MB | 2023/01/15 16:15 |

```cpp

class Solution {
public:
    bool areSentencesSimilar(string sentence1, string sentence2) {
        //处理字符串
        vector<string> s1, s2;
        stringstream ss1(sentence1), ss2(sentence2);
        string word;

        while(ss1 >> word)  s1.emplace_back(word);    
        while(ss2 >> word)  s2.emplace_back(word);

        //双指针
        int l1 = 0, r1 = s1.size() - 1, l2 = 0, r2 = s2.size() - 1;
        while(l1 <= r1 && l2 <= r2){            
            bool moveL = false, moveR = false;
            if(s1[l1] == s2[l2]){
                l1++; l2++; moveL = true;
            }
            if(s1[r1] == s2[r2]){
                r1--; r2--; moveR = true;
            }
            if(!moveL && !moveR) return false;
        }
        return true;
    }   
};

```
## My Notes - 我的笔记


No notes

