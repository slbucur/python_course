## Python 101
### Introduction to Python @Cegeka

---

## Introduction

- Short course  |
- Very hands-on, project in every course  |
- Repetition, repetition, repetition  |

Note:
This will be a short course, that covers the main features of python.
We won't go into details, but we want you to get a solid understanding
of the basics and where to look if you have questions (yes, you will
become an expert python googler).

In programming, practice is better than theory, so in every course
we'll have a hands-on project.

To learn something, you need to repeat it enough times that it becomes
a part of your thought. This is why over the course we will use use
the same concepts again and again in different contexts.

---

## Rules

- Interactive course, you can ask me any question at any time  |
- No question is a dumb question  |

Note:
Since this is a hands on course, it's meant to be interactive.
Ask me any question at any time.
I mean it, no question is a dumb question

---

## Project - Hashtag

- Simple project
- We'll add more features to every course
- Reads a list of hashtags and messages and publishes them to twitter
using the twitter API

---

- Steps:
  - Start with a hardcoded list and print it in the terminal (Course 1)
  - Read the input from excel and use the twitter API (Course 2)
  - Create a web server that does this action when requested (Course 3)

In the last course we'll have a hackaton with your own ideas.

---

## Course 1
### Introduction to programming and Python


---

### What we'll cover today

- What is programming
- What is Python and what sets it apart
- Basic programming concepts
- Project **Hashtag** - part 1

---

### Programming

> Input data -> Instructions -> Output data

Also known as *coding*.


Note:
At the fundamental level, this is what programming is.
Giving a machine instructions to process data in order to create
new data.

---

### Abstractions

A modern computer abstracts the basic

`(in -> instructions -> out )` through many abstractions:
- assembly
- programming languages
- programming interfaces
- operating systems
- user interfaces
- virtualization

Note:
Over the last decades, the goal of computing was to create
abstractions.
A modern computer encapsulates data and instructions through many
abstractions.
This

---

### Instructions

A CPU has a very limited set of instructions:
```asm
INC COUNT        ; Increment the memory variable COUNT

MOV TOTAL, 48    ; Transfer the value 48 in the
                 ; memory variable TOTAL

ADD AH, BH       ; Add the content of the
                 ; BH register into the AH register

AND MASK1, 128   ; Perform AND operation on the
                 ; variable MASK1 and 128

ADD MARKS, 10    ; Add 10 to the variable MARKS
MOV AL, 10       ; Transfer the value 10 to the AL register
```

Note:

As you can see, what the machine does is pretty cryptic.
(And this is at a human readable level).
But with this base, it can perform any computation.

---

### Programming languages

- abstract underlying hardware and software (operating systems)
- provide easy to use concepts to create any instruction
- This is where `Python` comes along 😊 (finally)


---

### Python

Python is general purpose programming language with the goals of:
- ease of use
- readability
- ergonomics

---

Which one do you understand better?

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World");
    }
}
//java
```

```python
print('Hello world')
# python
```

```ruby
puts('Hello world')
# ruby
```

Note:

As you can see, python values brevity (small instructions), but also
 understandability.

The java version is obviously very long, though you can pretty much
guess that `System.out.println` prints to the console.

Ruby values brevity, but it's not immediate what `puts` means.
(It stands for put string).

This is not to say that the design of these other languages is worse,
they all have their values and guidelines, but I think `Python` really
hits it's goals with ease of use and understandability
most of the time.

---

### Why `Python` ?

- simple, easy to use language
 - doesn't get in your way
- vast (huge) amount of good quality packages
 - no need to reinvent the wheel
- ease of installation
 - available by default on most Linux Distros
- third language by popularity

---

Useful for a many development paths:
 - Scripting (one off script or batch jobs)
 - Web development (Django, Flask)
 - Data science (Machine learning, Data processing, Data analysis)
 - Security (hacking, whitehat or not)
 - Gaming
 - Probably many more

---

### Why not `Python`?

- slow
- obstacles for concurrency
- operational overhead

Note:

Slow:

About 20 times slower than C/C++ for first draft algorithms
- don't be intimidated, most math calculations can be done using
high performance libraries (numpy)
- pypy (a custom python interpreter) is > 8 times faster than standard
python

Concurrency:

- historically hard to create use more than 1 CPU
- got much better in the last decade
- other languages had (and some still have) the same issues

Operational:

- the python library is pretty big (40 mb)
- a medium sized project can easily install 0.5 gb of dependencies
- solvable issues, but you need to keep them in mind


---

## Python is the perfect glue language

You can call almost any library and interact

 with any backend system through python:
- libraries made in other languages
- databases
- APIs
- authentication systems
- really, anything 😄

---

### Hashtag - version 0

```python
tweets = [
    {'message': 'I love exotic fruits', 'hastag': '#mango'},
    {'message': 'Local foods are the best', 'hastag': '#pear'},
    {'message': 'Why not vegetables', 'hastag': '#celery'}
]

for tweet in tweets:
    print('Sending tweet:')
    print('{} {}'.format(tweet['messsage'], tweet['hashtag']))

```

Quite a lot going on, let's take it one by one.

@[1](A list holding the tweets)
@[2](A dictionary)
@[7](Take an item for element of the list)
@[8-9](Print the resulting tweet)

---

Confused? Don't worry, we'll start with the basics.

---

Go to {url} and you will be able to use python in the browser.

All materials are available at https://github.com/slbucur/python_course

Copy paste this snipped in the browser and run it.

What do you see?

---

## Variables
- simple ones: string, int, float

```python
a = 'Banana'
print(a) # a string - sequence of characters
print(type(a)) # a string

a = 1
b = 2
print(a + b) # a and be are integers

a = 18
b = 5
print(a / b) # dividing a over b gives a float (rational number)

# for integer division use //
print(a // b)
```

---

- tuple

A sequence of things. Once initialized it can't change: `immutable`.

```python
fruits = ('mango', 'banana', 'apple')
print(','.join(fruits)) # a basket of fruits (actually a string)

fruits[0] = 'pear' # this will error out
```

---

- list

Also a sequence of things. A list can change

(add items, remove item, change items)

```python
fruits = ['mango', 'banana', 'apple', 'monkey']

# what's that monkey doing there?
delete fruits[3] # as you can see, python is 0 indexed

fruits.append['pear']
print(','.join(fruits)) # a basket of fruits (actually a string)

```

---

- dictionary

A map with keys and values.
```python

bank_account = {
    'Joe': 1,
    'Bill': 72_000_000_000, # python 3 syntax
}

print(bank_account['Joe'])
print(bank_account['Bill'])
```

Note:
What Bill is that?


---

## Objects

What do all these variables have in common?
They are **objects**

---

Everything in python is an object:

* variables
* functions
* classes
* modules

---

_But what is an object?_

A structure with that holds **data** and has **properties**

Note:
Yes, it's that simple. We're not going into Object Oriented Programming
just yet.

---

Let's take a basic example, and Integer.

It holds a value, a natural number:
* 0, 1, 2, 3 ... n
* -1, -2, -3, ... -n

---

And it has a bunch of properties:
* you can **add** another integer to it => which gives another integer
* **subtract** another integer
* **multiply**
* **divide**

---

Holds a value:
```python
a = 1
```

Add another integer
```python
a = 1
b = 2
print(a + b)
```

Subtract another integer:
```python
a = 1
b = 2
print(a - b)
```

---

Multiply
```python
a = 11
b = 653
print(a * b)
```

Divide
```python
a = 15
b = 2
print(a / b) # floating point (decimal) division
print(a // b) # integer division
```

Note:
It gets a bit interesting at division. In python 3, if you divide
two integers, by default you will get a floating point number.
Use `//` for integer division.

---

There are more properties an integer can have.

We can see them all with this:
```python
>> help(int)
```

```
class int(object)
 |  int(x=0) -> int or long
 |  int(x, base=10) -> int or long
 |
 |  Convert a number or string to an integer, or return 0 if no arguments
 |  are given.  If x is floating point, the conversion truncates towards zero.
 |  If x is outside the integer range, the function returns a long instead.
 |
 |  If x is not a number or if base is given, then x must be a string or
 |  Unicode object representing an integer literal in the given base.  The
 |  literal can be preceded by '+' or '-' and be surrounded by whitespace.
 |  The base defaults to 10.  Valid bases are 0 and 2-36.  Base 0 means to
 |  interpret the base from the string as an integer literal.
 |  >>> int('0b100', base=0)
 |  4
 |
 |  Methods defined here:
 |
 |  __abs__(...)
 |      x.__abs__() <==> abs(x)
 |
 |  __add__(...)
 |      x.__add__(y) <==> x+y
 |
 |  __and__(...)
 |      x.__and__(y) <==> x&y
 |
 |  __cmp__(...)
 |      x.__cmp__(y) <==> cmp(x,y)
 |
 |  __coerce__(...)
 |      x.__coerce__(y) <==> coerce(x, y)
 |
 |  __div__(...)
 |      x.__div__(y) <==> x/y
 |
 |  __divmod__(...)
 |      x.__divmod__(y) <==> divmod(x, y)
 |
 |  __float__(...)
 |      x.__float__() <==> float(x)
 |
 |  __floordiv__(...)
 |      x.__floordiv__(y) <==> x//y
 |
 |  __format__(...)
 |
 |  __getattribute__(...)
 |      x.__getattribute__('name') <==> x.name
 |
 |  __getnewargs__(...)
 |
 |  __hash__(...)
 |      x.__hash__() <==> hash(x)
 |
 |  __hex__(...)
 |      x.__hex__() <==> hex(x)
 |
 |  __index__(...)
 |      x[y:z] <==> x[y.__index__():z.__index__()]
 |
 |  __int__(...)
 |      x.__int__() <==> int(x)
 |
 |  __invert__(...)
 |      x.__invert__() <==> ~x
 |
 |  __long__(...)
 |      x.__long__() <==> long(x)
 |
 |  __lshift__(...)
 |      x.__lshift__(y) <==> x<<y
 |
 |  __mod__(...)
 |      x.__mod__(y) <==> x%y
 |
 |  __mul__(...)
 |      x.__mul__(y) <==> x*y
 |
 |  __neg__(...)
 |      x.__neg__() <==> -x
 |
 |  __nonzero__(...)
 |      x.__nonzero__() <==> x != 0
 |
 |  __oct__(...)
 |      x.__oct__() <==> oct(x)
 |
 |  __or__(...)
 |      x.__or__(y) <==> x|y
 |
 |  __pos__(...)
 |      x.__pos__() <==> +x
 |
 |  __pow__(...)
 |      x.__pow__(y[, z]) <==> pow(x, y[, z])
 |
 |  __radd__(...)
 |      x.__radd__(y) <==> y+x
 |
 |  __rand__(...)
 |      x.__rand__(y) <==> y&x
 |
 |  __rdiv__(...)
 |      x.__rdiv__(y) <==> y/x
 |
 |  __rdivmod__(...)
 |      x.__rdivmod__(y) <==> divmod(y, x)
 |
 |  __repr__(...)
 |      x.__repr__() <==> repr(x)
 |
 |  __rfloordiv__(...)
 |      x.__rfloordiv__(y) <==> y//x
 |
 |  __rlshift__(...)
 |      x.__rlshift__(y) <==> y<<x
 |
 |  __rmod__(...)
 |      x.__rmod__(y) <==> y%x
 |
 |  __rmul__(...)
 |      x.__rmul__(y) <==> y*x
 |
 |  __ror__(...)
 |      x.__ror__(y) <==> y|x
 |
 |  __rpow__(...)
 |      y.__rpow__(x[, z]) <==> pow(x, y[, z])
 |
 |  __rrshift__(...)
 |      x.__rrshift__(y) <==> y>>x
 |
 |  __rshift__(...)
 |      x.__rshift__(y) <==> x>>y
 |
 |  __rsub__(...)
 |      x.__rsub__(y) <==> y-x
 |
 |  __rtruediv__(...)
 |      x.__rtruediv__(y) <==> y/x
 |
 |  __rxor__(...)
 |      x.__rxor__(y) <==> y^x
 |
 |  __str__(...)
 |      x.__str__() <==> str(x)
 |
 |  __sub__(...)
 |      x.__sub__(y) <==> x-y
 |
 |  __truediv__(...)
 |      x.__truediv__(y) <==> x/y
 |
 |  __trunc__(...)
 |      Truncating an Integral returns itself.
 |
 |  __xor__(...)
 |      x.__xor__(y) <==> x^y
 |
 |  bit_length(...)
 |      int.bit_length() -> int
 |
 |      Number of bits necessary to represent self in binary.
 |      >>> bin(37)
 |      '0b100101'
 |      >>> (37).bit_length()
 |      6
 |
 |  conjugate(...)
 |      Returns self, the complex conjugate of any int.
 |
 |  ----------------------------------------------------------------------
 |  Data descriptors defined here:
 |
 |  denominator
 |      the denominator of a rational number in lowest terms
 |
 |  imag
 |      the imaginary part of a complex number
 |
 |  numerator
 |      the numerator of a rational number in lowest terms
 |
 |  real
 |      the real part of a complex number
 |
 |  ----------------------------------------------------------------------
 |  Data and other attributes defined here:
 |
 |  __new__ = <built-in method __new__ of type object>
 |      T.__new__(S, ...) -> a new object with type S, a subtype of T
```

---


Take any other basic type and let's think about the
data it holds it's properties:
* tuple
* list
* string
* dictionary

---

## Control flow

Note:
Now we have objects with properties.

We need to do things with them.

This is where control flow comes along.

---

Definition:

_Instructions to process data_

---

Think of it as a recipe:

You have:
* two eggs
* bacon
* bowl
* a stove
* and a pan

---

Steps:
1. Break the eggs
2. Cut the bacon
3. Mix them in the bowl
4. Start the stove
5. Place pan on stove
6. Wait for the pan to heat up
7. Put the mix into the bowl
8. Scramble
9. Enjoy 🍳

---

Let's try to this in python:
```python
eggs = [egg1, egg2]
bacon, bowl, stove, pan

ingredients = []

for egg in eggs:
    egg.break()
    if egg.is_good():
        ingredients.append(egg)

if ingredients.empty():
    # we have no good eggs
    order_pizza()

```

---

```python

bacon.cut()
ingredients.append(bacon)

bowl.mix(ingredients)

stove.heat()
stove.place(pan)
while pan.temperature < 100:
    wait(5)

pan.place(ingredients)

while ingredients.not_done:
    ingredients.scramble()

omlette = ingredients
omlette.enjoy()
```

---

The five elements of control flow:
* instructions
* line ordering
* conditions
* loops
* functions

---

### Instructions

Each line contains one instruction.
You can do multiple instructions using the `;` operator, but it's not
recommended.

```python
a = 1
b = 2; c = 2
```

---

### Line ordering

Instructions run in order they are ran.
If an instruction **a** is above instruction **b**, by the time we get
to **b**, **a** already ran.

```python
a = 1
print(b) # error, b is not initialized
b = 2
print(a) # a is initialized before b
```

---

### Conditions

#### if/else

If an **if** is satisfied, the code below it runs.

Otherwise, the one below **else** runs.

```python
price = 10
cash_in_pocket = 5

if cash_in_pocket >= price:
    print('You can pay with the money in your pocket')
else:
    print('Better luck next time')
```

---

#### elif

**elif** can be used to add multiple conditions to the standard
**if/else**.

```python
price = 10
cash_in_pocket = 5
cash_in_wallet = 5

if cash_in_pocket >= price:
    print('You can pay with the money in your pocket')
elif cash_in_pocket + cash_in_wallet >= price:
    print('You can pay with the money in your pocket and your wallet')
else:
    print('Better luck next time')
```

---


### Whitespace

Note:
It's time for a small side note about whitespace in python.

---

### Only one rule
Use 4 spaces for indentation

Note:
You can also use tabs, or other types of indentation, it will work,
but to make your life easy, just use 4 spaces.
It's the standard in python, as stated in PEP8 (The style guide for
python, used by almost all modern python code)

---

Whitespace is relevant in python:
* used to define code blocks:
  * if
  * while
  * for
  * functions
  * classes
* when the lines are indented under one of these blocks,
python interprets them as code blocks

---

Which one is right and why?

```python
# 1
price = 10
cash = 5
print('Tring to pay')
if cash >= price:
    print('You can buy the item')
print('Item bought')
```

```python
# 2
price = 10
cash = 5
print('Tring to pay')
if cash >= price:
    print('You can buy the item')
    print('Item bought')
```

Note:
The second one is right. The first one prints 'Item bought'
no matter how much money you have.

---

### Loop the loop

![Logo](http://www.guinnessworldrecords.com/Images/jaguar-upside-down_tcm25-396303.jpg)

---

Loops are used to iterate. You have two options:
* **for**
* **while**

Note:
You can always create a for with a while, but not the other way around.

---

### FOR

```python
fruits = ['banana', 'strawberry', 'orange', 'plum']

for fruit in fruits:
    # python 3.6 f-strings
    print(f'I like the fruit named {fruit}')

```

---

### Side note - String formatting

##### The `.format` function

```python
# the standard way since python 2.6
# has more formatting options than %
price = 10.956
print('The item costs {} dollars'.format(price))
# bonus, show only 2 decimals
print('The item costs {0:.2f} dollars'.format(price))
```

##### F-strings

```python
# new in python 3.6
price = 10.956
print(f'The item costs {price} dollars')
print(f'The item costs {price:.2f} dollars')
```

Note:
String formatting is displaying a string in another string.

---

##### String adding
```python
# because it quickly becomes unreadable
# you also need to cast any other type but string
price = 10.956
print('The item costs ' + str(price) + ' dollars')
```


##### Percent formatting

```python
# similar to the one in C
# used in older applications and libraries
# not recommended for new apps
price = 10.956
print('The item costs %s dollars' % price)
print('The item costs %.2f dollars' % price)
```


----

#### Back to loops

```python

# multiplying board

for x in range(4):
    for y in range(4):
        print(f'{x}x{y}={x * y}')
```

This might be useful to visualize:
Go to http://www.pythontutor.com/visualize.html#mode=edit and copy
the code.

Note:
You see what we did there? Multiple indentations.

---

