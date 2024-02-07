---
title: "Day #2: Product of all the elements of the array, except self."
datePublished: Fri Jun 12 2020 03:34:21 GMT+0000 (Coordinated Universal Time)
cuid: ckl052kxa06rsm2s18crjevo3
slug: day-2-product-of-all-the-elements-of-the-array-except-self-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1613004227339/DLesJ_YPv.jpeg

---


  
  
Hello, today is the Day 2 of the #100DaysOfCodeChallenge. Received a problem previously asked by Uber with a hard tag to it. Tried my best in solving it, looking for better solutions if possible. 

> But before that, an addition to yesterday's solution. The reason why in operator takes a time of O(1) on average for sets is: in Python, the sets are stored as hash tables. So when we need to check for the membership of a key, python calculates it's hash value which is the index and thus gives the answer if it exists or not. In most cases, the hashes are unique, and the worst case occurs only when the hash value is common for all the elements in the set and that's when all the elements are to be checked leading to a time complexity of O(n).

  

The Question On Day #2:  

    Given an array of integers, return a new array such that each element at  
    index `i` of the new array is the product of all the numbers in the  
    original array except the one at `i`.

    For example, if our input was `[1, 2, 3, 4, 5]`, the expected output would  
    be `[120, 60, 40, 30, 24]`. If our input was `[3, 2, 1]`, the expected  
    output would be `[2, 3, 6]`. 

**Condition: Division is not allowed.**  
  

## Naive Approach  
  

 - Input the given *n* numbers into a list.  
 - Traverse through the list n times and calculate the product each time, by skipping the number at that index.  
 - Store the product in a new answer list.  
  

**Python Code**  

   ```py
     l=[1,2,3,4,5]  
     a=[0]*len(l)  
     for i in range(len(l)):  
	    p=1  
	    for j in range(len(l)):
		    if(i==j):
			    continue
		    else:
			    p*=l[j]  
    	    a[i]=p  
     print(a)  
```

**Time Complexity Of The Above Solution**  
  

>  **The traversal through the list for the outer loop executes at a time of O(n). The inner loop again takes a time of O(n) to traverse through the entire list.**  
  

***The total time complexity for the solution will result in a time complexity of O(n^2).***  
  

## Better Approach  

I wrote a code satisfying the problem statement but found a better solution than mine in terms of time complexity at LeetCode. [ref](https://leetcode.com/articles/product-of-array-except-self/#)  
  

**Algorithm**  
  

 - Input the given *n* numbers into a list.  
 - Consider that each element has a left product and a right produt, which mean product of all the elements to the left of the element and product of all the elements to the right of the element respectively.  
 - Store the left and right products of each element in 2 different lists l and r where l has the left product of an element at the index i in list a and r similarly has the right product.  
 - Now store the product of multiplying l[i[4] and r[i] in r[i] itself, which is the final output list.  
  

**Python Code**  

```py
    a=[1,2,3,4,5]  
    length=len(a)  
    l=[0]*length  
    r=[0]*length  
    
    l[0]=1             #since there is no element to the left of the first element we keep it's left product as 1  
    
    for i in range(1,length):  
	    l[i]=l[i-1]*a[i-1]  
	        
    '''Ex: take i=1 the left product at i=1 is product of all elements  
    to the left of it. Since we have the left product of the   
    previous element already stored in the list l we multiply  
    it with the element at i-1.'''  
    
    r[length-1]=1       #since there is no element to the right of the last element.  

    for i in reversed(range(length-1)): 
	    r[i]=r[i+1]*l[i+1]
	    #same logic as above but in reverrse order

	#calculating the individual product
	for i range(length):
		r[i]*=l[i]
	print(r)
```
**Time Complexity Of The Above Solution**  
  

>**The 3 individual loops need 1 traversal each through the entire list and each loop has only one operation in it.**
  

**Thus the total time complexity of the above program is O(n)**    

***Thanks and cheers:)***

