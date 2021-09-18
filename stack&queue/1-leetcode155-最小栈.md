> [题目链接](https://leetcode-cn.com/problems/min-stack/)

我的解答：

```java
package top.xijinian.stack;

import java.util.Stack;

class MinStack {

    /** initialize your data structure here. */
    private final Stack<Integer> stack;
    private final Stack<Integer> minStack;

    public MinStack() {
        stack = new Stack<>();
        minStack = new Stack<>();
    }
    
    public void push(int val) {
        stack.push(val);
        int currentMin;
        if (minStack.isEmpty()) {
            currentMin = val;
        } else {
            currentMin = val < minStack.peek() ? val : minStack.peek();
        }
        minStack.push(currentMin);
    }
    
    public void pop() {
        stack.pop();
        minStack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
        return minStack.peek();
    }
}
```

