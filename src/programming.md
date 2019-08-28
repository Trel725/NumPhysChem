# Python programming basics

To get started, firstly Python need to be installed,
which could be easily done by following instructions
from official [website](https://www.python.org/).
This will create minimal setup, enough for work. Still,
more complex program, called [Spyder IDE](https://www.spyder-ide.org/) 
(for Integrated Development Environment) is much more convinient to use.
Here and in following parts it is assumed that reader 
uses Python 3.7, which is the latest version of the
software at the moment of writing. Some examples
may use the functionality of Spyder, nevertheless 
they could be done in any preferred code editor.

Any computer program is nothing more than a sequence of 
simple commands. The programming languages are divided
into two main cathegories: compiled and interpreted. 
The formers are languages which are directly translated
into machine code, that runs on real hardware. Nevertheless
this is the only way to efficiently utilize computational
resources it requires much more care and experience.
The second type, interpreted languages are actually
commands to another program, called interpreter.
This gives, at the price of speed, ability to make
programming much closer to the human thinking.

As a simple example, lets start with the following program:

```python
print("This is")
print("Physical")
print("Chemistry")
```

The output of this command sequence will be:

	This is
	Physical
	Chemistry

As you may guess command *print* prints the
string to the console.

The parenthesis means that *print* is a function
which is *called*:

	print - function name
	print() - function call

This syntax is inspired from the mathematics, where
arguments are written in parenthesis:
	
	f - function
	f(x) - function with argument x

Similarly, in Python functions may have arguments, 
but in contrast to math, function are not necessary
returns value. This is sometimes called procedure,
i.e. the piece of code which does something useful.

Thus command
``` Python
print("Chemistry")
```
means to call the function (indicated by parenthesis), named 
*print* with argument "Chemistry".

## Data types

Why "Chemistry" is enclosed in the quotation mark?
This follows from the so called type system. 
Due to inability of machine to handle any data which
is entered, the types are intriduced, which describe how
to work with different information. With some imagination,
similar concept could be found in math, for example a 
real number, complex number, vector, matrix, etc.
Any of this entities is a type, i.e. a set of operations
are defined for them. For example it is known how to add
real numbers or matrices, but it is nonsense to add
matrices to reals. On the other hand, real and
complex number could be added if we will think of
real as of complex with zero imaginary part. This 
thinking is called type casting in computer science
and is very useful sometimes.

Python is a dynamically typed language, which means that
in majority of cases it is not needed neither to bother with data type
nor to define it explicitly. The program will automatically understand 
what is meant. 

```python
a = 1.0 # float
b = 42 # integer 
c = 2.0+1j # complex
s = "Chemistry" # string
t = True # boolean
```

This are the most commonly used data types.
Float, recognized by dot, integer, a simple number,
complex, having both real and imaginary part, string
which should be enclosed into "double" or 'single' quotation
marks (but don't mix them!) or boolean which could have only
two values, True and False. The letters here are variables,
which are aliases for the given numbers. Now, it is possible to use
this variables to perfrom basic mathematical operations. 

As an example, in Spyder click on File tab and create new file.
The text editor should open new tab, named "untitled.py" or similar.
Enter the commands from above and
click on the green triangle on top of the window to run the
file.
Spyder will ask for filename to save the program, which
should be something reasonable. After saving, the program
will run and five variables will be created in the computer memory.
In the
right bottom corner of the Spyder there is a window, called
IPython console. It is very useful for evaluating of the small
commands without need to completely re-run the program.
Now enter `b+b` to the console. As the script (Python programs
are frequently called scripts) have been already run, the variables
exists in memory and could be manipulated from the console.

	In[7]: b+b
	Out[7]: 84
	In[8]: a+a
	Out[8]: 2.0
	In [9]: a+b
	Out[9]: 43.0

Note that if two integer numbers are added, the result is integer as well.
In case of two floats, result is a float, but in case of float and integer
result is casted to the float, i.e. integer 42 is understood as the float 42.0.

Another important consequnece of typing system is additional error detection.

	In [12]: a+s
	Traceback (most recent call last):

	  File "<ipython-input-12-4d0c24e003cf>", line 1, in <module>
	    a+s

	TypeError: unsupported operand type(s) for +: 'float' and 'str'

This clearly indicates that it is nonsence to add number to a string.
Still, typing error can not provide 100 % error detection, because 
conviniece is on the first place. The language definces some operations, which
are not mathematically correct, but very useful, such as string addition:

	In [13]: s+s
	Out[13]: 'ChemistryChemistry'

Still, in majority cases it is not necessary to bother much about types.

## Data structures

In general, we use computers to process some data. This is why programming
languages have developed rich system of data structures.

1. Lists

Lists are sequences of variables of same or different types:

```python
lst1 = [1, 2, 3]
lst2 = [1.0, 2.0, 3.0]
lst3 = [1, 2.0, "Python"]
```

They allow to store information, which should be grouped together.
New items could be appended to the lists using a **method** *append*.
Method is a function which is bound to the own data structure. 
E.g. to add the number 5 to above-defined lst1.

	In [16]: print(lst1)
	[1, 2, 3]

	In [17]: lst1.append(5)

	In [18]: print(lst1)
	[1, 2, 3, 5]

To insert number 6 to other position method *insert* exists:

	In [20]: lst1.insert(2, 6)

	In [21]: print(lst1)
	[1, 2, 6, 3, 5]

Obtained list could be sorted with *sort*:

	In [22]: lst1.sort()

	In [23]: lst1
	Out[23]: [1, 2, 3, 5, 6]


2. Tuples

Tuples are similar to lists but immutable, i.e. after definition
they could not be changed anymore. 

```python
tpl=(2, 4)
```

They are useful for multiple definitions:
```
(a, b, c) = (1, 2, 3)
```
This will create three variables in a one string.

3. NumPy types

Vanilla Python is not well suited to scientific calculations due to 
absence of arrays, special data structures which efficiently 
handles sequences of the **same type**, which could consist
of millions of units. This is why NumPy (numerical Python)
module was developed. It introduces few important types,
but worth separate discussion in following chapter.

## Iterating

One of the most important structures in programming are loops,
which are a method to make a computer performs large amount of
routine operations. The most important type of loop in Python
are **for** loops, usage of which are demonstrated below:

```python
for elem in lst1:
    print(elem)
```

	1
	2
	3
	5
	6

The main idea here is that for loop splits an *iterable* (common name
for data types, which could be split, such as list in that case) into elements, and assign
the value of this element to variable, which is specified in the loop declaration
(elem in that case). This is *very powerful* programming technique. E.g. to calculate
the seconds powers of the numbers in list:

```python
for elem in lst1:
    print(elem**2)
```

	1
	4
	9
	25
	36

Or to calculate the sum of list:
```python
sm = 0 # initialize the variable to hold the sum
for elem in lst1: 
    sm += elem # add value of each element to the sum
print(sm) # output result
```
Note that the *body* of cycle (the part of code that is executed
on every iteration is separated by tab or four spaces), while
parts, that should be executed only once (sum initialization and printing)
are not separated.

## Indexing

Iterables could be indexed with the square brackets, with numbering starting at zero.

	In [49]: print(lst1)
	[1, 2, 3, 5, 6]

	In [50]: print(lst1[0])
	1

	In [51]: print(lst1[3])
	5



## Functions

In programming, functions could have two meanings without 
clear difference between them. First kind is a function
in mathematical sence, which takes an input and returns 
output, for example:

```python
def square(nmbr):
    result = nmbr**2
    return result
```

This function takes argument, which becomes available inside the function
body under alias *nmbr*, creates new variable *result*, squares the number (
double asterisk is a raising to power operator), puts the square
into the result variable and returns it. The body of function is 
separated by the tabs or spaces in the same manner as for loop. 
Keyword **return** means that this value is the output of the function.
Now, it can be used as:

	In [41]: var = square(5)

	In [42]: print(var)
	25


Another types of functions are a pieces of code, which just executed, but does not
return anything.

```python
def greeting():
    print("Hello, user")
```

	In [55]: greeting()
	Hello, user

It is possible combine both approaches:

```python
def greeting(name):
    print("Hello", name)
```

	In [61]: greeting("Alex")
	Hello Alex
