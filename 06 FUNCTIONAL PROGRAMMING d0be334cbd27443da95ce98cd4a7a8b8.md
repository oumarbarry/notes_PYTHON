# 06. FUNCTIONAL PROGRAMMING

[Functional Programming in Python: When and How to Use It - Real Python](https://realpython.com/python-functional-programming/)

> **FP has one and only one pillar: Pure Functions**
> 

## What is Functional Programming ?

<aside>
💡 FP is all about packaging our code into separate chunks, so everything is well organized in each part of the code and each part is organized in a way that make sense based on functionality.

Like OOP, FP is so all about separation of concerns.

BUT unlike OOP, FP separates data and actions/functions.

FP is so all about keeping data and actions separate, so that we can focus on pure functions in one side and on data, in another side.

</aside>

<aside>
💡 The goal of functional programming (like OOP too) is to make code:

- clear and understandable,
- easy to extend,
- easy to maintain,
- memory efficient,
- and finally DRY
</aside>

## Pure Functions

<aside>
💡 A pure function has 2 rules:

- first is that given the same input, it will always return the same output
- second point is that it should not produce any side effects

Side effects are things that a function does, **that affects his outside world i.e his parent scope or the global scope**

</aside>

<aside>
💡 With pure functions we have less buggy code, code is easier to test, easier to understand.

And by the way, we have the benefit of not having different parts of code touching and affecting each, other which makes life as programmer so much easier.

But remember pure functions is more a guideline that an absolute, because it's impossible to have pure functions everywhere.
In real world, some functions must affect the outside otherwise we wouldn't have any programs.

</aside>

<aside>
💡 Manage to create mostly pure functions and only have few non pure functions.

</aside>

## Example of Pure Functions (map, filter, zip and reduce)

```python
# map(function, *iterables)
def times2(item):
	return item*2

print(list( map(times2, [1,2,3]) )) #--> will output [2,4,6]

# filter(function, *iterables)
def is_odd(item):
	return item%2 != 0

print(list( filter(is_odd, [1,2,3,4]) )) #--> output: [1,3]

# zip(iterable1, iterable2, ..., iterableN)
list1 = [1,2,3]
list2 = [9,8,7]
print(list( zip(list1, list2) )) #--> output: [(1,9), (2,8), (3,7)]

# reduce(function, data, initial)
from functools import reduce
def accumulator(receiver_of_initial, item):
	return receiver_of_initial + item
print( reduce(accumulator, [1,2,3]), 10) ) #--> 16
```

## Lambda Expressions

<aside>
💡 lambda function in Python is equivalent to anonymous function in other language

anonymous functions are just like normal functions and even behave equally but we only use them once and they don't have a name

lambda function is usually defined as one time anonymous function that you don't need more than once

</aside>

```python
# lambda params: action_on_params

# generic_example.py
print(list(map( lambda item: item*2, [1,2,3] ))) #--> output: [2,4,6]
print(list(filter( lambda item: item%2 !=0, [1,2,3,4] ))) #--> output: [1,3]
print(reduce( lambda acc, item: acc+item, [1,2,3], 0 )) #--> output: 6

# list_sorting.py (how to sort by the tuple second item):
my_list = [(0,2), (4,3), (9,9), (10,-1)]
my_list.sort(key = lambda t: t[1])
```

## Comprehensions

<aside>
💡 When we talk about **comprehensions** we talk about list, set and dictionary comprehension.

Comprehensions **are a quicker way to create list or set or dict** in Python (instead of using loops).

</aside>

```python
# list_comprehension = [ expression for item in iterable if condition ]
li1 = [ char for char in 'hello' ]
li2 = [ num**2 for num in range(100) ]
li3 = [ num for num in range(100) if num%2==0 ]

# set comprehension is similar to list comprehension, just change [] by {}

# dict_comprehension = { key:value for key,value in simple_dict if value%2==0 }
di = { num:num*2 for num in [1,2,3] }
```

```python
# example.py : use comprehension to return a list with only duplicated items
data = ['a', 'b', 'c', 'b', 'm', 'n', 'n']
duplicates = list({ item for item in data if data.count(item)>1 })
```