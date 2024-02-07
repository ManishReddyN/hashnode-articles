---
title: "Day #1: My Start With 100 Days Of Code"
datePublished: Wed Jun 10 2020 17:32:13 GMT+0000 (Coordinated Universal Time)
cuid: ckl052p7k06vvl1s10x3qc91v
slug: day-1-my-start-with-100-days-of-code
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1613004233098/6lEQAkPyb.jpeg

---



Hi! I'm Manish. I was wondering what to do in this COVID-19 pandemic, to stay a bit productive and then the phrase **100 Days Of Code** striked me while surfing the internet and I decided to take up the challenge. 

To begin with that, I have enolled for the email subscription by [**Daily Coding Problems**](https://www.dailycodingproblem.com/). The team at DCP sends us an email with one coding problem a day and I believed that it would be the right thing for the challenge. To add to that, I have decided to share my experience on solving the question too and start writing on **dev**.

The Question On Day #1:

    Given a list of numbers and a number `k`, return whether any two numbers from the list add up to `k`.
    
    For example, given `[10, 15, 3, 7]` and `k` of `17`, return true since `10 + 7` is `17`.

## My First Approach

 - Input the given numbers into a list and and the sum to check in a variable.
 - Traverse through the list and for each element at index *i*, check if there exists a complementary number starting from the index *i* in the list.
 - If there exists atleast one such number print "pair exists" and exit the loop by marking a flag.
 - After the cursor exits the loop adn if the flag is still unmarked, print "pair doesn't exist".

**Python Code**

    l=[10,15,3,7]
    k=17
    flag=0
    for i in range(len(l)-1):
	    if (k-l[i]) in l[i+1:]:
		    #slicing to prevent additional checks
		    print("pair exists")
		    flag=1
		    break
	if flag==0:
		print("pair doesn't exist")

**Points To Note:**

 - The check for the complementary number is only done for the sliced list from i+1 to len(l), since the previous number pairs are already checked in the iterations before.
 - The last element of the list is thus skipped from being checked for a complementary number.

**Time Complexity Of The Above Solution**

> **The traversal through the list takes a time of O(n) where n is the length of list. For each element, there is an another check with *in* operator which again takes a time complexity of O(n-i) for a list in python [ref](https://wiki.python.org/moin/TimeComplexity).** 

***The total time complexity for the solution will result in a time complexity of O(n^2).***

## Better Approach
An approach better to the above solution is to convert the list into a set first, does making the *in operator* efficient to use.

The time complexity of using the in operator on a set is O(1) on average and O(n) in the worst case.

**Python Code**

    l=[10,15,3,7]
    k=17
    s=set(l) #converting list l into a set and storing it in s
    flag=0
    for i in s:
	    if (k-i) in s:
		    print("pair exists")
		    flag=1
		    break
	if flag==0:
		print("pair doesn't exist")
		
**Time Complexity Of The Above Solution**

>**The conversion from list to a set takes a time of O(n) where n is the length of list. Hence, the total time complexity for the above solution is O(n)+O(nx1)**
>*[O(nx1) on average and O(nxn) in the worst case for the loop and condition check using in operator on the set s].*

**Thus the total time complexity on average results to O(n) and O(n^2) in the worst case scenario.**



> *This question helped me in understanding the time complexities of individual data structure operations in python. I would love to hear from my fellow developers and take suggestions on improving the above logic. I am a pretty newbie to solving such questions, please consider it. I also request you to drop suggestions to improve my article readability or understanding.*

***Thanks and cheers:)***


