
# 1629. Slowest Key - 按键持续时间最长的键

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/String-字符串-blue.svg">  


## Description - 题目描述

### EN:
<p>A newly designed keypad was tested, where a tester pressed a sequence of <code>n</code> keys, one at a time.</p>

<p>You are given a string <code>keysPressed</code> of length <code>n</code>, where <code>keysPressed[i]</code> was the <code>i<sup>th</sup></code> key pressed in the testing sequence, and a sorted list <code>releaseTimes</code>, where <code>releaseTimes[i]</code> was the time the <code>i<sup>th</sup></code> key was released. Both arrays are <strong>0-indexed</strong>. The <code>0<sup>th</sup></code> key was pressed at the time <code>0</code>,&nbsp;and every subsequent key was pressed at the <strong>exact</strong> time the previous key was released.</p>

<p>The tester wants to know the key of the keypress that had the <strong>longest duration</strong>. The <code>i<sup>th</sup></code><sup> </sup>keypress had a <strong>duration</strong> of <code>releaseTimes[i] - releaseTimes[i - 1]</code>, and the <code>0<sup>th</sup></code> keypress had a duration of <code>releaseTimes[0]</code>.</p>

<p>Note that the same key could have been pressed multiple times during the test, and these multiple presses of the same key <strong>may not</strong> have had the same <strong>duration</strong>.</p>

<p><em>Return the key of the keypress that had the <strong>longest duration</strong>. If there are multiple such keypresses, return the lexicographically largest key of the keypresses.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> releaseTimes = [9,29,49,50], keysPressed = &quot;cbcd&quot;
<strong>Output:</strong> &quot;c&quot;
<strong>Explanation:</strong> The keypresses were as follows:
Keypress for &#39;c&#39; had a duration of 9 (pressed at time 0 and released at time 9).
Keypress for &#39;b&#39; had a duration of 29 - 9 = 20 (pressed at time 9 right after the release of the previous character and released at time 29).
Keypress for &#39;c&#39; had a duration of 49 - 29 = 20 (pressed at time 29 right after the release of the previous character and released at time 49).
Keypress for &#39;d&#39; had a duration of 50 - 49 = 1 (pressed at time 49 right after the release of the previous character and released at time 50).
The longest of these was the keypress for &#39;b&#39; and the second keypress for &#39;c&#39;, both with duration 20.
&#39;c&#39; is lexicographically larger than &#39;b&#39;, so the answer is &#39;c&#39;.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> releaseTimes = [12,23,36,46,62], keysPressed = &quot;spuda&quot;
<strong>Output:</strong> &quot;a&quot;
<strong>Explanation:</strong> The keypresses were as follows:
Keypress for &#39;s&#39; had a duration of 12.
Keypress for &#39;p&#39; had a duration of 23 - 12 = 11.
Keypress for &#39;u&#39; had a duration of 36 - 23 = 13.
Keypress for &#39;d&#39; had a duration of 46 - 36 = 10.
Keypress for &#39;a&#39; had a duration of 62 - 46 = 16.
The longest of these was the keypress for &#39;a&#39; with duration 16.</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>releaseTimes.length == n</code></li>
	<li><code>keysPressed.length == n</code></li>
	<li><code>2 &lt;= n &lt;= 1000</code></li>
	<li><code>1 &lt;= releaseTimes[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>releaseTimes[i] &lt; releaseTimes[i+1]</code></li>
	<li><code>keysPressed</code> contains only lowercase English letters.</li>
</ul>


### ZH-CN:
<p>LeetCode 设计了一款新式键盘，正在测试其可用性。测试人员将会点击一系列键（总计 <code>n</code> 个），每次一个。</p>

<p>给你一个长度为 <code>n</code> 的字符串 <code>keysPressed</code> ，其中 <code>keysPressed[i]</code> 表示测试序列中第 <code>i</code> 个被按下的键。<code>releaseTimes</code> 是一个升序排列的列表，其中 <code>releaseTimes[i]</code> 表示松开第 <code>i</code> 个键的时间。字符串和数组的 <strong>下标都从 0 开始</strong> 。第 <code>0</code> 个键在时间为 <code>0</code> 时被按下，接下来每个键都 <strong>恰好</strong> 在前一个键松开时被按下。</p>

<p>测试人员想要找出按键 <strong>持续时间最长</strong> 的键。第 <code>i</code><sup> </sup>次按键的持续时间为 <code>releaseTimes[i] - releaseTimes[i - 1]</code> ，第 <code>0</code> 次按键的持续时间为 <code>releaseTimes[0]</code> 。</p>

<p>注意，测试期间，同一个键可以在不同时刻被多次按下，而每次的持续时间都可能不同。</p>

<p>请返回单次按键 <strong>持续时间最长</strong> 的键，如果有多个这样的键，则返回 <strong>按字母顺序排列最大</strong> 的那个键。</p>

<p>&nbsp;</p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>releaseTimes = [9,29,49,50], keysPressed = "cbcd"
<strong>输出：</strong>"c"
<strong>解释：</strong>按键顺序和持续时间如下：
按下 'c' ，持续时间 9（时间 0 按下，时间 9 松开）
按下 'b' ，持续时间 29 - 9 = 20（松开上一个键的时间 9 按下，时间 29 松开）
按下 'c' ，持续时间 49 - 29 = 20（松开上一个键的时间 29 按下，时间 49 松开）
按下 'd' ，持续时间 50 - 49 = 1（松开上一个键的时间 49 按下，时间 50 松开）
按键持续时间最长的键是 'b' 和 'c'（第二次按下时），持续时间都是 20
'c' 按字母顺序排列比 'b' 大，所以答案是 'c'
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>releaseTimes = [12,23,36,46,62], keysPressed = "spuda"
<strong>输出：</strong>"a"
<strong>解释：</strong>按键顺序和持续时间如下：
按下 's' ，持续时间 12
按下 'p' ，持续时间 23 - 12 = 11
按下 'u' ，持续时间 36 - 23 = 13
按下 'd' ，持续时间 46 - 36 = 10
按下 'a' ，持续时间 62 - 46 = 16
按键持续时间最长的键是 'a' ，持续时间 16</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>releaseTimes.length == n</code></li>
	<li><code>keysPressed.length == n</code></li>
	<li><code>2 &lt;= n &lt;= 1000</code></li>
	<li><code>1 &lt;= releaseTimes[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>releaseTimes[i] &lt; releaseTimes[i+1]</code></li>
	<li><code>keysPressed</code> 仅由小写英文字母组成</li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/slowest-key/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/slowest-key/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 0 ms | 10.5 MB | 2022/01/09 0:40 |

```cpp

class Solution {
public:
    char slowestKey(vector<int>& releaseTimes, string keysPressed) {
        int sizeOfTime = releaseTimes.size();
        int ans = 0;
        int maxVal = INT_MIN;
        for(int i = sizeOfTime - 1; i > 0; i--){
            releaseTimes[i] = releaseTimes[i] - releaseTimes[i - 1];
        }


        for(int i = 0; i < sizeOfTime; i++){
            if(maxVal < releaseTimes[i]){
                maxVal = releaseTimes[i];
                //ans = keysPressed[i];
            }
        }


        for(int i = 0; i < sizeOfTime; i++){
            if(maxVal == releaseTimes[i] && ans < keysPressed[i]){
                ans = keysPressed[i];
            }
        }
        return ans;
       
    }
};

```
## My Notes - 我的笔记


No notes

