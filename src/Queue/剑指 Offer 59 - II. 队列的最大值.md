# [剑指 Offer 59 - II. 队列的最大值](https://leetcode-cn.com/problems/dui-lie-de-zui-da-zhi-lcof/)

## 题目

请定义一个队列并实现函数 max_value 得到队列里的最大值，要求函数max_value、push_back 和 pop_front 的均摊时间复杂度都是O(1)。

若队列为空，pop_front 和 max_value 需要返回 -1

```
示例 1：

输入: 
["MaxQueue","push_back","push_back","max_value","pop_front","max_value"]
[[],[1],[2],[],[],[]]
输出: [null,null,null,2,1,2]
示例 2：

输入: 
["MaxQueue","pop_front","max_value"]
[[],[],[]]
输出: [null,-1,-1]
```

## 思路

**普通队列 + 双端队列**

- 普通队列 queue 维护正常的出队和入队
  - 出队时，如果 queue.poll( ) 等于 deque 的对头元素，则deque的对头元素也要弹出。
- 双端队列 deque 维护最大值
  - 进队时，如果双端队列的尾端值 < value，则弹出尾端值，直到尾端值 >= value，value入队



## 代码

```java
class MaxQueue {
    private Queue<Integer> queue; // 正常出，退
    private Deque<Integer> deque; // 保存最大值

    public MaxQueue() {
        this.queue = new LinkedList<>();
        this.deque = new LinkedList<>();
    }
    
    public int max_value() {
        if(queue.isEmpty()) return -1;
        return deque.peekFirst();
    }
    
    public void push_back(int value) {
        // queue正常入队
        queue.offer(value);

        // 维护deque
        while(!deque.isEmpty() && deque.peekLast() < value) {
            deque.pollLast();   
        }
        deque.offerLast(value);
    }
    
    public int pop_front() {
        if(queue.isEmpty()) return -1;
        int tem = queue.poll();
        if(deque.peekFirst() == tem)
            deque.pollFirst();
        return tem;
    }
}

/**
 * Your MaxQueue object will be instantiated and called as such:
 * MaxQueue obj = new MaxQueue();
 * int param_1 = obj.max_value();
 * obj.push_back(value);
 * int param_3 = obj.pop_front();
 */
```

