---
layout: "post"
title: "Binary Trees"
date:   2020-05-12 3:33:31 -0400
categories: "Data Structures"
---
# Binary Trees

Definition: Binary trees refer to the structure of at most children nodes.

Ordered binary trees include **Binary search trees (BST)** and **Binary Heaps**.

- Binary search trees (BST)
    - Left child smaller than parent
    - Right child larger than parent
    - Left subtree smaller than root
    - Right subtree larger than root
- Binary Heaps
    - Max Binary store maximum value at the root
    - Min Binary store minimum value at the root

## Sample questions

1. Find the min/max values of this binary search tree

    ![Binary tree](https://llyu0966.github.io/mypic/DS/BST1.png)

    <details><summary>CLICK ME</summary>
    <p>

    ![Binary tree](https://llyu0966.github.io/mypic/DS/BST1A.png)

    </p>
    </details>

2. Represent this binary search tree as an array, using inorder traversal.

   ![Binary tree](https://llyu0966.github.io/mypic/DS/BST2.png)

    <details><summary>CLICK ME</summary>
    <p>

    A B C D E F G H I J K

    </p>
    </details>

3. Is the following a valid heap? If yes, represent it as an array.

    ![Binary tree](https://llyu0966.github.io/mypic/DS/BH.png)

    <details><summary>CLICK ME</summary>
    <p>

    Yes. [100, 90, 80, 30, 60, 50, 70, 20, 10, 40, 55, 45, 5]

    </p>
    </details>
