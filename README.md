
# Series and Summations

### Learning objectives

* Understand how to represent a mathematical series
* Understand how indices are represented
* Understand how to represent a summation in sigma notation

### Introduction

One of the nice things about data science, is that it allows us to explore the symmetry between mathematics and coding.  We saw this with translating equations into functions.  For example, we have now seen different ways of how to translate something like this: $y = 1.3x + 20$, into code like this:

```python
def y(x):
    return 1.3*x + 20    
```

We'll keep that going in this section.

### Sequences

In Python, you are familiar with a list as looking like the following.


```python
my_list = [1, 6, 11, 16, 21]
```

Here we are just listing the literal list of numbers. But we can also express this more compactly in code:


```python
ending_i = 4
i = 0

terms = []
for i in range(i, ending_i + 1):
    terms.append(5*(i) + 1)
terms
```




    [1, 6, 11, 16, 21]



Notice, that by expressing the list of numbers more compactly we make a point about the numbers that we did not make previously.  These numbers form a pattern.  If you initialize an index at zero and increase it until it reaches four, the numbers equal $5*i + 1$ for each index, 0 through 4. 

Now in mathematics we can express `my_list` as the following: (1, 6, 11, 16, 21).  In math, this is called a sequence. Sometimes you will see parentheses used as in above, and other times you will see brackets used to describe a sequence like {1, 6, 11, 16, 21}.  A sequence is just an ordered list of numbers.  So just as a list in Python is an ordered list of elements, our sequence is the same thing where each element is a number.  To describe the components of a sequence, we can use the word **element**, or we can also use the word **term**.  So in our sequence above, 1 is a term, as is 6 and 21.

We can express the same sequence above as the following:

$(x_i)^4_{i=0}$ where $x_i =5*i + 1$

Here we are describing a sequence of numbers, $x_i$ from the indices of 0 to 4, where $x_i$ equals $5*i + 1$.  So just like our code above.  In describing a sequence, the initial index is placed at the bottom, the stopping point at the top.  And the common term for the sequence is also described.  Here that term is a function of the value of $i$.  

It doesn't have to be.  For example, here is another sequence:

$(x_i)^5_{i=1}$ where $x_i =5$

This is a sequence listing all of the elements, and it looks like the following: $(5, 5, 5, 5, 5)$.  So here we describe the starting point at $i = 1$ and the ending point at $ i = 5$.  For every element in the sequence, $x_i$, the value is 5.  So hopefully you can see that both math and code have similar ways to express the pattern in a sequence.

### A mathematical series

A series in mathematics is just the sum of the terms of a sequence.  In other words, the series of the sequence above  $(x_i)^4_{i=0}$ where $x_i = 5*i + 1 $ is equal to $ 1 + 6 + 11 + 16 + 21 = 55$.  Let's see how we would write something like this using Python.  Here are the terms that we previously generated.


```python
# first get the numbers 1 - 10
num_range = list(range(1, 25, 5))
```


```python
num_range
```




    [1, 6, 11, 16, 21]



Now we add up those terms.


```python
total = 0
for i in num_range:
    total += i
total
```




    55



We can also use Python's built in sum function to add up the numbers zero through twenty-five.


```python
num_range
sum(num_range)
```




    55



### Adding like a mathematician

We have just seen different ways for adding a sequence of numbers in code.  Now we can see how to express a summation of numbers in mathematics using sigma notation.  This is sigma notation for adding up the numbers from one to ten, $1 + 2 + 3+ 4+ 5+ 6+ 7 + 8 + 9+ 10$.

$$\sum_{i=1}^{10} i$$

Ok, so let's break this down. The greek letter $\sum$, means that we are about to add up a set of numbers, one after the other.  Whatever is at the bottom of the sigma indicates our starting point, just like with sequences. So, at the bottom of the $\sum$, we see $i = 1 $.  This means we will be initializing $i$ to equal 1.  The number at the top still indicates where we will be stopping, with $i = 10 $.  Now, what comes after the $\sum$ indicates what we are adding.  Here, we are adding $i$, where $i$ is the numbers one through ten.


```python
total = 0
for i in range(1, 11):
    total += i
total
```




    55



Ok, now let's try another of these.  What does adding up the numbers one through five look like in sigma notation?  Well, we know we start at one and end at five.  Then we add each of those numbers, i.  Let's see how this looks with use of sigma notation.

$$\sum_{i=1}^{5} i$$

Ok, not too bad.  The above is the equivalent of $ 1 + 2 + 3 + 4 + 5 = 15 $.

For $(x_i)^5_{i=0}$ with $x_i = i$,  $y = x_i + x_{i + 1} ... x_5 $

Ok, so now that we have discussed adding numbers one after the other, let's talk about how to describe adding any terms in a sequence. This is one way to describe a sum of a sequence:  

$(x_i)^5_{i=0}$ where $x_i = 5*i$

We can read that as, for an element in the series with i starting at 0 and going to 5, with each element equal to $5 * i$, add up all of those elements of the series and set it equal to $y$.  Another way of saying this is, add the numbers (0, 5, 10, 15, 20, 25) together.  Here is that same sequence with summation notation.

$$\sum_{i=1}^{5} 5*i$$

So just like in code, by using sigma notation we can express the summation more succinctly.  And in doing so, we can get more to the core of what we are trying to express.

### Summary

In this section, we saw the similarity between abstractions in mathematics and in coding.  We saw that a sequence is an ordered list of elements or terms.  And how we can describe a sequence by indicating the initial value, the stopping point and the general case, as in: 

$(x_i)^5_{i=0}$ where $x_i = 5*i $

A statement like that means start where $i = 0 $ and end where $i = 5$.  The elements in the series are $5 * i$, or $(0, 5, 10, 15, 20, 25)$.

We also saw how to add the terms in a sequence using the sigma notation as in: 

$$\sum_{i=1}^{5} 5*i$$ which translates to $0 + 5 + 10 + 15 + 20 + 25 $.  Going forward we will use sigma notation to explain concepts in math and data science.
