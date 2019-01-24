---
title: Binary Search Summary
description: Summary of binary search problems in Leetcode.
categories:
 - Leetcode
tags:
 - binary
---
# Binary Search Summary

## Binary Search Template
1. Find First Position of Element is Sorted Array

2. Find Last Position of Element in Sorted Array

## Binary Search to Find a Specific Position
1. First Bad Version
2. Find K Closest Elements
3. Search in a Big Sorted Array (Exponential Backoff)
4. Find minimum in a rotated Array
OOOO | X(minimum number)XXX
corner case: sorted array
>= first or > last number?
> last, because if >= first, then you cannot find position to seperate sorted array.
True: first position <= last number
Wrong: first position <= or < first number
Follow up: What if the sorted rotated array has repeated number? What is the worst case? Cannot solve in O(n)
[1,1,1,...,0,1,1,1]
5. Peak Index in a Mountain Array
Follow up: Trinary Search

## Half & Half
1. Search in a Roatated Array
only use binary search once


