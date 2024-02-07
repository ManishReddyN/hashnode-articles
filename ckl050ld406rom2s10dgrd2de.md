---
title: "Day #4: Finding the smallest positive missing integer from an unordered list using Python."
datePublished: Sun Jun 14 2020 13:50:07 GMT+0000 (Coordinated Universal Time)
cuid: ckl050ld406rom2s10dgrd2de
slug: day-4-finding-the-smallest-positive-missing-integer-from-an-unordered-list-using-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1613004134333/u41MjT5jf.jpeg

---

Hey, today is the Day 4 of the #100DaysOfCodeChallenge. Received a problem previously asked by Stripe with a hard tag to it.

  

## The Question On Day #4:
Given an array of integers, find the first missing positive integer in **linear time and constant space**. In other words, find the lowest positive integer that does not exist in the array. The array can contain duplicates and negative numbers as well.

For example, the input `[3, 4, -1, 1]` should give `2`. The input `[1, 2, 0]` should give `3`.


  

## Algorithm

 - Input the given array into a list
 - Filter out all the non-positive numbers from the list.
 - Note that after filtering the non positive elements, the maximum number of positive numbers in the array at the best case can be n, i.e. all the numbers from 1 to n, where n is the length of the positive numbers list.
 - Now we can mark all the numbers greater than n as not required, because the smallest positive number will definitely be in the range of [1,n] or it will be n+1 if all the numbers from 1 to n are in the array.
 - Coming to the core logic, consider an element `v` in the array which is not flag, i.e. it is in the range of [1,n]. Now mark the value at index `v` negative. If the value v is negative, consider its absolute value.
 - Why does this work?
	 - When a element is made negative, it means that the index `i` where it is located, which is a positive integer, exists in the list.
	 - If the positive integer doesn't exist in the list, that particular index remains positive, so when the array is traversed, we can exit at the first positive number encountered and output that index since that is the missing number. 
	 - If the entire array is negative, it means that all the numbers from 1 to n exist in the array, hence the smallest positive number missing is (n+1).
	 
	 
 - **Point to note:** Since index start from 0, it should be kept in mind while negating the numbers and returning the result.

  

**Python Code**  

%[https://gist.github.com/nmreddy1911/a829984ff07ccd98a5882f19f493c4ba]

**Output**

    7



Feel free to reach out for any query clearance.
**Thanks and cheers:)**

