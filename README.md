# Maximum-level-sum-of-a-binary-in-java

Here’s a **clear and interview-ready explanation + solution** for
**LeetCode 1161 – Maximum Level Sum of a Binary Tree**.

---

## 🔍 Problem Understanding (Simple Words)

* You are given a **binary tree**
* **Level numbering starts from 1**

  * Root → Level 1
  * Root’s children → Level 2
  * And so on…
* For **each level**, calculate the **sum of node values**
* Return the **smallest level number** that has the **maximum sum**

---

## 💡 Best Approach: **Level Order Traversal (BFS)**

Why BFS?

* BFS naturally processes the tree **level by level**
* Easy to calculate sum for each level

---

## 🧠 Algorithm (Step-by-Step)

1. Use a **Queue** for BFS
2. Start with `level = 1`
3. For each level:

   * Calculate sum of nodes
   * Compare with `maxSum`
4. If current level sum > `maxSum`:

   * Update `maxSum`
   * Store the level number
5. Return the stored level

---

## ✅ Java Solution (Recommended for LeetCode)

```java
import java.util.*;

class Solution {
    public int maxLevelSum(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);

        int level = 1;
        int maxLevel = 1;
        int maxSum = Integer.MIN_VALUE;

        while (!queue.isEmpty()) {
            int size = queue.size();
            int sum = 0;

            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                sum += node.val;

                if (node.left != null) queue.add(node.left);
                if (node.right != null) queue.add(node.right);
            }

            if (sum > maxSum) {
                maxSum = sum;
                maxLevel = level;
            }

            level++;
        }

        return maxLevel;
    }
}
```

---

## ⏱ Time & Space Complexity

| Complexity | Value                           |
| ---------- | ------------------------------- |
| **Time**   | `O(n)` (each node visited once) |
| **Space**  | `O(n)` (queue in worst case)    |

---

## 📌 Example Walkthrough

### Input

```
root = [1,7,0,7,-8,null,null]
```

### Level Sums

```
Level 1 → 1
Level 2 → 7 + 0 = 7  ✅
Level 3 → 7 + (-8) = -1
```

### Output

```
2
```

---

## 🧪 Edge Cases Covered

✔ Tree with negative values
✔ Single node tree
✔ Multiple levels having same sum (returns smallest level)

---


