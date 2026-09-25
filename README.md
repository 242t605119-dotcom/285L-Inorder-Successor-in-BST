# LeetCode 285 - Inorder Successor in BST

## Problem Statement

Given the root of a Binary Search Tree (BST) and a node `p` in the tree, find the **inorder successor** of node `p`.

The inorder successor is the node with the smallest value that is greater than `p.val`.

If the successor does not exist, return `None`.

---

## Example

```text
Input:

       2
      / \
     1   3

p = 1

Output:
2
```

### Explanation

The inorder traversal of the tree is:

```text
[1, 2, 3]
```

The node immediately after `1` is `2`.

Therefore, the inorder successor is `2`.

---

## Approach

Because the tree is a **Binary Search Tree**, we can use its ordering property.

For every node:

```text
Left subtree  <  Root  <  Right subtree
```

We start from the root and compare its value with `p.val`.

### Case 1: `root.val > p.val`

The current root can be a possible successor.

We store it as `successor` and move to the left subtree to find a smaller valid successor.

### Case 2: `root.val <= p.val`

The current root cannot be the successor because its value is not greater than `p.val`.

So we move to the right subtree.

We continue until the root becomes `None`.

---

## Algorithm

1. Set `successor = None`.
2. Start from the root.
3. While the current node exists:

   * If `root.val > p.val`:

     * Store the current node as `successor`.
     * Move to the left subtree.
   * Otherwise:

     * Move to the right subtree.
4. Return `successor`.

---

## Example Walkthrough

Consider:

```text
        5
       / \
      3   6
     / \
    2   4
   /
  1
```

Suppose:

```text
p = 3
```

### Step 1

Current node:

```text
5
```

Since:

```text
5 > 3
```

`5` can be a successor.

```text
successor = 5
```

Move left.

### Step 2

Current node:

```text
3
```

Since:

```text
3 <= 3
```

Move right.

### Step 3

Current node:

```text
4
```

Since:

```text
4 > 3
```

Update:

```text
successor = 4
```

Move left.

There is no more node.

Therefore:

```text
Answer = 4
```

---

## Why This Works

When we find a node greater than `p`, it is a possible successor.

However, there might be a smaller node greater than `p` in its left subtree.

So we continue searching left.

If a node is smaller than or equal to `p`, it cannot be the successor, so we search the right subtree.

This uses the BST property to avoid visiting every node.

---

## Time Complexity

At every step, we move down one level of the tree.

**Time Complexity:** `O(h)`

where `h` is the height of the BST.

For a balanced BST:

```text
O(log n)
```

For a skewed BST:

```text
O(n)
```

---

## Space Complexity

The solution uses only a few variables and does not use recursion.

**Space Complexity:** `O(1)`

---

## Key Concept

The main concepts used are:

* Binary Search Tree
* BST ordering property
* Inorder successor
* Tree traversal
* Iterative search

---

## Language

Python

## LeetCode Problem

285 - Inorder Successor in BST

## Author

T. Nandhini
