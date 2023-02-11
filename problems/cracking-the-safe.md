
# 753. Cracking the Safe - 破解保险箱

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Depth First Search-深度优先搜索-blue.svg">   <img src="https://img.shields.io/badge/Graph-图-blue.svg">   <img src="https://img.shields.io/badge/Eulerian Circuit-欧拉回路-blue.svg">  


## Description - 题目描述

### EN:
<p>There is a safe protected by a password. The password is a sequence of <code>n</code> digits where each digit can be in the range <code>[0, k - 1]</code>.</p>

<p>The safe has a peculiar way of checking the password. When you enter in a sequence, it checks the <strong>most recent </strong><code>n</code><strong> digits</strong> that were entered each time you type a digit.</p>

<ul>
	<li>For example, the correct password is <code>&quot;345&quot;</code> and you enter in <code>&quot;012345&quot;</code>:

	<ul>
		<li>After typing <code>0</code>, the most recent <code>3</code> digits is <code>&quot;0&quot;</code>, which is incorrect.</li>
		<li>After typing <code>1</code>, the most recent <code>3</code> digits is <code>&quot;01&quot;</code>, which is incorrect.</li>
		<li>After typing <code>2</code>, the most recent <code>3</code> digits is <code>&quot;012&quot;</code>, which is incorrect.</li>
		<li>After typing <code>3</code>, the most recent <code>3</code> digits is <code>&quot;123&quot;</code>, which is incorrect.</li>
		<li>After typing <code>4</code>, the most recent <code>3</code> digits is <code>&quot;234&quot;</code>, which is incorrect.</li>
		<li>After typing <code>5</code>, the most recent <code>3</code> digits is <code>&quot;345&quot;</code>, which is correct and the safe unlocks.</li>
	</ul>
	</li>
</ul>

<p>Return <em>any string of <strong>minimum length</strong> that will unlock the safe <strong>at some point</strong> of entering it</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> n = 1, k = 2
<strong>Output:</strong> &quot;10&quot;
<strong>Explanation:</strong> The password is a single digit, so enter each digit. &quot;01&quot; would also unlock the safe.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> n = 2, k = 2
<strong>Output:</strong> &quot;01100&quot;
<strong>Explanation:</strong> For each possible password:
- &quot;00&quot; is typed in starting from the 4<sup>th</sup> digit.
- &quot;01&quot; is typed in starting from the 1<sup>st</sup> digit.
- &quot;10&quot; is typed in starting from the 3<sup>rd</sup> digit.
- &quot;11&quot; is typed in starting from the 2<sup>nd</sup> digit.
Thus &quot;01100&quot; will unlock the safe. &quot;01100&quot;, &quot;10011&quot;, and &quot;11001&quot; would also unlock the safe.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 4</code></li>
	<li><code>1 &lt;= k &lt;= 10</code></li>
	<li><code>1 &lt;= k<sup>n</sup> &lt;= 4096</code></li>
</ul>


### ZH-CN:
<p>有一个需要密码才能打开的保险箱。密码是&nbsp;<code>n</code> 位数, 密码的每一位都是范围&nbsp;<code>[0, k - 1]</code>&nbsp;中的一个数字。</p>

<p>保险箱有一种特殊的密码校验方法，你可以随意输入密码序列，保险箱会自动记住 <strong>最后&nbsp;<code>n</code>&nbsp;位输入</strong> ，如果匹配，则能够打开保险箱。</p>

<ul>
	<li>例如，正确的密码是 <code>"345"</code> ，并且你输入的是 <code>"012345"</code> ：

	<ul>
		<li>输入 <code>0</code> 之后，最后 <code>3</code> 位输入是 <code>"0"</code> ，不正确。</li>
		<li>输入 <code>1</code> 之后，最后 <code>3</code> 位输入是 <code>"01"</code> ，不正确。</li>
		<li>输入 <code>2</code> 之后，最后 <code>3</code> 位输入是 <code>"012"</code> ，不正确。</li>
		<li>输入 <code>3</code> 之后，最后 <code>3</code> 位输入是 <code>"123"</code> ，不正确。</li>
		<li>输入 <code>4</code> 之后，最后 <code>3</code> 位输入是 <code>"234"</code> ，不正确。</li>
		<li>输入 <code>5</code> 之后，最后 <code>3</code> 位输入是 <code>"345"</code> ，正确，打开保险箱。</li>
	</ul>
	</li>
</ul>

<p>在只知道密码位数 <code>n</code> 和范围边界 <code>k</code> 的前提下，请你找出并返回确保在输入的 <strong>某个时刻</strong> 能够打开保险箱的任一 <strong>最短</strong> 密码序列 。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 1, k = 2
<strong>输出：</strong>"10"
<strong>解释：</strong>密码只有 1 位，所以输入每一位就可以。"01" 也能够确保打开保险箱。
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 2, k = 2
<strong>输出：</strong>"01100"
<strong>解释：</strong>对于每种可能的密码：
- "00" 从第 4 位开始输入。
- "01" 从第 1 位开始输入。
- "10" 从第 3 位开始输入。
- "11" 从第 2 位开始输入。
因此 "01100" 可以确保打开保险箱。"01100"、"10011" 和 "11001" 也可以确保打开保险箱。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 4</code></li>
	<li><code>1 &lt;= k &lt;= 10</code></li>
	<li><code>1 &lt;= k<sup>n</sup> &lt;= 4096</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/cracking-the-safe/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/cracking-the-safe/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 4 ms | 6.4 MB | 2023/01/09 15:37 |

```cpp

class Solution {
public:
    string crackSafe(int n, int k) {
        //k的n - 1次方个节点，每个节点有k条出边，所以图有k的n次方条边。
		int edgesNum = pow(k, n), nodeNum = pow(k, n - 1);
		//数组node是用来存储每个节点的出边，出边用索引表示，最大索引是k - 1
		vector<int> node(nodeNum, k - 1);
		//这里多出来的n-1，其实是因为要初始化第一个节点"00..0"
		string s(edgesNum + (n - 1), '0');
                //idx表示节点索引
		for (int i = n - 1, idx = 0; i < s.size(); ++i) {
			int edge = node[idx];
			s[i] = edge + '0';
			//将对应的边出栈
			node[idx]--;
			//一共k ^ (n - 1)个节点，可以看作n - 2位的k进制数能表示的数，
			//即最小为0，最大为k ^ (n - 1) - 1 (想象一下10进制，比如10^2，就好理解了)。
			//如果当前节点对应的数为 a1a2⋯an−1，那么它的第 x 条出边就连向数 a2⋯an−1x 对应的节点
			//那么计算通向的下一个节点，需要先对当前的数进行左移操作（即在数值右端补0），
			//所以先 * k, 然后加上出边x，最后再通过 % 来抹去高位的a1。
			// 
			//官解的highest用的是10进制，由于k的取值范围是[1, 10]，所以是可行的。
			//如果你将官解的highest改成16进制，也是可行的。具体看评论提供的代码。
			//但是这里是否可以直接用10来取代k呢？不可行，如果换成了10，
			//k小于10的时候，其实是将原本紧密排列的节点索引idx零散地映射在了[0, 10^(n-1))上，
			//所以idx的取值是可能大于k ^ (n - 1) - 1，就会在node上发生数组越界。
                        //如果要采用10进制，需要对数组进行扩容。具体参考评论提供的代码。
			idx = (idx * k + edge) % nodeNum;
		}
		return s;
    }
};

```
## My Notes - 我的笔记


No notes

