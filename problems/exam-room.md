
# 855. Exam Room - 考场就座

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Design-设计-blue.svg">   <img src="https://img.shields.io/badge/Ordered Set-有序集合-blue.svg">   <img src="https://img.shields.io/badge/Heap (Priority Queue)-堆（优先队列）-blue.svg">  


## Description - 题目描述

### EN:
<p>There is an exam room with <code>n</code> seats in a single row labeled from <code>0</code> to <code>n - 1</code>.</p>

<p>When a student enters the room, they must sit in the seat that maximizes the distance to the closest person. If there are multiple such seats, they sit in the seat with the lowest number. If no one is in the room, then the student sits at seat number <code>0</code>.</p>

<p>Design a class that simulates the mentioned exam room.</p>

<p>Implement the <code>ExamRoom</code> class:</p>

<ul>
	<li><code>ExamRoom(int n)</code> Initializes the object of the exam room with the number of the seats <code>n</code>.</li>
	<li><code>int seat()</code> Returns the label of the seat at which the next student will set.</li>
	<li><code>void leave(int p)</code> Indicates that the student sitting at seat <code>p</code> will leave the room. It is guaranteed that there will be a student sitting at seat <code>p</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input</strong>
[&quot;ExamRoom&quot;, &quot;seat&quot;, &quot;seat&quot;, &quot;seat&quot;, &quot;seat&quot;, &quot;leave&quot;, &quot;seat&quot;]
[[10], [], [], [], [], [4], []]
<strong>Output</strong>
[null, 0, 9, 4, 2, null, 5]

<strong>Explanation</strong>
ExamRoom examRoom = new ExamRoom(10);
examRoom.seat(); // return 0, no one is in the room, then the student sits at seat number 0.
examRoom.seat(); // return 9, the student sits at the last seat number 9.
examRoom.seat(); // return 4, the student sits at the last seat number 4.
examRoom.seat(); // return 2, the student sits at the last seat number 2.
examRoom.leave(4);
examRoom.seat(); // return 5, the student sits at the last seat number 5.

</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>9</sup></code></li>
	<li>It is guaranteed that there is a student sitting at seat <code>p</code>.</li>
	<li>At most <code>10<sup>4</sup></code> calls will be made to <code>seat</code> and <code>leave</code>.</li>
</ul>


### ZH-CN:
<p>在考场里，一排有&nbsp;<code>N</code>&nbsp;个座位，分别编号为&nbsp;<code>0, 1, 2, ..., N-1</code>&nbsp;。</p>

<p>当学生进入考场后，他必须坐在能够使他与离他最近的人之间的距离达到最大化的座位上。如果有多个这样的座位，他会坐在编号最小的座位上。(另外，如果考场里没有人，那么学生就坐在 0 号座位上。)</p>

<p>返回&nbsp;<code>ExamRoom(int N)</code>&nbsp;类，它有两个公开的函数：其中，函数&nbsp;<code>ExamRoom.seat()</code>&nbsp;会返回一个&nbsp;<code>int</code>&nbsp;（整型数据），代表学生坐的位置；函数&nbsp;<code>ExamRoom.leave(int p)</code>&nbsp;代表坐在座位 <code>p</code> 上的学生现在离开了考场。每次调用&nbsp;<code>ExamRoom.leave(p)</code>&nbsp;时都保证有学生坐在座位&nbsp;<code>p</code>&nbsp;上。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[&quot;ExamRoom&quot;,&quot;seat&quot;,&quot;seat&quot;,&quot;seat&quot;,&quot;seat&quot;,&quot;leave&quot;,&quot;seat&quot;], [[10],[],[],[],[],[4],[]]
<strong>输出：</strong>[null,0,9,4,2,null,5]
<strong>解释：</strong>
ExamRoom(10) -&gt; null
seat() -&gt; 0，没有人在考场里，那么学生坐在 0 号座位上。
seat() -&gt; 9，学生最后坐在 9 号座位上。
seat() -&gt; 4，学生最后坐在 4 号座位上。
seat() -&gt; 2，学生最后坐在 2 号座位上。
leave(4) -&gt; null
seat() -&gt; 5，学生最后坐在 5 号座位上。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>1 &lt;= N &lt;= 10^9</code></li>
	<li>在所有的测试样例中&nbsp;<code>ExamRoom.seat()</code>&nbsp;和&nbsp;<code>ExamRoom.leave()</code>&nbsp;最多被调用&nbsp;<code>10^4</code>&nbsp;次。</li>
	<li>保证在调用&nbsp;<code>ExamRoom.leave(p)</code>&nbsp;时有学生正坐在座位 <code>p</code> 上。</li>
</ol>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/exam-room/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/exam-room/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 388 ms | 19.8 MB | 2022/12/30 15:05 |

```cpp

class ExamRoom {
private:
    set<int> st;
    int N;
public:
    ExamRoom(int n): N(n) {}
    
    int seat() {
        if(st.empty()){
            st.insert(0);
            return 0;
        }

        int pre = *st.begin(), idx = 0, mx = pre;
        for(auto u: st){
            if((u - pre) / 2 > mx){
                mx = (u - pre) / 2;
                idx = (u + pre) / 2;
            }
            pre = u;
        }

        if((N - 1 - pre) > mx) idx = N - 1;
        st.insert(idx);
        return idx;
    }
    
    void leave(int p) {
        st.erase(p);
    }
};

/**
 * Your ExamRoom object will be instantiated and called as such:
 * ExamRoom* obj = new ExamRoom(n);
 * int param_1 = obj->seat();
 * obj->leave(p);
 */

```
## My Notes - 我的笔记


No notes

