> [题目链接](https://leetcode-cn.com/problems/implement-queue-using-stacks/)

我的解答：

```java
package top.xijinian.stack;

import java.util.Stack;

class MyQueue {

    /** Initialize your data structure here. */
    private final Stack<Integer> pushStack;
    private final Stack<Integer> popStack;
    private int total = 0;
    private int used = 0;

    public MyQueue() {
        this.pushStack = new Stack<>();
        this.popStack = new Stack<>();
    }
    
    /** Push element x to the back of queue. */
    public void push(int x) {
        pushStack.push(x);
        total++;
    }
    
    /** Removes the element from in front of queue and returns that element. */
    public int pop() {
        peek();
        return popStack.pop();
    }
    
    /** Get the front element. */
    public int peek() {
        if (popStack.isEmpty()) {
            int count = total - used;
            while (count > 0) {
                popStack.push(pushStack.pop());
                count--;
                used++;
            }
        }
        return popStack.peek();
    }
    
    /** Returns whether the queue is empty. */
    public boolean empty() {
        return popStack.isEmpty() && total == used;
    }
}
```

