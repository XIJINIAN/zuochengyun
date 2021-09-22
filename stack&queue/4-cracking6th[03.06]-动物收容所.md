> [题目链接](https://leetcode-cn.com/problems/animal-shelter-lcci/)

我的解答：

```java
package top.xijinian.stack;

import java.util.LinkedList;
import java.util.Queue;
import java.util.concurrent.atomic.AtomicInteger;

class AnimalShelf {

    private final Queue<int[]> dogQueue;
    private final Queue<int[]> catQueue;
    private final AtomicInteger currentTime;

    public AnimalShelf() {
        this.dogQueue = new LinkedList<>();
        this.catQueue = new LinkedList<>();
        currentTime = new AtomicInteger();
    }
    
    public void enqueue(int[] animal) {
        int[] animalTime = new int[3];
        animalTime[0] = animal[0];
        animalTime[1] = animal[1];
        animalTime[2] = (currentTime.get());
        currentTime.incrementAndGet();
        if (animal[1] == 1) {
            dogQueue.offer(animalTime);
        } else if (animal[1] == 0) {
            catQueue.offer(animalTime);
        }
    }
    
    public int[] dequeueAny() {
        if (catQueue.isEmpty() && dogQueue.isEmpty()) {
            return new int[]{-1, -1};
        }
        if (catQueue.isEmpty()) {
            return dequeueDog();
        }
        if (dogQueue.isEmpty()) {
            return dequeueCat();
        }
        int[] animalTime;
        if (catQueue.peek()[2] < dogQueue.peek()[2]) {
            animalTime = catQueue.poll();
        } else {
            animalTime = dogQueue.poll();
        }
        return new int[]{animalTime[0], animalTime[1]};
    }
    
    public int[] dequeueDog() {
        if (dogQueue.isEmpty()) {
            return new int[]{-1, -1};
        }
        int[] animalTime = dogQueue.poll();
        return new int[]{animalTime[0], animalTime[1]};
    }
    
    public int[] dequeueCat() {
        if (catQueue.isEmpty()) {
            return new int[]{-1, -1};
        }
        int[] animalTime = catQueue.poll();
        return new int[]{animalTime[0], animalTime[1]};
    }
}
```
