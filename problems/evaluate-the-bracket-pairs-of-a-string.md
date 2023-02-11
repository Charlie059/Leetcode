
# 1807. Evaluate the Bracket Pairs of a String - 替换字符串中的括号内容

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a string <code>s</code> that contains some bracket pairs, with each pair containing a <strong>non-empty</strong> key.</p>

<ul>
	<li>For example, in the string <code>&quot;(name)is(age)yearsold&quot;</code>, there are <strong>two</strong> bracket pairs that contain the keys <code>&quot;name&quot;</code> and <code>&quot;age&quot;</code>.</li>
</ul>

<p>You know the values of a wide range of keys. This is represented by a 2D string array <code>knowledge</code> where each <code>knowledge[i] = [key<sub>i</sub>, value<sub>i</sub>]</code> indicates that key <code>key<sub>i</sub></code> has a value of <code>value<sub>i</sub></code>.</p>

<p>You are tasked to evaluate <strong>all</strong> of the bracket pairs. When you evaluate a bracket pair that contains some key <code>key<sub>i</sub></code>, you will:</p>

<ul>
	<li>Replace <code>key<sub>i</sub></code> and the bracket pair with the key&#39;s corresponding <code>value<sub>i</sub></code>.</li>
	<li>If you do not know the value of the key, you will replace <code>key<sub>i</sub></code> and the bracket pair with a question mark <code>&quot;?&quot;</code> (without the quotation marks).</li>
</ul>

<p>Each key will appear at most once in your <code>knowledge</code>. There will not be any nested brackets in <code>s</code>.</p>

<p>Return <em>the resulting string after evaluating <strong>all</strong> of the bracket pairs.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(name)is(age)yearsold&quot;, knowledge = [[&quot;name&quot;,&quot;bob&quot;],[&quot;age&quot;,&quot;two&quot;]]
<strong>Output:</strong> &quot;bobistwoyearsold&quot;
<strong>Explanation:</strong>
The key &quot;name&quot; has a value of &quot;bob&quot;, so replace &quot;(name)&quot; with &quot;bob&quot;.
The key &quot;age&quot; has a value of &quot;two&quot;, so replace &quot;(age)&quot; with &quot;two&quot;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;hi(name)&quot;, knowledge = [[&quot;a&quot;,&quot;b&quot;]]
<strong>Output:</strong> &quot;hi?&quot;
<strong>Explanation:</strong> As you do not know the value of the key &quot;name&quot;, replace &quot;(name)&quot; with &quot;?&quot;.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> s = &quot;(a)(a)(a)aaa&quot;, knowledge = [[&quot;a&quot;,&quot;yes&quot;]]
<strong>Output:</strong> &quot;yesyesyesaaa&quot;
<strong>Explanation:</strong> The same key can appear multiple times.
The key &quot;a&quot; has a value of &quot;yes&quot;, so replace all occurrences of &quot;(a)&quot; with &quot;yes&quot;.
Notice that the &quot;a&quot;s not in a bracket pair are not evaluated.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= knowledge.length &lt;= 10<sup>5</sup></code></li>
	<li><code>knowledge[i].length == 2</code></li>
	<li><code>1 &lt;= key<sub>i</sub>.length, value<sub>i</sub>.length &lt;= 10</code></li>
	<li><code>s</code> consists of lowercase English letters and round brackets <code>&#39;(&#39;</code> and <code>&#39;)&#39;</code>.</li>
	<li>Every open bracket <code>&#39;(&#39;</code> in <code>s</code> will have a corresponding close bracket <code>&#39;)&#39;</code>.</li>
	<li>The key in each bracket pair of <code>s</code> will be non-empty.</li>
	<li>There will not be any nested bracket pairs in <code>s</code>.</li>
	<li><code>key<sub>i</sub></code> and <code>value<sub>i</sub></code> consist of lowercase English letters.</li>
	<li>Each <code>key<sub>i</sub></code> in <code>knowledge</code> is unique.</li>
</ul>


### ZH-CN:
<p>给你一个字符串&nbsp;<code>s</code>&nbsp;，它包含一些括号对，每个括号中包含一个 <strong>非空</strong>&nbsp;的键。</p>

<ul>
	<li>比方说，字符串&nbsp;<code>"(name)is(age)yearsold"</code>&nbsp;中，有&nbsp;<strong>两个</strong>&nbsp;括号对，分别包含键&nbsp;<code>"name"</code> 和&nbsp;<code>"age"</code>&nbsp;。</li>
</ul>

<p>你知道许多键对应的值，这些关系由二维字符串数组&nbsp;<code>knowledge</code>&nbsp;表示，其中&nbsp;<code>knowledge[i] = [key<sub>i</sub>, value<sub>i</sub>]</code>&nbsp;，表示键&nbsp;<code>key<sub>i</sub></code>&nbsp;对应的值为&nbsp;<code>value<sub>i</sub></code><sub>&nbsp;</sub>。</p>

<p>你需要替换 <strong>所有</strong>&nbsp;的括号对。当你替换一个括号对，且它包含的键为&nbsp;<code>key<sub>i</sub></code>&nbsp;时，你需要：</p>

<ul>
	<li>将&nbsp;<code>key<sub>i</sub></code>&nbsp;和括号用对应的值&nbsp;<code>value<sub>i</sub></code>&nbsp;替换。</li>
	<li>如果从 <code>knowledge</code>&nbsp;中无法得知某个键对应的值，你需要将&nbsp;<code>key<sub>i</sub></code>&nbsp;和括号用问号&nbsp;<code>"?"</code>&nbsp;替换（不需要引号）。</li>
</ul>

<p><code>knowledge</code>&nbsp;中每个键最多只会出现一次。<code>s</code>&nbsp;中不会有嵌套的括号。</p>

<p>请你返回替换 <strong>所有</strong>&nbsp;括号对后的结果字符串。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<b>输入：</b>s = "(name)is(age)yearsold", knowledge = [["name","bob"],["age","two"]]
<b>输出：</b>"bobistwoyearsold"
<strong>解释：</strong>
键 "name" 对应的值为 "bob" ，所以将 "(name)" 替换为 "bob" 。
键 "age" 对应的值为 "two" ，所以将 "(age)" 替换为 "two" 。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<b>输入：</b>s = "hi(name)", knowledge = [["a","b"]]
<b>输出：</b>"hi?"
<b>解释：</b>由于不知道键 "name" 对应的值，所以用 "?" 替换 "(name)" 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<b>输入：</b>s = "(a)(a)(a)aaa", knowledge = [["a","yes"]]
<b>输出：</b>"yesyesyesaaa"
<b>解释：</b>相同的键在 s 中可能会出现多次。
键 "a" 对应的值为 "yes" ，所以将所有的 "(a)" 替换为 "yes" 。
注意，不在括号里的 "a" 不需要被替换。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= s.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= knowledge.length &lt;= 10<sup>5</sup></code></li>
	<li><code>knowledge[i].length == 2</code></li>
	<li><code>1 &lt;= key<sub>i</sub>.length, value<sub>i</sub>.length &lt;= 10</code></li>
	<li><code>s</code>&nbsp;只包含小写英文字母和圆括号&nbsp;<code>'('</code>&nbsp;和&nbsp;<code>')'</code>&nbsp;。</li>
	<li><code>s</code>&nbsp;中每一个左圆括号&nbsp;<code>'('</code>&nbsp;都有对应的右圆括号&nbsp;<code>')'</code>&nbsp;。</li>
	<li><code>s</code>&nbsp;中每对括号内的键都不会为空。</li>
	<li><code>s</code>&nbsp;中不会有嵌套括号对。</li>
	<li><code>key<sub>i</sub></code>&nbsp;和&nbsp;<code>value<sub>i</sub></code>&nbsp;只包含小写英文字母。</li>
	<li><code>knowledge</code>&nbsp;中的&nbsp;<code>key<sub>i</sub></code>&nbsp;不会重复。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/evaluate-the-bracket-pairs-of-a-string/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/evaluate-the-bracket-pairs-of-a-string/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 296 ms | 114.3 MB | 2023/01/12 9:46 |

```cpp

class Solution {
public:
    string evaluate(string s, vector<vector<string>>& knowledge) {
        unordered_map<string, string> hm;
        string ans;
        const int n = knowledge.size();

        for(int i = 0; i < n; i++) hm[knowledge[i][0]] = knowledge[i][1];

        bool edit = false;
        string tmp;
        for(const char& c: s){
            if(c == '(') edit = true;
            else if(c == ')'){
                ans += hm.count(tmp) ? hm[tmp] : "?";
                tmp = "";
                edit = false;
            }else if(!edit){
                ans += c;
            }else if(edit){
                tmp += c;
            }
        }

        return ans;

    }
};

```
## My Notes - 我的笔记


No notes

