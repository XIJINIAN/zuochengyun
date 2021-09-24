> [题目链接](https://leetcode-cn.com/problems/sort-of-stacks-lcci/)
>
> 本题中的大部分 Java 题解都是错的（甚至没看到对的），推荐自己写一个 `main` 方法调试，看看 `List` `A` `B` `C` 是否按照预想的那样转移元素。

1. 原题

   - 递归解法

     ```java
     package top.xijinian.stack;
     
     import java.util.ArrayList;
     import java.util.List;
     
     class Solution {
     
         public void hanota(List<Integer> A, List<Integer> B, List<Integer> C) {
             process(A.size(), 'A', 'B', 'C', A, B, C);
         }
     
         private void process(int n, char from, char buff, char to, List<Integer> A, List<Integer> B, List<Integer> C) {
             if (n == 1) {
                 move(from, to, A, B, C);
             } else {
                 process(n - 1, from, to, buff, A, B, C);
                 move(from, to, A, B, C);
                 process(n - 1, buff, from, to, A, B, C);
             }
         }
     
         private void move(char from, char to, List<Integer> A, List<Integer> B, List<Integer> C) {
             List<Integer> fromList = getListByName(from, A, B, C);
             List<Integer> toList = getListByName(to, A, B, C);
             System.out.println(fromList.get(0) + " 从 " + from + " 到 " + to);
             toList.add(0, fromList.remove(0));
         }
     
         private List<Integer> getListByName(char name, List<Integer> A, List<Integer> B, List<Integer> C) {
             switch (name) {
                 case 'A':
                     return A;
                 case 'B':
                     return B;
                 default:
                     return C;
             }
         }
     
         public static void main(String[] args) {
             List<Integer> A = new ArrayList<>();
             A.add(1);
             A.add(2);
             List<Integer> B = new ArrayList<>();
             List<Integer> C = new ArrayList<>();
             Solution solution = new Solution();
             solution.hanota(A, B, C);
         }
     }
     ```

   - 栈解法

2. 左程云的新限制

   > 限制不能从最左侧的塔直接移动到最右侧，也不能从最右侧直接移动到最左侧，而是必须经过中间。

   - 递归解法

     ```java
     package top.xijinian.stack;
     
     import java.util.ArrayList;
     import java.util.List;
     
     class Solution {
     
         public void hanota(List<Integer> A, List<Integer> B, List<Integer> C) {
             process(A.size(), 'A', 'B', 'C', A, B, C);
         }
     
         private void process(int n, char from, char buff, char to, List<Integer> A, List<Integer> B, List<Integer> C) {
             if (n == 1) {
                 move(from, buff, A, B, C);
                 move(buff, to, A, B, C);
             } else {
                 process(n - 1, from, buff, to, A, B, C);
                 move(from, buff, A, B, C);
                 process(n - 1, to, buff, from, A, B, C);
                 move(buff, to, A, B, C);
                 process(n - 1, from, buff, to, A, B, C);
             }
         }
     
         private void move(char from, char to, List<Integer> A, List<Integer> B, List<Integer> C) {
             List<Integer> fromList = getListByName(from, A, B, C);
             List<Integer> toList = getListByName(to, A, B, C);
             System.out.println(fromList.get(0) + " 从 " + from + " 到 " + to);
             toList.add(0, fromList.remove(0));
         }
     
         private List<Integer> getListByName(char name, List<Integer> A, List<Integer> B, List<Integer> C) {
             switch (name) {
                 case 'A':
                     return A;
                 case 'B':
                     return B;
                 default:
                     return C;
             }
         }
     
         public static void main(String[] args) {
             List<Integer> A = new ArrayList<>();
             A.add(1);
             A.add(2);
             List<Integer> B = new ArrayList<>();
             List<Integer> C = new ArrayList<>();
             Solution solution = new Solution();
             solution.hanota(A, B, C);
         }
     }
     ```

   - 栈解法

