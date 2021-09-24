> [题目链接](https://leetcode-cn.com/problems/sort-of-stacks-lcci/)

我的解答：

```java
package top.xijinian.stack;

import java.util.Stack;

class SortedStack {

    private final Stack<Integer> stack;
    private final Stack<Integer> helper;

    public SortedStack() {
        this.stack = new Stack<>();
        this.helper = new Stack<>();
    }
    
    public void push(int val) {
        if (stack.isEmpty()) {
            stack.push(val);
        } else {
            while (!stack.isEmpty() && stack.peek() < val) {
                helper.push(stack.pop());
            }
            helper.push(val);
            while (!helper.isEmpty()) {
                stack.push(helper.pop());
            }
        }
    }
    
    public void pop() {
        if (!stack.isEmpty()) {
            stack.pop();
        }
    }
    
    public int peek() {
        if (!stack.isEmpty()) {
            return stack.peek();
        } else {
            return -1;
        }
    }
    
    public boolean isEmpty() {
        return stack.isEmpty();
    }
}
```

