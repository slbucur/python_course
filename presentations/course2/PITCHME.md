## Course 2
### Using external libraries

---

* Local python installation
* Maybe some git
* Python style guide
* Object oriented programming (basics)
* Using external libraries
* Bonus - git

---

How did `Homework 1` go?
Let's take it [step by step](#/65).

---

#### What is Python (the executable).

* It's the standard python interpreter.

* When you install it, it appends your `%PATH%` variable, so you will have
it available everywhere in the shell.

---

This executable:
* interprets and executes python instructions from python files
* conceptually it's a virtual machine, because it abstracts the
underlying hardware and software to some basic programming concepts
* python has it's own internal operations called Operation Codes
(OPCodes)

---

### Virtual environments

* An isolated python instance where you
 can install dependencies without affecting the global python
 installation
* This way you can have separate dependencies (external libraries)
for every project

---

### Pipenv

* Pipenv is a library that makes it very easy to work with virtual
environments

* create a new directory an change the directory into it
```bash
mkdir project_name
cd project_name
```

* initialize pipenv
```bash
pipenv install
```

---


* Right now we are still using the global python installation
```
which python
```

* Change to the virtual environment
```
pipenv shell
```

* The python installation has changed
```
which python
```

---

* If you look around, you'll see two files:
  * [Pipfile](https://github.com/slbucur/python_course/blob/master/Pipfile)
  * [Pipfile.lock](https://github.com/slbucur/python_course/blob/master/Pipfile.lock)
* Let's look at them for a little

Note:
The Pipfile is straightforward, with just two dependencies: 
* jupyterlab
* requests

If we look in the Pipfile.lock, thogh, we can see all 
the complexity hidden from us.

Jupyterlab depends on many other libraries, 
and they are all here.

---

### Dependencies

* External libraries that you can use in your own code
* It's usually code written by other people that was open source
* You already know one example:
  * Jupyter

---

### [pypi.org](pypi.org)

* Platform containing thousands of python projects
* All projects are vetoed by the community
* All packages here can be installed with **pip**

---

### Using dependencies

* Let's install a library for doing http requests
* It's called requests

```bash
pipenv install requests
```

---

* Now let's open a notebook

```python
import requests
response = requests.get('https://google.com')
print(response.text)
```
* What do you see?

---

## Object oriented programming

---

### OOP

* Recall the last course, about objects and properties
* objects:
  * hold data
  * have properties

* OOP allows us to have hierarchies of objects (Think parent-child).

---

* Let's create our own object

```python

class MyAwesomeObject():
    def be_awesome(self):
        print('😎')

my_awesome_object = MyAwesomeObject()
my_awesome_object.be_awesome()

```

---

* A bit of complication

```python
class MyAwesomeObject():
    been_awesome = 0
    def be_awesome(self):
        if self.been_awesome >= 5:
            print("I've been awesome too many times")
        else:
            print('😎')
            self.been_awesome += 1

my_object = MyAwesomeObject()
for i in range(7):
    my_object.be_awesome()

```

---

### Inheritance

```python
class Animal():
    def __init__(self, sound):
        self.sound = sound

    def make_sound():
        print(sound)

class Cat(Animal):
    def __init__(self):
        super().__init__('Meow !')

class Dog(Animal):
    def __init(self):
        super().__init__('Bark !')

cat = Cat()
dog = Dog()

cat.make_sound()
dog.make_sound()

```
Note:
A small biological hierarchy.
Both cats and dogs are animals and make sounds.
The way they make sounds is the same (by printing to the console).
Their sounds are different though:
  * Bark for the dog
  * Meow for the cat

---

### __init__

* This is the method called when instantiating an object

```python
class MiniInteger():
    def __init__(self):
        self.state = 0
    def increment():
        self.state += 1
        print(state)

mini_int = MiniInteger()
for i in range(4):
    mini_int.increment()

```

Note:

Here we have a very small example of an integer.
It can only increment.

When we initialize it with MiniInteger(), the state
initializes with 0.
Then we can increase that state with 1 using 
the MiniInteger.increment() function

---

### OOP - Conclusions

* OOP is used extensively throughout python
* It's not usually necessary to create your 
own hierarchies
* But it's important to know for using other libraries

---

### Exceptions

* Exceptions are a classic example of OOP in python
* When an exception is raised in the program the program stops
* Unless the exception is caught in the code


---

### KeyboardInterrupt

* Try this in an notebook. It will sleep forever.
* To stop it, use the ⏹️ button
* This will send a Ctrl+C to the program, and raise a KeyboardInterrupt exception

```python
from time import sleep
while True:
    sleep(1)
```

---

### The stacktrace


```python
---------------------------------------------
KeyboardInterrupt
Traceback (most recent call last)
<ipython-input-1-ecf9bc35922a> in <module>()
      1 from time import sleep
      2 while True:
----> 3     sleep(1)

KeyboardInterrupt: 
```

* Under normal python behavior, if an exception is not caught
a stack trace will be displayed on the screen
* This shows where the exception was encountered

---

### Another exception

```python
nr = 12
divisors = [0, 1, 2, 3, 4, 6, 12]

for divisor in divisors:
    print(f'{nr} / {divisor} = {nr / divisor}')
```

---

```python
---------------------
ZeroDivisionError
Traceback (most recent call last)
<ipython-input-8-e92e33772d17> in <module>()
      3 
      4 for divisor in divisors:
----> 5     print(f'{nr} / {divisor} = {nr/divisor}')

ZeroDivisionError: division by zero
```

---

* Let's try to catch that

```python
nr = 12
divisors = [0, 1, 2, 3, 4, 6, 12]

for divisor in divisors:
    try:
        print(f'{nr} / {divisor} = {nr / divisor}')
    except ZeroDivisionError:
        print(f'Can\'t divide {nr} by 0')
```

Note:
This works similar to an **if** block.

Also notice the quote (`'`) escaping with `\`.
Since the string is made with single quotes, we need to 
escape the quotes inside the string.
An alternative would have been `f"Can't divide {nr} by 0"`

---
### Try-except

* Try-except works similar to an **if** block
* You need to pass the type of exception you are catching in **except**

```python
try:
    1 / 0
except ZeroDivisionError:
    print('To infinity and beyond!')
```
---

### OOP in exceptions

* All exceptions inherit from the **Exception** class
* So this also works:

```python
try:
    1 / 0
except Exception as e:
    print(type(e))
    print(e)
    print('To infinity and beyond')
```

---

## The Exception class

* if you want to catch any possible exception,
use `except Exception`
* it's recommended you don't do that, and manually
set all exceptions you want to handle
* otherwise it can be **very** hard to debug the code

---

### Our own exception

```python
class NotAnAppleError(Exception):
    pass

def process_apple(fruit):
    if fruit != '🍏':
        raise NotAnAppleError()

    print('Making apple juice')
fruits = ['🍏', '🍌', '🍓']

for fruit in fruits:
    process_apple(fruit)

```

Note:
The `pass` keyword denotes that we don't want anything 
but inheriting the class.

Try to catch the exception so that the program 
doesn't stop.

---

### The `pass` keyword

* The `pass` keyword is used to not do anything.
* It can be used a placeholder until actual code will
be written

```python
apple = '🍏'
fruit = '🍓'

if fruit == apple:
    pass
else:
    print(f'{fruit} is not an {apple}')
```

---

## The python module system

Two types of modules:
* user modules
* system modules
    * python default modules
    * external libraries

---

* default way of importing

```python
import time # a default python module

print('Sleeping 10 seconds')
time.sleep(10)
```

---

* anther way of importing
* imports only the needed function

```python
from time import sleep
print('Sleeping 10 seconds')
sleep(10) 

```

---

* import everything from a module
* usually not recommended

```python
import * from time
sleep(10)
```

---

### Your own modules


* Go to the `code/module_parent` folder
* Open the notebook
* What do you see

---

* The python module system is based on directories
* From python's point of view, directories that have
an `__init__.py` file in them are considered modules

---

### Importing from your own modules

```
from module1 import function1
from nested.module2 import function2
function1()
function2()
```

---

The file structure:

```
module_parent/
├── __init__.py
├── module1.py --> function1
├── nested
│   ├── __init__.py
│   └── module2.py --> function2
└── notebook.ipynb
```

Note:

* Our notebook is in the top folder named `module_parent`.
* This has an `__init__.py ` file, so `module_parent` is the top level module.
* Another file, `module1`, is also a module
  * so we can do `from module1 import function1`
* A folder called `nested` is also here
  * since it has an `__init__.py`, it's also a module
  * since it has a file name `module2.py`
    * we can do `from nested.module2 import function2`

---

### Gotchas regarding modules

* try to do imports at the top of the module
  * it's more readable that way
* imports work related to the module where you call
* For example, let's look at function3 in module3.

```python
from nested.module3 import function3
function3()
```

Note:

* `module3` calls `function1` from `module1`.
* Works because you are calling the module from `module_parent`
* If you try from the nested folder, for example, it will not work
* Let's try that now, create a new notebook in the nested folder

---

### Hashtag version 2

```python
from twitter import Api, TwitterError
from openpyxl import load_workbook
from pprint import pprint

EXCEL_FILE = './hashtag.xlsx'
EXCEL_SHEET = 'hashtag'

api = Api(
    consumer_key='uV8NLoJBkI46NPiHZJgvJY2PP',
    consumer_secret='4gtGFn2QySlxnyFkdcnpjXy5a8rVRyBdaoJcXiJordEbx0UpXk',
    access_token_key='994947930971885569-rZGjnP0IhF4UbPHHQjKlr2l2eI4m4iM',
    access_token_secret='eAdMlpqzmZApHAVHa1WRziIQw0U5KP62AhfyOdasyUwiz'
)

def get_tweets():
    wb = load_workbook(EXCEL_FILE)
    sheet = wb[EXCEL_SHEET]

    tweets = []
    header = {}
    for i, row in enumerate(sheet.rows):
        if i == 0:
            for j, cell in enumerate(row):
                header[j] = cell.value
        else:
            tweet = {}
            for j, cell in enumerate(row):
                tweet[header[j]] = cell.value
            tweets.append(tweet)

    return tweets

def send_tweets():
    tweets = get_tweets()
    print('Tweets to be sent')
    pprint(tweets)
    
    print('Starting to send tweets')
    for tweet in tweets:
        update = '{} {}'.format(tweet['message'], tweet['hashtag'])
        print(f'Sending update `{update}`')
        try:
            status = api.PostUpdate(update)
            print('Update sent successfully')
        except TwitterError as e:
            print('Failed {}'.format(e))

send_tweets()

```

---

* Quite a lot going on, let's take it step by step.

---

### Twitter API

* Twitter has a REST API which lets you:
  * read tweets
  * send tweets
  * many more
* A library was created to wrap this basic API: [python-twitter](https://python-twitter.readthedocs.io/en/latest/)

---

<iframe src="https://python-twitter.readthedocs.io/en/latest/" style="width:75vw; height:50vh">

---

To use the twitter API, you will need 3 things:
* to import the library 
```python
import twitter
```

* to instantiate it
```python
api = twitter.Api(
    consumer_key='', consumer_secret='',
    access_token_key='', access_token_secret=''
)
```

* to use it with `api.<method>`
```python
api.PostUpdate('Update text')
```

---

### Secrets

* To get the secrets, you'll need to set up a new App in twitter (and a user, maybe?)
* Don't worry, one is already set up for you, [here](https://apps.twitter.com/app/15218341/keys)
  * The user is * Sally WaffleLover*, we'll give you the credentials during the course 😉
* If you want it for your own twitter user, follow this python-twitter 
[page](https://python-twitter.readthedocs.io/en/latest/getting_started.html), 
it's pretty good

---

#### `openpyxl`

* This is a library used to read/write Excel 2007+ files (xlsx)
* An alternative could have been pandas, but it's a bigger library
* It enables reading an excel document as a python object

---

### Basic `openpyxl` usage

```python
wb = load_workbook('./hashtag.xlsx')
sheet = wb['hashtag']

print(sheet.rows)
for row in sheet.rows:
    print(row)
    for cell in row:
        print(cell.value, end=';')
```

Note:

* To load a sheet, it's easy.
* First you have to open the file using `load_workbook`.
* Then you can read the sheet using `workbook['<sheetname>']`.
* The sheet will have an object called `rows`.
* This is called a `generator` object, as you can't read it directly
, you have to iterate over it.
* This is done for performance reasons, as you don't always 
want to load the entire file in memory.
* Every row is a actually a list of cells
* We can iterate over them and find their values

---

### Getting the tweets

```python
def get_tweets():
    wb = load_workbook(EXCEL_FILE)
    sheet = wb[EXCEL_SHEET]

    tweets = []
    header = {}
    for i, row in enumerate(sheet.rows):
        if i == 0:
            for j, cell in enumerate(row):
                header[j] = cell.value
        else:
            tweet = {}
            for j, cell in enumerate(row):
                tweet[header[j]] = cell.value
            tweets.append(tweet)

    return tweets
```

@[2-3](Load the workbook)
@[5-6](Initialize the header as an empty dict, and the tweets as an empty list)
@[7](Iterate over the rows)
@[8-10](Generate the header object - key will be an integer - the column, value the header name)
@[11-15](Generate the tweet dictionaries)

Note:

* What does this code do?
* It reads an file with a header and rows
* And generates a list of dictionaries
* `enumerate` is used to iterate over a list and generate two variables:
  * the index (from 0 to len(list))
  * the value
  * this way we don't need to keep track of the index ourselves

---

### Sending the tweets


```python
def send_tweets():
    tweets = get_tweets()
    print('Tweets to be sent')
    pprint(tweets)
    
    print('Starting to send tweets')
    for tweet in tweets:
        update = '{} {}'.format(tweet['message'], tweet['hashtag'])
        print(f'Sending update `{update}`')
        try:
            status = api.PostUpdate(update)
            print('Update sent successfully')
        except TwitterError as e:
            print('Failed {}'.format(e))
```
@[2](Load the tweets)
@[3-4](Print the tweets, prettified)
@[6-7](Start sending the tweets. Iterate over.)
@[8](Generate the update message. This way we can print it and send it 😉)
@[9](Log that we try to send the update)
@[10-15](Try to send the tweet, but catch the errors)

Note:

* A lot of printing, but the core functionality can be resumed to
```python
api.PostUpdate(update)
```

---

### Homework 3

1. Try to also send mails to yourself. (For Gmail you can use this [link](http://stackabuse.com/how-to-send-emails-with-gmail-using-python/))
2. Read the documentation about python [decorators](https://realpython.com/primer-on-python-decorators/)
3. Create an account on github.com, if you don't have one already.
   As a developer you'll find it quite useful.
4. How did Homework 1 go? Ask us question now.


---

### Next course

1. In the next course we'll make a simple API using Flask.
2. Also we'll some github fundamentals, like forking a 
   project and backing up your code.
3. Beyond that we'll cover one of the these topic, by popular vote

Go to https://doodle.com/poll/wkmw7ayp3wtk97rv

---


### Topics

The first few topics chosen will be discussed in the next course.

* Simple REST API in Django
* Building a bot for Telegram (or facebook messenger)
* Data Analysis with Python, Numpy and Pandas (generating charts and insights from data)
* Querying relational databases
* Regex in Python
* Docker for Python applications

---


* Image generation (art) with Python
* Making a video game with pygame
* Generating PDF files with Python
* Generating .exe files from python applications with PyInstaller
* Basic image analysis (Computer vision)

We can discuss other topics now, and add them to the poll. Happy choices 😊!
