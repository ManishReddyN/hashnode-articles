---
title: "Day #7: Number of possible decodable messages"
datePublished: Wed Jun 17 2020 15:31:23 GMT+0000 (Coordinated Universal Time)
cuid: ckl0505fi06vil1s1ef9kdf7g
slug: day-7-number-of-possible-decodable-messages
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1613004113956/kLpS7hrmo.jpeg

---


  
  
Hello everyone.
Today is the Day 7 of the #100DaysOfCodeChallenge.
And it's a week!!!!
Received a problem previously asked by Facebook with a hard tag to it.
  

## The Question On Day #6:


Given the mapping a = 1, b = 2, ... z = 26, and an encoded message, count the number of ways it can be decoded.

For example, the message '111' would give 3, since it could be decoded as 'aaa', 'ka', and 'ak'.

You can assume that the messages are decodable. For example, '001' is not allowed.

  

## Algorithm

 - The algorithm is similar to the concept behind fibonacci series. For every increase in the value of n is fibonacci we added it to the n-1 sum.
 - Similarly, for every increase in the length of the message, we add a particular value to the number of possible ways, based on certain conditions.
 - Points to check:
	 - a 1-digit number is considered a message only if it is greater than 0, because a is represented by 1 according to the question.
	 - a 2-digit number is considered a message only if it has 2 in the ten's place and digit<7 in the one's place or 1 in ten's place and any digit in one's place.

## **Python Code**

%[https://gist.github.com/nmreddy1911/b68ce4c953a8ca458e70e18b04fce539]

**Output**
    Number Of Ways: 3
# Visualiser
You can look into the visualiser to understand the BTS of the logic [here](http://pythontutor.com/visualize.html#code=message%20%3D%20%221212121%22%0Al%20%3D%20len%28message%29%0Aa%20%3D%201%0Ab%20%3D%201%0Ac%20%3D%200%0Afor%20i%20in%20range%282,%20l%2B1%29%3A%0A%20%20%20%20m1%3Dmessage%5Bi-1%5D%0A%20%20%20%20m2%3Dmessage%5Bi-2%5D%0A%20%20%20%20if%20i%20!%3D%202%3A%0A%20%20%20%20%20%20%20%20a%20%3D%20b%0A%20%20%20%20%20%20%20%20b%20%3D%20c%0A%20%20%20%20%20%20%20%20c%20%3D%200%0A%20%20%20%20if%20m1%20!%3D%20'0'%3A%0A%20%20%20%20%20%20%20%20c%20%3D%20b%0A%20%20%20%20if%20%28m2%20%3D%3D%20'1'%20or%20m2%20%3D%3D%20'2'%29%20and%20m1%20%3C%20'7'%3A%0A%20%20%20%20%20%20%20%20c%20%2B%3D%20a%0Aprint%28%22Number%20Of%20Ways%3A%22,%20c%29&cumulative=false&curInstr=46&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false).

Feel free to reach out for any query clearance.

**Thanks and cheers:)**

