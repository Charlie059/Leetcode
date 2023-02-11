
# 1694. Reformat Phone Number - 重新格式化电话号码

## Tags - 题目标签

 <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a phone number as a string <code>number</code>. <code>number</code> consists of digits, spaces <code>&#39; &#39;</code>, and/or dashes <code>&#39;-&#39;</code>.</p>

<p>You would like to reformat the phone number in a certain manner. Firstly, <strong>remove</strong> all spaces and dashes. Then, <strong>group</strong> the digits from left to right into blocks of length 3 <strong>until</strong> there are 4 or fewer digits. The final digits are then grouped as follows:</p>

<ul>
	<li>2 digits: A single block of length 2.</li>
	<li>3 digits: A single block of length 3.</li>
	<li>4 digits: Two blocks of length 2 each.</li>
</ul>

<p>The blocks are then joined by dashes. Notice that the reformatting process should <strong>never</strong> produce any blocks of length 1 and produce <strong>at most</strong> two blocks of length 2.</p>

<p>Return <em>the phone number after formatting.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> number = &quot;1-23-45 6&quot;
<strong>Output:</strong> &quot;123-456&quot;
<strong>Explanation:</strong> The digits are &quot;123456&quot;.
Step 1: There are more than 4 digits, so group the next 3 digits. The 1st block is &quot;123&quot;.
Step 2: There are 3 digits remaining, so put them in a single block of length 3. The 2nd block is &quot;456&quot;.
Joining the blocks gives &quot;123-456&quot;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> number = &quot;123 4-567&quot;
<strong>Output:</strong> &quot;123-45-67&quot;
<strong>Explanation: </strong>The digits are &quot;1234567&quot;.
Step 1: There are more than 4 digits, so group the next 3 digits. The 1st block is &quot;123&quot;.
Step 2: There are 4 digits left, so split them into two blocks of length 2. The blocks are &quot;45&quot; and &quot;67&quot;.
Joining the blocks gives &quot;123-45-67&quot;.
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> number = &quot;123 4-5678&quot;
<strong>Output:</strong> &quot;123-456-78&quot;
<strong>Explanation:</strong> The digits are &quot;12345678&quot;.
Step 1: The 1st block is &quot;123&quot;.
Step 2: The 2nd block is &quot;456&quot;.
Step 3: There are 2 digits left, so put them in a single block of length 2. The 3rd block is &quot;78&quot;.
Joining the blocks gives &quot;123-456-78&quot;.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= number.length &lt;= 100</code></li>
	<li><code>number</code> consists of digits and the characters <code>&#39;-&#39;</code> and <code>&#39; &#39;</code>.</li>
	<li>There are at least <strong>two</strong> digits in <code>number</code>.</li>
</ul>


### ZH-CN:
<p>给你一个字符串形式的电话号码 <code>number</code> 。<code>number</code> 由数字、空格 <code>' '</code>、和破折号 <code>'-'</code> 组成。</p>

<p>请你按下述方式重新格式化电话号码。</p>

<ul>
	<li>首先，<strong>删除</strong> 所有的空格和破折号。</li>
	<li>其次，将数组从左到右 <strong>每 3 个一组</strong> 分块，<strong>直到 </strong>剩下 4 个或更少数字。剩下的数字将按下述规定再分块：
	<ul>
		<li>2 个数字：单个含 2 个数字的块。</li>
		<li>3 个数字：单个含 3 个数字的块。</li>
		<li>4 个数字：两个分别含 2 个数字的块。</li>
	</ul>
	</li>
</ul>

<p>最后用破折号将这些块连接起来。注意，重新格式化过程中 <strong>不应该</strong> 生成仅含 1 个数字的块，并且 <strong>最多</strong> 生成两个含 2 个数字的块。</p>

<p>返回格式化后的电话号码。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>number = "1-23-45 6"
<strong>输出：</strong>"123-456"
<strong>解释：</strong>数字是 "123456"
步骤 1：共有超过 4 个数字，所以先取 3 个数字分为一组。第 1 个块是 "123" 。
步骤 2：剩下 3 个数字，将它们放入单个含 3 个数字的块。第 2 个块是 "456" 。
连接这些块后得到 "123-456" 。</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>number = "123 4-567"
<strong>输出：</strong>"123-45-67"
<strong>解释：</strong>数字是 "1234567".
步骤 1：共有超过 4 个数字，所以先取 3 个数字分为一组。第 1 个块是 "123" 。
步骤 2：剩下 4 个数字，所以将它们分成两个含 2 个数字的块。这 2 块分别是 "45" 和 "67" 。
连接这些块后得到 "123-45-67" 。
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>number = "123 4-5678"
<strong>输出：</strong>"123-456-78"
<strong>解释：</strong>数字是 "12345678" 。
步骤 1：第 1 个块 "123" 。
步骤 2：第 2 个块 "456" 。
步骤 3：剩下 2 个数字，将它们放入单个含 2 个数字的块。第 3 个块是 "78" 。
连接这些块后得到 "123-456-78" 。</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>number = "12"
<strong>输出：</strong>"12"
</pre>

<p><strong>示例 5：</strong></p>

<pre>
<strong>输入：</strong>number = "--17-5 229 35-39475 "
<strong>输出：</strong>"175-229-353-94-75"
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>2 <= number.length <= 100</code></li>
	<li><code>number</code> 由数字和字符 <code>'-'</code> 及 <code>' '</code> 组成。</li>
	<li><code>number</code> 中至少含 <strong>2</strong> 个数字。</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/reformat-phone-number/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/reformat-phone-number/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 6.1 MB | 2022/09/30 23:03 |

```cpp

class Solution {
public:
    string reformatNumber(string number) {
        const int n = number.length();
        vector<int> tmp;

        for(auto c: number) if(isdigit(c)) tmp.emplace_back(c);
        const int m = tmp.size();
        string ans;

        int i = 0;
        while(m - i > 4){
            for(int j = 0; j < 3; j++) ans += tmp[i + j];        
            ans += '-';
            i += 3;  
        }

        if(m - i == 4){
            for(int j = 0; j < 2; j++) ans += tmp[i + j]; 
            ans += '-';
            i += 2;
            for(int j = 0; j < 2; j++) ans += tmp[i + j]; 
        }else{
            for(int j = 0; i + j < m; j++){
                ans += tmp[i + j];
            }
        }
        
        return ans;
    }
};

```
## My Notes - 我的笔记


No notes

