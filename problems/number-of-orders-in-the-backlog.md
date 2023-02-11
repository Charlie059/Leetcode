
# 1801. Number of Orders in the Backlog - 积压订单中的订单总数

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Array-数组-blue.svg">   <img src="https://img.shields.io/badge/Simulation-模拟-blue.svg">   <img src="https://img.shields.io/badge/Heap (Priority Queue)-堆（优先队列）-blue.svg">  


## Description - 题目描述

### EN:
<p>You are given a 2D integer array <code>orders</code>, where each <code>orders[i] = [price<sub>i</sub>, amount<sub>i</sub>, orderType<sub>i</sub>]</code> denotes that <code>amount<sub>i</sub></code><sub> </sub>orders have been placed of type <code>orderType<sub>i</sub></code> at the price <code>price<sub>i</sub></code>. The <code>orderType<sub>i</sub></code> is:</p>

<ul>
	<li><code>0</code> if it is a batch of <code>buy</code> orders, or</li>
	<li><code>1</code> if it is a batch of <code>sell</code> orders.</li>
</ul>

<p>Note that <code>orders[i]</code> represents a batch of <code>amount<sub>i</sub></code> independent orders with the same price and order type. All orders represented by <code>orders[i]</code> will be placed before all orders represented by <code>orders[i+1]</code> for all valid <code>i</code>.</p>

<p>There is a <strong>backlog</strong> that consists of orders that have not been executed. The backlog is initially empty. When an order is placed, the following happens:</p>

<ul>
	<li>If the order is a <code>buy</code> order, you look at the <code>sell</code> order with the <strong>smallest</strong> price in the backlog. If that <code>sell</code> order&#39;s price is <strong>smaller than or equal to</strong> the current <code>buy</code> order&#39;s price, they will match and be executed, and that <code>sell</code> order will be removed from the backlog. Else, the <code>buy</code> order is added to the backlog.</li>
	<li>Vice versa, if the order is a <code>sell</code> order, you look at the <code>buy</code> order with the <strong>largest</strong> price in the backlog. If that <code>buy</code> order&#39;s price is <strong>larger than or equal to</strong> the current <code>sell</code> order&#39;s price, they will match and be executed, and that <code>buy</code> order will be removed from the backlog. Else, the <code>sell</code> order is added to the backlog.</li>
</ul>

<p>Return <em>the total <strong>amount</strong> of orders in the backlog after placing all the orders from the input</em>. Since this number can be large, return it <strong>modulo</strong> <code>10<sup>9</sup> + 7</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/11/ex1.png" style="width: 450px; height: 479px;" />
<pre>
<strong>Input:</strong> orders = [[10,5,0],[15,2,1],[25,1,1],[30,4,0]]
<strong>Output:</strong> 6
<strong>Explanation:</strong> Here is what happens with the orders:
- 5 orders of type buy with price 10 are placed. There are no sell orders, so the 5 orders are added to the backlog.
- 2 orders of type sell with price 15 are placed. There are no buy orders with prices larger than or equal to 15, so the 2 orders are added to the backlog.
- 1 order of type sell with price 25 is placed. There are no buy orders with prices larger than or equal to 25 in the backlog, so this order is added to the backlog.
- 4 orders of type buy with price 30 are placed. The first 2 orders are matched with the 2 sell orders of the least price, which is 15 and these 2 sell orders are removed from the backlog. The 3<sup>rd</sup> order is matched with the sell order of the least price, which is 25 and this sell order is removed from the backlog. Then, there are no more sell orders in the backlog, so the 4<sup>th</sup> order is added to the backlog.
Finally, the backlog has 5 buy orders with price 10, and 1 buy order with price 30. So the total number of orders in the backlog is 6.
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/11/ex2.png" style="width: 450px; height: 584px;" />
<pre>
<strong>Input:</strong> orders = [[7,1000000000,1],[15,3,0],[5,999999995,0],[5,1,1]]
<strong>Output:</strong> 999999984
<strong>Explanation:</strong> Here is what happens with the orders:
- 10<sup>9</sup> orders of type sell with price 7 are placed. There are no buy orders, so the 10<sup>9</sup> orders are added to the backlog.
- 3 orders of type buy with price 15 are placed. They are matched with the 3 sell orders with the least price which is 7, and those 3 sell orders are removed from the backlog.
- 999999995 orders of type buy with price 5 are placed. The least price of a sell order is 7, so the 999999995 orders are added to the backlog.
- 1 order of type sell with price 5 is placed. It is matched with the buy order of the highest price, which is 5, and that buy order is removed from the backlog.
Finally, the backlog has (1000000000-3) sell orders with price 7, and (999999995-1) buy orders with price 5. So the total number of orders = 1999999991, which is equal to 999999984 % (10<sup>9</sup> + 7).
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= orders.length &lt;= 10<sup>5</sup></code></li>
	<li><code>orders[i].length == 3</code></li>
	<li><code>1 &lt;= price<sub>i</sub>, amount<sub>i</sub> &lt;= 10<sup>9</sup></code></li>
	<li><code>orderType<sub>i</sub></code> is either <code>0</code> or <code>1</code>.</li>
</ul>

### ZH-CN:
<p>给你一个二维整数数组 <code>orders</code> ，其中每个 <code>orders[i] = [price<sub>i</sub>, amount<sub>i</sub>, orderType<sub>i</sub>]</code> 表示有 <code>amount<sub>i</sub></code><sub> </sub>笔类型为 <code>orderType<sub>i</sub></code> 、价格为 <code>price<sub>i</sub></code> 的订单。</p>

<p>订单类型 <code>orderType<sub>i</sub></code> 可以分为两种：</p>

<ul>
	<li><code>0</code> 表示这是一批采购订单 <code>buy</code></li>
	<li><code>1</code> 表示这是一批销售订单 <code>sell</code></li>
</ul>

<p>注意，<code>orders[i]</code> 表示一批共计 <code>amount<sub>i</sub></code> 笔的独立订单，这些订单的价格和类型相同。对于所有有效的 <code>i</code> ，由 <code>orders[i]</code> 表示的所有订单提交时间均早于 <code>orders[i+1]</code> 表示的所有订单。</p>

<p>存在由未执行订单组成的 <strong>积压订单</strong> 。积压订单最初是空的。提交订单时，会发生以下情况：</p>

<ul>
	<li>如果该订单是一笔采购订单 <code>buy</code> ，则可以查看积压订单中价格 <strong>最低</strong> 的销售订单 <code>sell</code> 。如果该销售订单 <code>sell</code> 的价格 <strong>低于或等于</strong> 当前采购订单 <code>buy</code> 的价格，则匹配并执行这两笔订单，并将销售订单 <code>sell</code> 从积压订单中删除。否则，采购订单 <code>buy</code> 将会添加到积压订单中。</li>
	<li>反之亦然，如果该订单是一笔销售订单 <code>sell</code> ，则可以查看积压订单中价格 <strong>最高</strong> 的采购订单 <code>buy</code> 。如果该采购订单 <code>buy</code> 的价格 <strong>高于或等于</strong> 当前销售订单 <code>sell</code> 的价格，则匹配并执行这两笔订单，并将采购订单 <code>buy</code> 从积压订单中删除。否则，销售订单 <code>sell</code> 将会添加到积压订单中。</li>
</ul>

<p>输入所有订单后，返回积压订单中的 <strong>订单总数</strong> 。由于数字可能很大，所以需要返回对 <code>10<sup>9</sup> + 7</code> 取余的结果。</p>

<p> </p>

<p><strong>示例 1：</strong></p>
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2021/03/21/ex1.png" style="width: 450px; height: 479px;" />
<pre>
<strong>输入：</strong>orders = [[10,5,0],[15,2,1],[25,1,1],[30,4,0]]
<strong>输出：</strong>6
<strong>解释：</strong>输入订单后会发生下述情况：
- 提交 5 笔采购订单，价格为 10 。没有销售订单，所以这 5 笔订单添加到积压订单中。
- 提交 2 笔销售订单，价格为 15 。没有采购订单的价格大于或等于 15 ，所以这 2 笔订单添加到积压订单中。
- 提交 1 笔销售订单，价格为 25 。没有采购订单的价格大于或等于 25 ，所以这 1 笔订单添加到积压订单中。
- 提交 4 笔采购订单，价格为 30 。前 2 笔采购订单与价格最低（价格为 15）的 2 笔销售订单匹配，从积压订单中删除这 2 笔销售订单。第 3 笔采购订单与价格最低的 1 笔销售订单匹配，销售订单价格为 25 ，从积压订单中删除这 1 笔销售订单。积压订单中不存在更多销售订单，所以第 4 笔采购订单需要添加到积压订单中。
最终，积压订单中有 5 笔价格为 10 的采购订单，和 1 笔价格为 30 的采购订单。所以积压订单中的订单总数为 6 。
</pre>

<p><strong>示例 2：</strong></p>
<img alt="" src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2021/03/21/ex2.png" style="width: 450px; height: 584px;" />
<pre>
<strong>输入：</strong>orders = [[7,1000000000,1],[15,3,0],[5,999999995,0],[5,1,1]]
<strong>输出：</strong>999999984
<strong>解释：</strong>输入订单后会发生下述情况：
- 提交 10<sup>9</sup> 笔销售订单，价格为 7 。没有采购订单，所以这 10<sup>9</sup> 笔订单添加到积压订单中。
- 提交 3 笔采购订单，价格为 15 。这些采购订单与价格最低（价格为 7 ）的 3 笔销售订单匹配，从积压订单中删除这 3 笔销售订单。
- 提交 999999995 笔采购订单，价格为 5 。销售订单的最低价为 7 ，所以这 999999995 笔订单添加到积压订单中。
- 提交 1 笔销售订单，价格为 5 。这笔销售订单与价格最高（价格为 5 ）的 1 笔采购订单匹配，从积压订单中删除这 1 笔采购订单。
最终，积压订单中有 (1000000000-3) 笔价格为 7 的销售订单，和 (999999995-1) 笔价格为 5 的采购订单。所以积压订单中的订单总数为 1999999991 ，等于 999999984 % (10<sup>9</sup> + 7) 。</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= orders.length <= 10<sup>5</sup></code></li>
	<li><code>orders[i].length == 3</code></li>
	<li><code>1 <= price<sub>i</sub>, amount<sub>i</sub> <= 10<sup>9</sup></code></li>
	<li><code>orderType<sub>i</sub></code> 为 <code>0</code> 或 <code>1</code></li>
</ul>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/number-of-orders-in-the-backlog/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/number-of-orders-in-the-backlog/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 200 ms | 57.1 MB | 2023/01/01 16:18 |

```cpp

class Solution {
public:
    int getNumberOfBacklogOrders(vector<vector<int>>& orders) {
        const int MOD = pow(10, 9) + 7;

        auto less = [](const pair<int, int>& a, const pair<int, int>& b) { return a.first < b.first; };
        auto greater = [](const pair<int, int>& a, const pair<int, int>& b) { return a.first > b.first; };

        priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(less)> minQueue(less);
        priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(greater)> maxQueue(greater);

        long long totalOrders = 0, freeOrders = 0;

        for(const vector<int>& order: orders){
            const int price = order[0];
            const int num = order[1];
            const int type = order[2];

            if(type == 0) minQueue.push({price, num});  
            else maxQueue.push({price, num});

            totalOrders += num;

            while(!minQueue.empty() && !maxQueue.empty()){
                const int sell = maxQueue.top().first;
                const int buy = minQueue.top().first;
                const int sellNum = maxQueue.top().second;
                const int buyNum = minQueue.top().second;
                
                if(buy >= sell){
                    if(sellNum > buyNum){
                        int newValue = sellNum - buyNum;
                        minQueue.pop();
                        maxQueue.pop();
                        maxQueue.push({sell, newValue});

                        freeOrders += 2 * buyNum;
                    }else if(sellNum < buyNum){
                        int newValue = buyNum - sellNum;
                        minQueue.pop();
                        maxQueue.pop();
                        minQueue.push({buy, newValue});

                        freeOrders += 2 * sellNum;
                    }else{
                        minQueue.pop();
                        maxQueue.pop();
                        freeOrders += 2 * buyNum;
                    }  
                }else break;
            }
        }

        return (totalOrders - freeOrders) % MOD;
    }
};

```
## My Notes - 我的笔记


No notes

