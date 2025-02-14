---
title: 'DSA - Day 3 Linked List I'
date: 2025-02-13
tags: [Programming]
draft: false
hideInList: false
feature: 
isTop: false
---

# KarmaCoder Day 3 LC203/707/206

1️⃣ Remove Linked List Elements
Link: [lc203](https://leetcode.com/problems/remove-linked-list-elements/description/)

Takeaway:microphone::
1. ListNode construction: value, next
2. Often the process is we find a node, and do some operations on it. Thus, it's most convenient to identify this node at its previous node, and at the same time, store the pointer to its next node.
3. Creating a dummy node ahead of the head node allows us to process the head node as other nodes.

2️⃣ Design linked list
1. When designing a linked list, initialize a dummy head, then add elements one by one.

3️⃣ Reverse linked list
1. Two pointers, one is cur, the other is pre
2. Temporarily save current node's next node because we will change it to the previous node.