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
@[6](Take an item for element of the list)
@[7](Print the resulting tweet)

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


