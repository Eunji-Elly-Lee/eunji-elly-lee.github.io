---
layout:     post
title:      "Python Basics"
date:       2022-02-18
image:      python_code.jpg
categories: [Python]
---

<p class="intro"><span class="dropcap">P</span>ython is a high-level, object-oriented, general-purpose programming language developed in 1991 by Guido van Rossum.</p>

Python is known to have a concise syntax and grammar with the use of indentations focused on code readability. There are numerous packages and libraries created by developers around the world due to this Python's characteristic that is easy to read and write and the expressive structure that resembles the human thinking system. Many developers say these make it easy for beginners to learn and make Python's use easier to expand for a variety of purposes. It would be a reason Python has been on the popular list as a mainstream programming language these days.

<div style="text-align:center">
<img src="https://www.python.org/static/img/python-logo@2x.png" width="80%">
</div>

<!-- <div style="text-align:center">
<video width="65%" controls>
<source src="/assets/video/?????????????????????.mp4" type="video/mp4">
</video>
</div> -->

### Python's Environment Setup

We can download a suitable Python version for our local computer system from this link. In my case, I selected the 3.8.7 version for Windows.

<https://www.python.org/downloads/>

In the first step of the installation process, we should check the 'ADD Python to PATH' option at the bottom to add Python to PATH which is one of environmental variables. After clicking 'Install Now' in the middle, we can leave all the options in the following steps as default.

<div style="text-align:center">
<img src="/assets/img/python_img/python_install_window.png" width="80%">
</div>

After completing all processes, we can check the successful installation of Python at Command Prompt. Open the command prompt, enter 'python.' We will be able to print out words or sentences.

<div style="text-align:center">
<img src="/assets/img/python_img/python_cmd.png" width="80%">
</div>

There are many good IDEs (Integrated Development Environment) for Python programming. Many developers recommend PyCharm, IDLE, and Visual Studio Code (VS Code). I selected VS Code that I am already familiar with. It is a free and open-source code editor which has many good features, and we can just add an extension to create a Python development environment.

Search 'Python' in the Extension section of VS Code and install it.

<div style="text-align:center">
<img src="/assets/img/python_img/python_extension.png" width="80%">
</div>

Create a temporary working folder for testing, and open the folder using VS Code. After then, we will create a simple Python file in it. A Python file has an extension of .py.

<div style="text-align:center">
<img src="/assets/img/python_img/python_simple_file.png" width="80%">
</div>

In the Debug section, we can see a link 'create a launch.json file.' Click the link, and select 'Python File' as an option. We have a launch.json file now.

<div style="text-align:center">
<img src="/assets/img/python_img/python_launch_file.png" width="80%">
</div>

Run a command pallet with the shortcut 'Ctrl + Shift + p' for an installation of the Python interpreter, and search for 'Python: Select Interpreter.' After then, we should select one like our Python version currently installed.

<div style="text-align:center">
<img src="/assets/img/python_img/python_interpreter.png" width="80%">
</div>

It is all ready to sail into the Python programming world!

### Python's Basic Syntax

As mentioned earlier, Python's syntax is characterized by simplicity. We will look into Python's syntax by comparing it with Java.

**Semicolon (;)**

Unlike the semicolon that must be attached to the end of all Java's statements, it is not necessary to use it in Python. Of course, its use is not unconditionally prohibited. We can use a semicolon to separate multiple statements in a single line.

```python
print("Hello!"); print("Nice to meet you!")
print("Python is fun!")
```

**colon (:)**

A colon is not used well in Java syntax. The most famous example used is a for-each loop.

```java
for(String i: list) {
   System.out.println(i);
}
```

In Python syntax, a colon is required at the start of a block, the header line. The blocks made up of compound or complex statements include 'if,' 'while,' 'for,' and 'def.' For the next statement after a colon, we should press enter and write it on a new line. However, it is recommended to write all statements in one line in the lambda function.

```python
if 30 <= temp:
   print("Too hot!")
elif 10 <= temp and temp < 30:
   print("Perfect!")
elif 0 < temp  < 10:
   print("Take your jacket!")
else:
   print("Too cold!")

x = lambda y: y + 1
```

**Comment**

Java's single-line comment starts with two slashes (//), while in Python, a comment starts with a hash (#). We can also use triple quotations (&#39;&#39;&#39;) at the beginning and end of the multi-line comments. One good tip is to drag the lines we want to change into the comments, and press the shortcut 'Ctrl + / .'

```python
# This is a comment

''' This is
the multi-line comment'''
```

**Indentation**

Python is very strict to indentation. Java defines a block of code using braces ({ }), but Python removed it for concise syntax. Indentation is used to highlight the blocks of code in Python. Note that the first line of the code cannot have any indentation. We should avoid mixing tabs and whitespaces for making indentation, and using whitespaces are better than using taps.

```python
def function01():
   if True:
      print("Hello!")
   else:
      print("Bye!")
```

### Python's Print

We will simply print out something using Python.

Python's print() statement is the same as Java's println() statement. After printing, a cursor is automatically moved to the next line.

We can see that this `System.out.println("Hello" + 2022);` code of Java is output as "**Hello2022**." However, we cannot use String and Int data together with plus (+) in print() statement in Python without type converting. It is permissible to simply print these two different types of data together using a comma (,).

```python
print("Hello" + str(2022))
print("Hello", 2022)
```

Interestingly, the result of the first code is "**Hello2022**" without whitespace like Java's, but the second code automatically inserts whitespace between the two words, like "**Hello 2022**."

There are three ways to print out using the format function:

1)

```python
print("I like %d the most!" %7) 
print("I like %s because it's fun!" %"Python") 
print("I like %d, and %s so much!" %(7, "Python"))
```

'%d' represents an Int type, and '%s' represents a String type.

2)

```python
print("I like {} the most!".format(7)) 
print("I like {}, and {} so much!".format(7, "Python"))
print("I like {0}, and {1} so much!".format(7, "Python"))
print("I like {1}, and {0} so much!".format(7, "Python"))
```

If we don't put the index number in braces ({ }), it will be matched in order and printed.

3)

```python
print("I like {num}, and {lang} so much!".format(num=7, lang="Python"))
print("I like {num}, and {lang} so much!".format(lang="Python", num=7))
```

If we specify variable names in braces ({ }), they will be matched well regardless of the order and printed.

### Python's Fucntion

We can notice that Python's function is the same as Java's method. A Python's function can be easily defined as the 'def' keyword. Similar to Java's method syntax, there may or may not be parameters in parentheses (( )) after a function name. There may or may not be a return of a value using the 'return' keyword as well.

```python
def open_accout():
   print("New account open!")

def deposit(balance, money):
   print("Deposit has been completed. Balance: ${0}".format(balance + money))
   return balance + money

# Call the function
open_accout()
deposit(1000, 500)
```

### Python's Data Structure

We will look into Python's four data structures. We can think of these as similar to Java's List and HashMap.

1) **List**: Values are stored in order, and it is free to modify and delete elements after creation. It is created using brackets ([ ]). We can use various functions such as append(), insert(), pop(), clear(), sort().

```python
numbers = [10, 20, 30]
```

2) **Tuple**: This data structure stores values in order like List, but elements generated once cannot be modified and deleted. However, since there is no change in the data, the advantage is that the processing speed is faster than List. It is created using parentheses (( )).

```python
numbers = (10, 20, 30)
```

3) **Dictionary**: It stores data as a pair of a key and a value. The key and value are separated by a colon (:). Keys cannot be duplicated, and data management is done using the keys easily. It is created using braces ({ }).

```python
cabinet = {"A-1":"Alpha", "B-1":"Bravo", "C-1":"Charlie"}
```

4) **Set**: It stores data regardless of order and does not allow duplicated values. This Set can function like a set of mathematics. It is created using braces ({ }) or set() function. When converting Dictionary into Set using set() function, it becomes a set of keys.

```python
numbers = {10, 20, 30}
cabinet = {"A-1":"Alpha", "B-1":"Bravo", "C-1":"Charlie"}
cabinet_set = set(cabinet)
```

### Python's Import

Python's import is similar to Java's, but there is a kind of difference. The similarity is the use of the 'import' keyword, and the difference will be the use of the 'from' keyword.

When importing the entire function of a module, we can simply write the name of the module after the 'import' keyword, like this: `import random`. If we want to get only one or a few functions from a module, we will use the 'from' keyword. Interestingly, we can also import all the functions of a module using this 'from' keyword.

```python
from random import randint, choice
from math import *
```

The most impressive thing about Python's import function is that using an alias is allowed. An alias is applied like this using the 'as' keyword: `import random as rd`. We can give both modules and functions the aliases we want.

### Jump into Python

We spent this journey together to learn about Python's basics. There are more things left to learn, such as Python's class, inheritance, and package. We'll be able to look into these next time as working on some projects together.

Wrap up this time by writing a simple program with what we learned today.

```python
'''You are a taxi driver.
You only pick up passengers
who take between 5 and 15 minutes to drive time.
Create a program to calculate how many passengers you can pick up.'''

from random import *

count = 0

# Set the number of passengers between 1 and 50 using the for loop
for i in range(1, 51):
   # Set the driving time between 5 and 50 minutes.
   time = randrange(5, 51)
   
   if 5 <= time <= 15:
      print("No {0}. passenger: Driving time {1} minutes".format(i, time))
      count += 1
   else:
      print("No {0}. passenger: Driving time {1} minutes".format(i, time))

# Display the calculation result
print("Total number of passengers: {0}".format(count))
```