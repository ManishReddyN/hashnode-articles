---
title: "Day #3: Serializing and Deserializing a Binary Tree with Python."
datePublished: Sat Jun 13 2020 09:23:32 GMT+0000 (Coordinated Universal Time)
cuid: ckl052gf506rrm2s18p7zc1ns
slug: day-3-serializing-and-deserializing-a-binary-tree-with-python-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1613004221529/elA3C-A1d.jpeg

---


  
  
Hello, today is the Day 3 of the #100DaysOfCodeChallenge. Received a problem previously asked by Google with a medium tag to it. This is also listed in the hard set of problems on LeetCode.

  

## The Question On Day #3:

**Given the root to a binary tree, implement `serialize(root)`, which serializes the tree into a string, and `deserialize(s)`, which deserializes the string back into the tree.
For example, given the following `Node` class**

```
class Node:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```

**The following test should pass:**

```
node = Node('root', Node('left', Node('left.left')), Node('right'))
assert deserialize(serialize(node)).left.left.val == 'left.left'
``` 

  

## Algorithm

 - Create the binary tree using the Node class. 
 - **Serializing:**
	 - To serialize the tree into a string, I considered the null nodes as #.
	 - Starting from root, Depth First Search is used to traverse through the tree. 
	 - If a node exists, its value is appended to the string and the left sub tree is traversed.
	 - This process continues until there are no more children left. Then a '#' is appended to the array and the recursive function is exited.
	 - Then the right sub tree is traversed and the same process is followed.
	 - The final resulting is string is returned.
 - **Deserializing:**
	 - To deserialize a string to form a tree, the first word in the space seperated string is considered as the root.
	 - When a '#' is encountered, it is considered as a empty node and None is returned.
	 - In the remaining cases, a new node with the value as the word is formed and the remaining string is traversed.
	 - This function is called recursively until the end of the string is reached.
  

**Python Code**  

%[https://gist.github.com/nmreddy1911/fd19ddcb1f3c3d9b0e97ae5ea8a508ac]

**Output**

    String after serializing node: root left left.left # # # right # # 
    Assert: True


## Python Visualiser To Understand The Recursion Better
View the visualisation of the above code [here](http://pythontutor.com/visualize.html#code=class%20Node%3A%0A%20%20%20%20def%20__init__%28self,%20val,%20left%3DNone,%20right%3DNone%29%3A%0A%20%20%20%20%20%20%20%20self.val%20%3D%20val%0A%20%20%20%20%20%20%20%20self.left%20%3D%20left%0A%20%20%20%20%20%20%20%20self.right%20%3D%20right%0A%0A%0Anode%20%3D%20Node%28'root',%20Node%28'left',%20Node%28'left.left'%29%29,%20Node%28'right'%29%29%0As%20%3D%20%22%22%0A%0A%23%20serializing%20function%0A%0A%0Adef%20serialize%28node,%20s%3D%22%22%29%3A%0A%20%20%20%20if%28not%20node%29%3A%0A%20%20%20%20%20%20%20%20s%20%2B%3D%20%22%23%20%22%0A%20%20%20%20%20%20%20%20return%20s%0A%20%20%20%20s%20%2B%3D%20%28str%28node.val%29%2B%22%20%22%29%0A%20%20%20%20s%20%3D%20serialize%28node.left,%20s%3Ds%29%0A%20%20%20%20s%20%3D%20serialize%28node.right,%20s%3Ds%29%0A%20%20%20%20return%20s%0A%0A%0A%23%20deserializing%20function%0Ai%20%3D%200%0A%0A%0Adef%20deserialize%28s%29%3A%0A%20%20%20%20global%20i%0A%20%20%20%20if%20s%5Bi%5D%20%3D%3D%20%22%23%22%3A%0A%20%20%20%20%20%20%20%20if%28i%20%3C%20len%28s%29-2%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20i%20%2B%3D%202%0A%20%20%20%20%20%20%20%20return%20None%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20space%20%3D%20s%5Bi%3A%5D.find%28%22%20%22%29%0A%20%20%20%20%20%20%20%20sp%20%3D%20space%2Bi%0A%20%20%20%20%20%20%20%20node%20%3D%20Node%28s%5Bi%3Asp%5D%29%0A%20%20%20%20%20%20%20%20i%20%3D%20sp%2B1%0A%20%20%20%20%20%20%20%20node.left%20%3D%20deserialize%28s%29%0A%20%20%20%20%20%20%20%20node.right%20%3D%20deserialize%28s%29%0A%20%20%20%20%20%20%20%20return%20node%0A%0Aprint%28%22String%20after%20serializing%20node%3A%20%22%2Bserialize%28node%29%29%0Aprint%28%22Assert%3A%22,deserialize%28serialize%28node%29%29.left.left.val%20%3D%3D%20'left.left'%29&cumulative=false&curInstr=0&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false)  to understand the recursion better, step by step.


Please drop your queries in the comments section.

**Thanks and cheers:)**

