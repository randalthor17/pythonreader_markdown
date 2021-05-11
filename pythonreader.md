# Python Reader

# Python Introduction

Python is an extremely popular computer language. Python is general purpose, good for solving many types of problems.

Compared to other languages Python is in the "programmer efficient" niche - allowing the programmer to specify what they want pretty easily, perhaps at the cost of running a little slower or using more memory.

The style of Python is minimal - don't require the programmer to type in a lot words. Mostly get out of the programmer's way. Python is designed to have a consistent style across the language. There is a thematic consistency in how its parts fit together across many situations.

## Open Source

***

Python is distributed for free as open source software. This means many people and organization contribute code to make Python work, and it is free for anyone to use.

The central web site for Python information is python.org. Python was created in 1991 and for many years was run by Guido Van Rossum, who is kind of a rock star for creating such a world-influencing technology.

## Cross Platform

***

Python is cross-platform, meaning a python program developed on Mac OS X, can likely also run on Windows or Linux without any change to the code. When the Python code gets to the part where it, say, it wants to check the mouse location, running on Windows, it uses the Windows-specific mouse facility, and running on the Mac it uses the Mac-specific facility. In this way, the programmer is insulated from many platform-specific details and their code just works.

## Python Version 3

***

We will use Python version 3 in this course. Python version 3 made some changes vs. Python 2.x, in particular changing strings to be unicode, and the print() function to be a function. For the most part, Python 2.x code looks very similar to Python 3.x code. So working in both versions is not a big issue. That said, use of Python 2.x in the world is now dying out.


# Python Style Part 1 - PEP8

Code in Place does not just teach coding. It has always taught how to write clean code with good style. Your section leader will talk with you about the correctness of code, but also pointers for good style.

Messy code works poorly — hard to read, hard to debug. To help you develop the right habits, we want you to always turn in clean code, and of course all of our examples should also have good clean style.

## Readable Code

***

The goal of good style is "readable" code, meaning that when someone sweeps their eye over the code, what that code does shines through.

Experience has shown that readable code is less time consuming to build and debug. Debugging especially can be a huge time-sink, so learning to write clean code and keep it clean is how we will do things all the time. Like surgeons keeping their hands clean, it's the right way to do it and we will try to develop the habit all the time.

### Readability 1 - Function and Variable Names

***

The first step to good readability is a good variable and function names, like this example:

```python
...
url = get_browser_url()
if has_security_problem(url):
    display_alert('That url looks sketchy!')
else:
    html = download_url(url)
    display_html(html)
...
```

The narrative steps the code takes are apparent from the good function and variable names (essentially the verbs and nouns in the narrative). Notice that no other comments are necessary here. The names alone make it very readable.

The functions are the actions in the code, so we prefer verb names like "display_alert" or "remove_url" that say what the function does. Variables are like the nouns of the code, so we prefer names that reflect what that variable stores like "urls" or "original_image" or "resized_image". We'll talk about naming in more detail in the Style 2 document.

### Readability 2 - PEP8 Tactics

***

Python is developed as a collaborative, free and open source project. A "PEP" (Python Enhancement Proposal) is a written proposal used in Python development.

PEP8 is a consensus set of style and formatting rules for writing "standard" style Python, so your code has the right look for anyone else reading or modifying it. This is very much like English spelling reform, where "public" is the standard spelling, and "publick" is out of use and looks weird.

Here are the most important PEP8 rules we will use. The code you turn in should abide by PEP8.

#### Indent 4 Spaces

***

Indent code logically using spaces — 4 spaces is the most common. For if/for/while .. write "body" lines indented on the next line after the colon. Early in the life of Python, some programs used 2 spaces and some used 4 spaces, but 4 spaces has grown to dominate. The best practice is to use literal spaces to indent the code, not tab stops.

```python
if color == 'red':
    color = 'green'
    print(color)
```

#### Single Space Between Items

***

Most lines of code have "operators" mixed in such as as `+ * / = >=`. Use a single space to separate the operators and items:

```python
bound = x * 12 + 13
if x >= 4:
    print(x + 2)
```

#### Space After Comma/Colon

***

A comma or colon has 1 space after it, but no spaces before it.

```python
# e.g.
foo(1, 'hello', 42)  # params to a fn call
[1, 2, 3]            # e.g. list
{'a': 1, 'b': 2}     # e.g. dict
```

#### Use a Consistent Quote Mark

***

Python strings can be written within single quotes like `'Hello'` or double quotes like `"there"`. PEP8 requires a program to pick one quote style and use it consistently. For CS106A, we recommend just using single quote. Single quote is tiny bit easier since it does not require the shift key. Just always use single quote and don' think about it.

#### 2 Blank Lines Before Def

***

PEP8 requires 2 blank lines before each def in a file. This is one of the weaker PEP8 rules. We will not be very upset about your code if it has 3 lines between functions.

#### Blank Lines Within a Def

***

If the lines of code have have natural phases - a few lines setting up the file, a few lines sorting the keys, .. use blank lines within the def to separate these phases from each other, much like diving an essay into paragraphs. The standard says to use blank lines "sparingly".

#### Do Not Write: if x == True

***

The way that boolean True/False is evaluated in an if/while test is a little more complicated than it appears. The simple rule is this: do not write if `x == True` or `if x == False` in an in/while test.

Say we have a print_greeting() function that takes in a "shout_mode" parameter.

Do not write this:

```python
def print_greeting(words, shout_mode):
    if shout_mode == True:   # NO not like this
        print(words.upper())
    else
        print(words)
```

Write it this way:

```python
def print_greeting(words, shout_mode):
    if shout_mode:           # YES like this
        print(words.upper())
    else
        print(words)
```

To invert the logic do not use `== False`. Use `not` like this:

```python
def print_greeting(words, shout_mode):
    if not shout_mode:
        print('Not shouting')
    else
        print(words)
```

#### Remove Pass from Code

***

The `pass` directive in Python is a placeholder line that literally does nothing. It is very rarely used in regular production code. However, in coding exercises, there is often some boilerplate code with a `pass` marking the spot where the student code goes. Remove all the `pass` markers from your code before turning it in.

#### # Inline Comments

***

It's a good practice to add # "inline" comments to explain what especially non-obvious or interesting code does. Inline comments are not needed when the code itself does a good job of showing what the line does.

1. For the following lines, the code does a good job of telling the story, so no inline comments are needed beyond the good variable and function names. Most lines of code are like this.

```python
count += 1
total_len = len(name) + len(address)
```

2. Inline comments are appropriate as in the example below, explaining what a non-obvious line *accomplishes* - addressing the bigger goal picture, not the mechanics of the operators.

```python
# increase i to the next multiple of 10
i = 10 * (i // 10 + 1)
```

See how the inline comment provides useful information that is not obvious from the line itself.

3. Another important use of inline comments to note when the code does not do what it appears to. This speaks to readability - the code does not do what its variable and function names suggest, so we need an inline comment to clear things up.

```python
vendors.add('AT&T')
vendors.add('Stanford University')
vendors.add('T-Mobile')
# Note: We pass 'T-Mobile' here, but for historical
# reasons the payment system re-writes and uses
# 'Vodafone' for this internally.
```

Teaching - example code used in teaching often has more inline comments than regular production code, since for teaching there are many times we want to point out or explain a technique shown on a line.

#### The Misguided PEP8 Rule About ==

***

How do you compare two values in Python? The answer is: use the `==` operator like this:

```python
if word == 'meh':
    print('Enthusiasm low')
```

It works for strings, it works for ints, it works for lists, it works for pretty much everything. Having nailed down that `==` is the simple, correct thing that should come to mind when comparing two things, you may skip the following paragraph.

There is a IMHO misguided suggestion in PEP8: it requires that comparisons to the special value None use the obscure `is` operator instead of `==`. That is a bad idea, since comparing to None is pretty common, but the `is` operator is obscure. In fact it's unusual for a program to have any need for the `is` operator at all. Forcing the mass of regular programs to use this boutique operator most people have never heard of and will never need is not good Python. Therefore, the CS106A position it to just use `==` to compare any two values, which is the simple, intuitive way to think about comparisons.

```python
if val == None:  # CS106A says this is fine
    print('Is nothing sacred?')
```

***

Naming quirks:

#### Python Keywords

***

A few words like `def`, `for`, `and` are fixed "keywords" in Python, so you cannot use those words as variable or function names.

```python
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

#### "len" Rule: Do Not Use Builtin Function as a Variable Name

***

Python has many built-in functions like `len()` and `range()`. As a strange example of Python's flexibility, your code can use assignment `=` to change what `len` means within your code .. probably a huge mistake!

```python
>>> len('hello')   # len function works
5
>>> len = 7        # redefine "len" to be 7, bad idea
>>> len('hello')   # oh noes!
TypeError: 'int' object is not callable
```

Here is the simple rule: do not use the name of a common function as a variable name. Here are the most common function names:

```python
len abs min max int float list str dict range map filter format
```

Rather than memorize the list of all the function names to avoid, it is sufficient avoid using the names of functions that your code uses, typically the well known functions like `len`, `range`, `min`, and so on.

This is why we avoid using "str" or "list" as variable names, instead using "s" and "lst".

Redefining a function in this way only affects your local code, not code elsewhere in the program. So if your code accidentally defines a variable named `divmod`, that will not interfere with other code calling the `divmod()` function.

# Interpreter

You write your Python code in a text file with a name like hello.py. How does that code Run? There is program named "python", and its job is looking at and running your Python code. This type of program is called an "interpreter".

## Running code in the Ed Interpreter

***

Ed has a python interpreter. This allows it to run and execute your python code.

In Lecture 4, we wrote our first Python program: Hello World! To run our code, we need to first open the terminal on Ed. You can find the terminal underneath the code editor. To open the terminal, click the button that says Click here to activate the terminal.

![Terminal_demo](https://codeinplace2021.github.io/pythonreader/img/pythonreader/interpreter/terminal.png)

Now that we've activated our terminal, we are ready to run our program! To run your program, type into the terminal:

`python filename.py`

So, if we wanted to run our Hello World program, we would type: `python helloworld.py`

This tells our interpreter: use python to run our file named `helloword.py`

![Helloworld](https://codeinplace2021.github.io/pythonreader/img/pythonreader/interpreter/terminal2.png)

Voila! After we type `python helloworld.py` into our terminal and hit Enter, we see that the interpreter has printed out "Hello World", exactly what we wanted. Great work!

# Variables

A Python variable represents a little bit of memory, keeping track of a value as the code runs.

A variable is created simply with an "assignment" equal sign = stores a pointer to that value into the variable like this:

```python
x = 42
```

![Variable](https://codeinplace2021.github.io/pythonreader/img/pythonreader/variables/py-var1.png)

Later in the code, appearances of that variable name, e.g. x, retrieve its current value, in this case 42.

Trying to retrieve the value of a variable that does not exist fails with an error (i.e. no = ever assigned that variable).

## Variable Assignment Rules

Here is a more complicated code example and a picture of memory for it, with the variables on the left and their values on the right.

```python
x = 10
y = 'hello'
y = 'bye'
z = y
```

![Variable_assign](https://codeinplace2021.github.io/pythonreader/img/pythonreader/variables/py-var2.png)

Things to notice here...

1. Assignment like `x = 10` above sets a pointer into that variable, pointing to the value.

2. Assignment like `y = 'bye'` above, where the variable has an existing pointer in it, overwrites the existing pointer with the new one. Put another way, a variable holds just one pointer. Assigning a new pointer gets rid of the old one.

3. Assignment between two variables like `z = y` above, makes them point to the same thing. It does not set up a permanent link between the variables; it is simpler than that. This assignment just changes `z` to point to the `y` value at that moment.

4. Small observation 1: each value in Python is tagged with its type, so in the example above the number 10 is tagged with the type "int", and the string `'hello'` is tagged with its type "str".

Garbage Collection Aside: in the above example, the string 'hello' exists in memory at one time, but then the variable `y` is moved to point to something else. When a value such as a 'hello' here is left with no variable pointing to it, it cannot be used any more by the code. Such memory, storing a value that is not used, is called "garbage", and the "garbage collector" facility reclaims that memory, re-using it to hold new values. This is something Python does automatically behind the scenes. Most modern languages have a garbage collection to reclaim memory automatically.

## Variable Swap

Suppose we have two variables and we want to "swap" their values, so each takes on the value of the other. This is a little coding move that all programmers should know.

```python
a = 42
b = 13
```
![Variable_swap_1](https://codeinplace2021.github.io/pythonreader/img/pythonreader/variables/py-varswap1.png)

It might seem that one can begin with `a = b`, but this does not work, since it overwrites and thus loses the original value of `a`. The classic 3-line solution uses a temporary variable named "temp" to hold this value during the swap, like this:

```python
temp = a
a = b
b = temp
```

Starting with the above diagram, you can trace through the three assignments, leading to this memory structure:

![Variable_swap_2](https://codeinplace2021.github.io/pythonreader/img/pythonreader/variables/py-varswap2.png)

## Assignment `=` is Shallow

The swap example demonstrates a key feature of Python assignment — each assignment `=` merely changes what a variable points to. The int, string etc. values are undisturbed. The assignment `=` in Python just moves an arrow around. In the diagram, this changes the arrows on the left, but the values on the right are undisturbed.

We'll revisit this shallow quality of assignment with parameters and nested data structures.
Variable Names are Superficial Labels

Normally variables names are chosen to reflect what data they contain. That said, there is one funny feature of variable names to know.

Consider the following computation

```python
>>> x = 6
>>> y = x + x
>>> y
12
```

Using a couple variables, it computes that doubling 6 makes 12. Suppose instead it was written this way:

```python
>>> alice = 6
>>> bob = alice + alice
>>> bob
12
```

This is exactly the same computation, just using different variable names. What matters in a computation is the structure — which value is used at each spot in the computation. The variable names are just labels on the computation. If we change a variable name consistently throughout the code, the computation will work the same.

That said, though variable names are superficial, good code uses meaningful variable names, reflecting the role of that data in the algorithm.

***

# `print()` and Standard Out

Every running program has a text output area called "standard out", or sometimes just "stdout". The Python print() function takes in python data such as ints and strings, and prints those values to standard out.

![stdout](https://codeinplace2021.github.io/pythonreader/img/pythonreader/print/python-print.png)

To say that standard out is "text" here means a series of lines, where each line is a series of chars with a '\n' newline char marking the end of each line. Standard out is relatively simple. It is a single area of text shared by all the code in a program. Each printed line is appended at its end.

## Standard Out in the Terminal

When you run a program from the terminal, standard out appears right there. Here is example of running the above `hello.py` in the terminal, and whatever it prints appears immediately in the terminal.

```bash
>>> python hello.py
hello there
how are you?
I am fine
```

When using print , you can either use double quotes ("text"), or single quotes ('text')

If your text contains single quotes, you should use double quotes:

 `print("no, you didn't") --> `  **no, you didn't**

If your text contains double quotes, you should use single quotes:

 `print('say "hi" Karel') --> `  **say "hi" Karel**

# `input()` and Standard In

A program that runs in the terminal is called a "console program" (console and terminal are practically synonyms). These console programs can become much more interactive if we learn a way for the user to give us some "input". Python has a simple function for doing so, the aptly named `input` function.

```python
def hello():
    print('hello there')
    user_status = input('how are you? ')
    print('you said: ' + user_status)

def main():
    hello()
```

## Input in the Terminal

Here is example of running the above `hello.py` in the terminal. In this example the text written by the user is in <span style="color:blue">blue</span>.

> $ python hello.py\
> hello there\
> how are you? <span style="color:blue">I am fine</span>\
> you said: I am fine

## Changing variable types

When you call the `input` function, the response entered by the user is given back to you! It is always "returned" as a value of type "str" also known as a string. That is a problem if you want to do any further computation. For example, lets say you wanted to print the value a user entered divided by two. You open up the Python interpreter and run the following code:

```python
>>> x = input('enter a value: ')
enter a value: 42
>>> print(x)
42
>>> print(x/2)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for /: 'str' and 'int'
```

This is subtle, but recall that every variable has a type. Even though x looks like a number, its type is string. Recall that input always returns a string. The interpreter is complaining that it doesn't make sense to divide a string! Now that you know what the issue is, the fix is simple. You just need to change the variable type to be a float or an int. To do so you can use functions called `float` and `int`.

```python
>>> x_float = float(x)
>>> print(x_float/2)
21.0
```

We can call x_float anything we like. I put the term "float" in the name simply so that you can understand the type just by reading the name.

***