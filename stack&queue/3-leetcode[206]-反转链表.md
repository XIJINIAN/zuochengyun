> [题目链接](https://leetcode-cn.com/problems/reverse-linked-list/)

我的解答：

1. 迭代版本

   ```java
   package top.xijinian.stack;
   
   public class Solution {
   
       public ListNode reverseList(ListNode head) {
           ListNode prev = null;
           ListNode curr = head;
           while (curr != null) {
               ListNode tempNext = curr.next;
               curr.next = prev;
               prev = curr;
               curr = tempNext;
           }
           return prev;
       }
   }
   ```

2. 递归版本

   ```java
   package top.xijinian.stack;
   
   public class Solution {
   
       public static ListNode reverseList(ListNode head) {
           if (head == null || head.next == null) {
               return head;
           }
           ListNode curr = reverseList(head.next);
           head.next.next = head;
           head.next = null;
           return curr;
       }
   }
   ```

