---
title: "Day #5: Functional Programming with Python."
datePublished: Mon Jun 15 2020 14:16:53 GMT+0000 (Coordinated Universal Time)
cuid: ckl050ez506vjl1s11e3zc29j
slug: day-5-functional-programming-with-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1613004126528/J1NHXf9nJ.jpeg

---

Hey. Hope you have been enjoying the series so far.
Today is the Day 5 of the #100DaysOfCodeChallenge. Received a problem previously asked by [Jane Street](https://www.janestreet.com/) (refer the hyperlink for the company details) with a medium tag to it. This question is a true puzzle and can be solved in a minute if your functional programming understanding is strong.

You may get confused with the question, just like the way I did. I will try my best in putting the solution in the simplest way possible. You can always reach out to me if you need help.

  

## The Question On Day #5:

`cons(a, b)` constructs a pair, and `car(pair)` and `cdr(pair)` returns the first and last element of that pair. For example, `car(cons(3, 4))` returns `3`, and `cdr(cons(3, 4))` returns `4`.

Given this implementation of cons:

```
def cons(a, b):
    def pair(f):
        return f(a, b)
    return pair
```

Implement `car` and `cdr`.

## Explanation
The question is a bit confusing but let us try to understand it clearly.

 - `cons` is a function which takes two inputs (consider integers). It returns a value which is an function defined inside itself, i.e. `pair`.
 - `pair` is a function which takes a function `f` as input and returns the return value of its input function, i.e. the return value of the function `f` is returned by `pair`.
 - Now `f` is a function which will return a value.
 - **`f` is the key to all our solution.**

  

## Algorithm

 - The end value obtained on calling the function cons is a function pointer pointing to the `pair` function.
 - The required implementation goes as follows:

## **Python Code**

%[https://gist.github.com/nmreddy1911/a6b251f81e8c167055d466f606a8c618]

**Output**
    3
    4
## **Explanation**

When **`car(cons(3,4))`** is called, 

 1. cons(3,4) is invoked in the first place.
 2. cons returns the function pair function.
 3. The parameter passed to the `car` function is the `pair` function.
 4. `car` function returns the value returned by calling the `pair` function.
 5. `pair` function takes a function as input, so we pass the `left` function to it.
 6. `pair` function returns the value obtained by passing a, b to a a function `f`. So, our `left` is the function `f`, which takes a, b as input and returns a as output to the `pair` function.
 7.  Now the same a is returned by `pair` function to the `car` function, which will again return the same value of a.
 8. Now a is returned at the end and printed.
 9. Same goes with the function `cdr`.


#The Python visualiser is very much needed to understand this logic more clearly, please refer it [here](https://cscircles.cemc.uwaterloo.ca/visualize#code=%0Adef+cons%28a,+b%29:%0A++++def+pair%28f%29:%0A++++++++return+f%28a,+b%29%0A++++return+pair%0Adef+car%28pair%29:%0A++++def+left%28a,b%29:%0A++++++++return+a%0A++++return+pair%28left%29%0Adef+cdr%28pair%29:%0A++++def+right%28a,b%29:%0A++++++++return+b%0A++++return+pair%28right%29%0Aprint%28car%28cons%283,4%29%29%29%0Aprint%28cdr%28cons%283,4%29%29%29&mode=display&raw_input=&curInstr=33).

I hope you were able to understand this problem.
Feel free to reach out for any query clearance.

**Thanks and cheers:)**

