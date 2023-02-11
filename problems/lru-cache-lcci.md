
# 面试题 16.25. LRU Cache LCCI - LRU 缓存

## Tags - 题目标签

 <img src="https://img.shields.io/badge/Design-设计-blue.svg">   <img src="https://img.shields.io/badge/Hash Table-哈希表-blue.svg">   <img src="https://img.shields.io/badge/Linked List-链表-blue.svg">   <img src="https://img.shields.io/badge/Doubly Linked List-双向链表-blue.svg">  


## Description - 题目描述

### EN:
<p>Design and build a &quot;least recently used&quot; cache, which evicts the least recently used item. The cache should map from keys to values (allowing you to insert and retrieve a value associ&shy;ated with a particular key) and be initialized with a max size. When it is full, it should evict the least recently used item.</p>

<p>You should implement following operations:&nbsp;&nbsp;<code>get</code>&nbsp;and <code>put</code>.</p>

<p>Get a value by key:&nbsp;<code>get(key)</code> - If key is in the cache, return the value, otherwise return -1.<br />
Write a key-value pair to the cache:&nbsp;<code>put(key, value)</code> - If the key is not in the cache, then write its value to the cache. Evict the least recently used item before writing if necessary.</p>

<p><strong>Example:</strong></p>

<pre>
LRUCache cache = new LRUCache( 2 /* capacity */ );

cache.put(1, 1);
cache.put(2, 2);
cache.get(1);       // returns 1
cache.put(3, 3);    // evicts key 2
cache.get(2);       // returns -1 (not found)
cache.put(4, 4);    // evicts key 1
cache.get(1);       // returns -1 (not found)
cache.get(3);       // returns 3
cache.get(4);       // returns 4
</pre>


### ZH-CN:
<p>设计和构建一个&ldquo;最近最少使用&rdquo;缓存，该缓存会删除最近最少使用的项目。缓存应该从键映射到值(允许你插入和检索特定键对应的值)，并在初始化时指定最大容量。当缓存被填满时，它应该删除最近最少使用的项目。</p>

<p>它应该支持以下操作： 获取数据 <code>get</code> 和 写入数据 <code>put</code> 。</p>

<p>获取数据 <code>get(key)</code> - 如果密钥 (key) 存在于缓存中，则获取密钥的值（总是正数），否则返回 -1。<br>
写入数据 <code>put(key, value)</code> - 如果密钥不存在，则写入其数据值。当缓存容量达到上限时，它应该在写入新数据之前删除最近最少使用的数据值，从而为新的数据值留出空间。</p>

<p><strong>示例:</strong></p>

<pre>LRUCache cache = new LRUCache( 2 /* 缓存容量 */ );

cache.put(1, 1);
cache.put(2, 2);
cache.get(1);       // 返回  1
cache.put(3, 3);    // 该操作会使得密钥 2 作废
cache.get(2);       // 返回 -1 (未找到)
cache.put(4, 4);    // 该操作会使得密钥 1 作废
cache.get(1);       // 返回 -1 (未找到)
cache.get(3);       // 返回  3
cache.get(4);       // 返回  4
</pre>



## Link - 题目链接

[LeetCode](https://leetcode.com/problems/lru-cache-lcci/description/)  -  [LeetCode-CN](https://leetcode.cn/problems/lru-cache-lcci/description/)
## Latest Accepted Submissions - 最近一次 AC 的提交


| Language | Runtime | Memory | Submission Time |
|:---:|:---:|:---:|:---:|
| cpp  | 88 ms | 40.1 MB | 2022/10/30 22:05 |

```cpp

class Node{
public:
    int key;
    int val;
    Node* prev;
    Node* next;
    Node(int key, int val): key(key), val(val), prev(nullptr), next(nullptr){};
};

class DLinkedlist{
public:
    Node* head;
    Node* tail;
    DLinkedlist(): head(new Node(-1, -1)), tail(new Node(-1, -1)){
        head->next = tail;
        tail->prev = head;
    };
};

class LRUCache {
public:
    int capacity;
    int n;
    unordered_map<int, Node*> hm;
    DLinkedlist dll;

    LRUCache(int capacity): capacity(capacity), n(0), dll(DLinkedlist()) {};
    
    // rm node and add new node to the head and return that node
    Node* move2Head(Node* node){
        int key = node->key;
        int val = node->val;
        rmNode(node);
        Node* newNode = new Node(key, val);
        add2Head(newNode);
        return newNode;
    }

    // rm node and add new node to the head(update the val)and return that node
    Node* move2Head(Node* node, int val){
        int key = node->key;
        rmNode(node);
        Node* newNode = new Node(key, val);
        add2Head(newNode);
        return newNode;
    }

    // remove the spcific node
    void rmNode(Node* node){
        assert(node != nullptr);
        // rm odd hm
        hm.erase(node->key);

        Node* prev = node->prev;
        Node* next = node->next;
        prev->next = next;
        next->prev = prev;
        delete(node);
    }

    // add the node the head
    void add2Head(Node* node){
        Node* head = this->dll.head;
        Node* next = head->next;
        head->next = node;
        next->prev = node;
        node->prev = head;
        node->next = next;
    }

    int get(int key) {
        // if key not exist, return -1
        if(!hm.count(key)) return -1;
        else{ // if key exist, return the val and move the node to the front
            Node* node = hm[key];       
            // move the node to the head
            Node* newNode = move2Head(node);
            // update the hm
            hm[key] = newNode;
            // return ans
            return newNode->val;
        }
    }
    
    void put(int key, int value) {
        // if the key exist, update the value and hs and move to the front
        if(hm.count(key)){
            Node* toUpdate = hm[key];
            // move the node to the head
            Node* newNode = move2Head(toUpdate, value);
            // add to the hm
            hm[key] = newNode;
        }else{ // if not exist
            // if full, del the tail and add to the front
            assert(this->capacity >= n);
            if(this->capacity == n){
                rmNode(this->dll.tail->prev);
                Node * node = new Node(key, value);
                add2Head(node);
                // add to hm
                hm[key] = node;
            }else{ // if not full, add to front and update hm and n
                Node * node = new Node(key, value);
                add2Head(node);
                // add to hm
                hm[key] = node;
                // update n
                this->n++;
            }
        }
    }
};

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache* obj = new LRUCache(capacity);
 * int param_1 = obj->get(key);
 * obj->put(key,value);
 */

```
## My Notes - 我的笔记


No notes

