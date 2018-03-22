
# Series and Summations

### Introduction

One of the nice things about data science is that it allows us to explore the symmetry between mathematics and coding.  We saw this with translating equations into functions.  For example, we have now seen different ways of how to translate something like this: $y = 1.3x + 20$, into code like this:

```python
def y(x):
    return 1.3*x + 20    
```

In this section we'll see how we can use coding to better understand a mathematical series and summation.

### Learning objectives

* Understand how to represent a mathematical series
* Understand how indices are represented
* Understand how to represent a summation with sigma notation

### Sequences in code

In Python, you are familiar with a list as looking like the following.


```python
my_list = [1, 6, 11, 16, 21]
```

Now looking at the numbers above, you can see that these numbers start at one and increment by five for every number.  So below we generate these numbers with code, and also use code to express how these numbers increment.


```python
initial_i = 0
ending_i = 4

terms = []
for i in range(initial_i, ending_i + 1):
    current_element = 5*(i) + 1
    terms.append(current_element)
terms
```




    [1, 6, 11, 16, 21]



Our code above expresses a pattern in the numbers:  

* initialize a number (our index) at zero
* increase the index until it reaches four
* Each element in the list equals $5*i + 1$, for the index 0 up to and including 4

### Sequences in math

In Python we call this ordered collection of numbers as a list.  In math, an ordered list of numbers is called a sequence.  In math, we express sequences not with [], but as the following: (1, 6, 11, 16, 21) or {1, 6, 11, 16, 21}.  

To describe the components of a sequence, we can use the word **element**, or we can also use the word **term**.  So in our sequence above, 1 is a term, as is 6 and 21.

In math, another way to express the above sequence is as the following:

$(x_i)^4_{i=0}$ where $x_i =5*i + 1$

Read the above line as the following: 

* A sequence of numbers, $x_i$ from the indices of 0 to 4, where $x_i$ equals $5*i + 1$.  
* This gives us {1, 6, 11, 16, 21}

And notice the similarity to our code:


```python
initial_i = 0
ending_i = 4

terms = []
for i in range(initial_i, ending_i + 1):
    current_element = 5*(i) + 1
    terms.append(current_element)
terms
```




    [1, 6, 11, 16, 21]



In describing a sequence in math, the initial index is placed at the bottom, the stopping point at the top.  And the common term for the sequence is also described.

### Different sequences

In our first sequence, the term changed based on the value of $i$.  

$(x_i)^4_{i=0}$ where $x_i =5*i + 1$

But sequences don't have to depend on the value of the index.  For example, here is another sequence:

$(x_i)^5_{i=1}$ where $x_i =5$

Do you see what this sequence would look line: $(5, 5, 5, 5, 5)$.  So here we describe the starting point at $i = 1$ and the ending point at $ i = 5$.  For every element in the sequence, $x_i$, the value is 5.  

And the code would be


```python
initial_i = 0
ending_i = 4

terms = []
for i in range(initial_i, ending_i + 1):
    current_term = 5
    terms.append(current_term)
terms
```




    [5, 5, 5, 5, 5]



### A mathematical series

A series in mathematics is just the sum of the terms of a sequence.  In other words, the series of the sequence above:

$(x_i)^4_{i=0}$  where $ x_i = 5*i + 1  = 1 + 6 + 11 + 16 + 21 = 55$.  

Let's see how we would write something like this using Python.  Here is the sequence that we previously generated.


```python
num_range = list(range(1, 22, 5))
```


```python
num_range
```




    [1, 6, 11, 16, 21]



Now to turn this into a series, we just add up those terms.


```python
total = 0
for i in num_range:
    total += i
total
```




    55



Or we can use Python's built in sum function to add up the numbers zero through twenty-five.


```python
num_range
sum(num_range)
```




    55



### Adding like a mathematician

We have just seen different ways for adding a sequence of numbers in code.  Adding a sequence of numbers is called a summation.  Let's see how to express a summation of numbers in mathematics using sigma notation.  This is sigma notation for adding up the numbers from one to ten, {1 + 2 + 3+ 4+ 5+ 6+ 7 + 8 + 9+ 10}.

$$\sum_{i=1}^{10} i$$

Ok, so let's break down the syntax. The greek letter $\sum$, means that we are about to add up a set of numbers, one after the other.  Whatever is at the bottom of the sigma indicates our starting point, just like with sequences. So, at the bottom of the $\sum$, we see $i = 1 $.  This means we will be initializing $i$ to equal 1.  The number at the top still indicates where we will be stopping, with $i = 10 $.  Now, what comes after the $\sum$ indicates the term that we are adding.  Here, we are adding $i$, where $i$ is the numbers one through ten.


```python
total = 0
for i in range(1, 11):
    total += i
total
```




    55



Let's try another of these.  What does adding up the numbers one through five look like in sigma notation?  Well, we know we start at one and end at five.  Then we add each of those numbers, $i$.  

$$\sum_{i=1}^{5} i$$

Ok, not too bad.  The above is the equivalent of $ 1 + 2 + 3 + 4 + 5 = 15 $.

If we want to be a little more long winded about this, we can express this with our series notation as the following:

For $(x_i)^5_{i=0}$ with $x_i = i$,  $y = x_i + x_{i + 1} ... x_5 $

### Summation of any terms

So far we have discussed adding numbers one after the other.  Now let's use our notation to describe adding any terms in a sequence. This is one way to describe a sum of a sequence:  

$(x_i)^5_{i=0}$ where $x_i = 5*i$,  $y = x_i + x_{i + 1} ... x_5 $

We can read that as, for an element in the series with $i$ starting at 0 and going to 5, and each element equal to $5 * i$, add up all of those elements of the series and set it equal to $y$.  Here is that same sequence with sigma notation.

$$\sum_{i=1}^{5} 5*i$$

So by using sigma notation we can express the a summation more succinctly.  And in doing so, we can get more to the core of what we are trying to express.

### Summary

In this section, we saw the similarity between abstractions in mathematics and in coding.  We saw that a sequence is an ordered list of elements or terms.  And how we can describe a sequence by indicating the initial value, the stopping point and the general case, as in: 

$(x_i)^5_{i=0}$ where $x_i = 5*i $

A statement like that means start where $i = 0 $ and end where $i = 5$.  The elements in the series are $5 * i$, or ${0, 5, 10, 15, 20, 25}$.

We then saw how to add the terms in a sequence using the sigma notation as in: 

$$\sum_{i=1}^{5} 5*i$$ which translates to $0 + 5 + 10 + 15 + 20 + 25 $.  Going forward we will use sigma notation to explain concepts in math and data science.
