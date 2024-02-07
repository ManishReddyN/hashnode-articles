---
title: "Day #6: XOR Doubly Linked List"
datePublished: Tue Jun 16 2020 12:49:39 GMT+0000 (Coordinated Universal Time)
cuid: ckl050aeq06rnm2s1gl8p24jn
slug: day-6-xor-doubly-linked-list
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1613004120659/izSh4tt1v.jpeg

---

Hello.
Today is the Day 6 of the #100DaysOfCodeChallenge. Received a problem previously asked by Google with a hard tag to it.
  

## The Question On Day #6:


An XOR linked list is a more memory efficient doubly linked list. Instead of each node holding `next` and `prev` fields, it holds a field named `both`, which is an XOR of the next node and the previous node. Implement an XOR linked list; it has an `add(element)` which adds the element to the end, and a `get(index)` which returns the node at index.

Doing it on C++, since pointer implementation on Python is messy and not efficient.

  

## Algorithm
- The main logic behind the question is to understand the properties of XOR.
- Refer [wiki](https://en.wikipedia.org/wiki/XOR_linked_list).


## **C++ Code**

%[https://gist.github.com/nmreddy1911/28584d0667a1f920bcb580970ab3b25b]

**Output**

    Nodes: 
    40 30 20 10 
## **Explanation**

Not getting much into the details of the logic, the wikipedia reference speaks it all.

You can look into the visualiser to understand the BTS of the logic [here](http://www.pythontutor.com/cpp.html#code=%23include%20%3Cbits/stdc%2B%2B.h%3E%0A%23include%20%3Cinttypes.h%3E%0Ausing%20namespace%20std%3B%0Aclass%20Node%0A%7B%0Apublic%3A%0A%20%20%20%20int%20val%3B%0A%20%20%20%20Node%20*ptr%3B%0A%7D%3B%0A%0ANode%20*XOR%28Node%20*a,%20Node%20*b%29%0A%7B%0A%20%20%20%20return%20%28Node%20*%29%28%28uintptr_t%29%28a%29%20%5E%20%28uintptr_t%29%28b%29%29%3B%0A%7D%0A%0Avoid%20insert%28Node%20**head_ref,%20int%20val%29%0A%7B%0A%0A%20%20%20%20Node%20*new_node%20%3D%20new%20Node%28%29%3B%0A%20%20%20%20new_node-%3Eval%20%3D%20val%3B%0A%20%20%20%20new_node-%3Eptr%20%3D%20*head_ref%3B%0A%20%20%20%20if%20%28*head_ref%20!%3D%20NULL%29%0A%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%28*head_ref%29-%3Eptr%20%3D%20XOR%28new_node,%20%28*head_ref%29-%3Eptr%29%3B%0A%20%20%20%20%7D%0A%20%20%20%20*head_ref%20%3D%20new_node%3B%0A%7D%0Avoid%20printList%28Node%20*head%29%0A%7B%0A%20%20%20%20Node%20*curr%20%3D%20head%3B%0A%20%20%20%20Node%20*prev%20%3D%20NULL%3B%0A%20%20%20%20Node%20*next%3B%0A%20%20%20%20cout%3C%3C%22Nodes%3A/n%22%3B%0A%20%20%20%20while%20%28curr%20!%3D%20NULL%29%0A%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20cout%20%3C%3C%20curr-%3Eval%20%3C%3C%20%22%20%22%3B%0A%20%20%20%20%20%20%20%20next%20%3D%20XOR%28prev,%20curr-%3Eptr%29%3B%0A%20%20%20%20%20%20%20%20prev%20%3D%20curr%3B%0A%20%20%20%20%20%20%20%20curr%20%3D%20next%3B%0A%20%20%20%20%7D%0A%20%20%20%20cout%20%3C%3C%20%22%5Cn%22%3B%0A%7D%0Aint%20main%28%29%0A%7B%0A%20%20%20%20Node%20*head%20%3D%20NULL%3B%0A%20%20%20%20insert%28%26head,%2010%29%3B%0A%20%20%20%20insert%28%26head,%2020%29%3B%0A%20%20%20%20insert%28%26head,%2030%29%3B%0A%20%20%20%20insert%28%26head,%2040%29%3B%0A%20%20%20%20printList%28head%29%3B%0A%20%20%20%20return%20%280%29%3B%0A%7D&curInstr=42&mode=display&origin=opt-frontend.js&py=cpp&rawInputLstJSON=%5B%5D).

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=%23include%20%3Cbits/stdc%2B%2B.h%3E%0A%23include%20%3Cinttypes.h%3E%0Ausing%20namespace%20std%3B%0Aclass%20Node%0A%7B%0Apublic%3A%0A%20%20%20%20int%20val%3B%0A%20%20%20%20Node%20*ptr%3B%0A%7D%3B%0A%0ANode%20*XOR%28Node%20*a,%20Node%20*b%29%0A%7B%0A%20%20%20%20return%20%28Node%20*%29%28%28uintptr_t%29%28a%29%20%5E%20%28uintptr_t%29%28b%29%29%3B%0A%7D%0A%0Avoid%20insert%28Node%20**head_ref,%20int%20val%29%0A%7B%0A%0A%20%20%20%20Node%20*new_node%20%3D%20new%20Node%28%29%3B%0A%20%20%20%20new_node-%3Eval%20%3D%20val%3B%0A%20%20%20%20new_node-%3Eptr%20%3D%20*head_ref%3B%0A%20%20%20%20if%20%28*head_ref%20!%3D%20NULL%29%0A%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%28*head_ref%29-%3Eptr%20%3D%20XOR%28new_node,%20%28*head_ref%29-%3Eptr%29%3B%0A%20%20%20%20%7D%0A%20%20%20%20*head_ref%20%3D%20new_node%3B%0A%7D%0Avoid%20printList%28Node%20*head%29%0A%7B%0A%20%20%20%20Node%20*curr%20%3D%20head%3B%0A%20%20%20%20Node%20*prev%20%3D%20NULL%3B%0A%20%20%20%20Node%20*next%3B%0A%20%20%20%20cout%3C%3C%22Nodes%3A/n%22%3B%0A%20%20%20%20while%20%28curr%20!%3D%20NULL%29%0A%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20cout%20%3C%3C%20curr-%3Eval%20%3C%3C%20%22%20%22%3B%0A%20%20%20%20%20%20%20%20next%20%3D%20XOR%28prev,%20curr-%3Eptr%29%3B%0A%20%20%20%20%20%20%20%20prev%20%3D%20curr%3B%0A%20%20%20%20%20%20%20%20curr%20%3D%20next%3B%0A%20%20%20%20%7D%0A%20%20%20%20cout%20%3C%3C%20%22%5Cn%22%3B%0A%7D%0Aint%20main%28%29%0A%7B%0A%20%20%20%20Node%20*head%20%3D%20NULL%3B%0A%20%20%20%20insert%28%26head,%2010%29%3B%0A%20%20%20%20insert%28%26head,%2020%29%3B%0A%20%20%20%20insert%28%26head,%2030%29%3B%0A%20%20%20%20insert%28%26head,%2040%29%3B%0A%20%20%20%20printList%28head%29%3B%0A%20%20%20%20return%20%280%29%3B%0A%7D&codeDivHeight=400&codeDivWidth=350&curInstr=42&origin=opt-frontend.js&py=cpp&rawInputLstJSON=%5B%5D"> </iframe>

Feel free to reach out for any query clearance.

**Thanks and cheers:)**

