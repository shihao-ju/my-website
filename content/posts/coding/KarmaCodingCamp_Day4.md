---
title: 'DSA - Day 4 Linked List II'
date: 2025-02-14
tags: [Programming]
draft: false
hideInList: false
feature: 
isTop: false
---

# KarmaCoder Day 4 LC24/19/02.07/142

1️⃣ Swap nodes in pairs
Link: [lc24](https://leetcode.com/problems/swap-nodes-in-pairs/)

1. Draw the next directions can be straightforward.

2️⃣ Remove Nth node from end of list
1. Two pointers, one moves first by n steps, then both move until the first one moves to the last node, then delete the node the second pointer is located at.

3️⃣ Intersection of two linked list
1. Find the length difference of two lists and move the longer list pointer points to the same length position.
2. Move pointers on both lists together until they intersect.

4️⃣ Linked List Cyle II
1. Fast and slow two pointers with step size of 2 and 1, respectively, the distance between the head and the cycle begin is equal to the distance between the intersection and the cycle begin.
2. code is difficult, the key is to find out the above pattern.