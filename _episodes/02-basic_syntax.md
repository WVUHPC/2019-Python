---
title: "Basic syntax"
teaching: 60
exercises: 120
questions:
- "Where do I start?"
objectives:
- "Understand basic Python syntax and data types."
keypoints:
- "Use Python for: Interactive Scientific Computing"
- "Use Python for: Scripts to automatize straightforward executions"
- "Use Python for: Medium and Large Packages"
- "Use Python for: GUI and Web Applications"

---

## Different ways of using Python

Python is a very flexible language and can be used in ways that in other circunstances will require several different languages and programming environments to produce a similar result.

For this lesson we will be working from Jupyter notebooks and IPython terminals.
It is easier to show and learn the basic syntax from there. Python can also be used for writing scripts, development of large codes with several modules and submodules and even for creating web applications.

Lets have an overview of each one of them:

### Interactive Scientific Computing

In this case, Python works very similar to other environments like Matlab, Maple or Mathematica. You enter commands and they are execute after you click ENTER (IPython Terminal or qtconsole) or after executing SHIFT-ENTER

Lets start with this minimal introduction to python using one of those environments.

We start by using the IPython interpreter for interactive computing.
The most basic use of Python is to use it as a fancy calculator.
It is very easy to do basic math in Python.

```python
print(5 + 1)
```
```
6
```
{: .output}

Note that we don't always have to use the `print()` statement.
Notice how leaving out `print()` gives us the same result as above.

```python
5 + 1
```

```
6
```
{: .output}

During Interactive computing you write your commands, usually as a single line that is executed after hitting enter.

### Python for Scripting

Python is also a good language for writing scripts. Scripts are defined as small (even not so small) pieces of code, normally written on a single file or just very few and indented to execute a relatively straightforward execution.

They are written with a text editor and for Python 3.x should have `#!/usr/bin/env python3` on the first line of the file. Examples:

~~~
#!/usr/bin/env python3

# break operator
# prime numbers

for n in range(2, 1000):
    for x in range(2, n):
        if n % x == 0:
            print(n, 'equals', x, '*', int(n/x))
            break
    else:
        # loop fell through without finding a factor
        print(n, 'is a prime number')
~~~
{: .language-python}

~~~
#!/usr/bin/env python3

def perm(l):
        # Compute the list of all permutations of l
    if len(l) <= 1:
                  return [l]
    r = []  # here is new list with all permutations!
    for i in range(len(l)):
             s = l[:i] + l[i+1:]
             p = perm(s)
             for x in p:
              r.append(l[i:i+1] + x)
    return r

a=[1,2,3,4]

print(perm(a))
~~~
{: .language-python}

If you write this code in a file and make the file Executable

~~~
$ chmod +x permutation.py
$ ./permutation.py
~~~
{: language-bash}
~~~
[[1, 2, 3, 4], [1, 2, 4, 3], [1, 3, 2, 4], [1, 3, 4, 2], [1, 4, 2, 3], [1, 4, 3, 2], [2, 1, 3, 4], [2, 1, 4, 3], [2, 3, 1, 4], [2, 3, 4, 1], [2, 4, 1, 3], [2, 4, 3, 1], [3, 1, 2, 4], [3, 1, 4, 2], [3, 2, 1, 4], [3, 2, 4, 1], [3, 4, 1, 2], [3, 4, 2, 1], [4, 1, 2, 3], [4, 1, 3, 2], [4, 2, 1, 3], [4, 2, 3, 1], [4, 3, 1, 2], [4, 3, 2, 1]]
~~~
{: .output}

Do not worry if you do not understand, all these lines. All that you need to know is that Python Scripts can be written and you can actually convert interactive executions into scripts relatively easy.

Scripts can gain more complexity, start using classes to cluster variables and methods and receive arguments from the command line, for example:

~~~
#!/usr/bin/env python3

import argparse

class MultDivClass:

    def __init__(self, a=0, b=0):
       self.a = a
       self.b = b

    def run(self):
        self._private_product()
        self._private_division()

    # --- private
    def _private_product(self):
        print("The product of %f and %f is %f" % (self.a,self.b,self.a*self.b))

    def _private_division(self):
        if self.b == 0:
            print("Division by zero!")
        else:
            print("The division of %f by %f is %f" % (self.a,self.b,self.a/self.b))

if __name__ == "__main__":
    """
    Command line usage:
    `python -m path.to.my_file -a 12 -b 23`
    """

    parser = argparse.ArgumentParser(description="Computes product and division checking for zeros on denominator")

    parser.add_argument('--a_factor', '-a', help="First factor in product and division", type=float)
    parser.add_argument('--b_factor', '-b', help="Second factor in product and division", type=float)

    args = parser.parse_args()

    run_once = MultDivClass(a=args.a_factor, b=args.b_factor)

    run_once.run()
~~~
{: .language-python}

In this example above, we are not only using classes. But also using argparse that is a module in the Standard Library to read arguments from the command line.

### Python for large developments

For large projects we need to add more structure than provided by simple scripts.

Python offers the option to create packages. Set of Python files organized in folders. The important element here is that each folder must have a file callled `__init__.py`. Python uses that file to check if that folder must be understood as a module.

Consider this structure:

~~~
chemist/
    __init__.py
    utils/
        __init__.py
        periodic.py
        thermo.py
    io/
        __init__.py
        xyz.py
        pdb.py
    md/
      __init__.py
      move.py
      relax.py
~~~
{: .source}

This structure of folders and files is interpreted by Python as as set of modules than can be imported. The purpose of the `__init__.py` files is to include optional initialization code that runs as different levels when the module is imported.

For example `chemist/utils/__init__.py` could be like this:

~~~
# chemist/utils/__init__.py

from . import periodic
from . import thermo
~~~
{: .source}

We will talk about modules and packages later on. This is just an overview of what Python can do.

### Python for Web applications

This is a topic that is beyond the scope of this lesson. But it is good to know that you can use Python also to create web applications. Two popular packages for that are [Python Bottle](https://bottlepy.org/docs/dev/) and [Flask](https://flask.palletsprojects.com/en/1.1.x/)

## Basic Syntax Notebook

Most of these lessons are presented from Jupyter Notebooks. For the basic syntax the notebook is:

~~~
WVU Research Computing (02. Python Syntax).ipynb
~~~

After following the Notebook, you should be ready for the exercises.

## Exercises:

### Playing with your name

Create a variable with your full name. Print your name in several ways.

 * Capitalize your full name
 * Write first your last name in capitals followed by comma and your First name with only the first letter Capitalize (title() function)
 * Write your name backwards
 * Remove all spaces from your full name and write it uppercase
 * Remove all vowels from your name and write the resulting string.

These exercises will invite you to use some of the functions available to strings. Some of them will require to use lists. There are several ways to achieve the result asked.

### Playing with numbers

Create a list with all the numbers from 0 to 999 and start removing all the numbers with these properties.

  * The number is multiple of 7
  * The first character is equal to the last character
  * The number remains the same when written backwards
  * The sum of the first and last digits is equal to the central digit

How many numbers remained?

The purpose of this exercise is to force you to use lists, conditionals and converting integers to strings and back to integers.

### Platonic Solids

There are 5 platonic solids and some of their basic properties are contained in the next table:

| Polyhedrom  | Vertices | Edges | Faces | Schläfli Symbol | Vertex Configuration |
|-------------|----------|-------|-------|-----------------|---------|
| Tetrahedron  |	 4 	| 6 |	4 |	{3, 3} |	3.3.3 |
| Hexahedron (cube) | 8 |	12 |	6 |	{4, 3} |	4.4.4 |
| Octahedron 	 |   6 	| 12 |	8 |	{3, 4} |	3.3.3.3 |
| Dodecahedron | 	20 	| 30 |	12 |	{5, 3} | 	5.5.5 |
| Icosahedron  |	12 	| 30 |	20 |	{3, 5} |	3.3.3.3.3 |

Store all these information in a Python Dictionary.
The Schläfli symbol should be a tuple {p,q}, gives a combinatorial description of the polyhedron.

  * p is the number of edges (or, equivalently, vertices) of each face, and
  * q is the number of faces (or, equivalently, edges) that meet at each vertex.

Use the Python dictionary that you populate to verify two important properties of the number of Vertices (V), Edges (E) and Faces (F)

The first equation states that: (pF = 2E = qV)

<img src="https://latex.codecogs.com/svg.latex?\LARGE&space;pF = 2E = qV" title="pF = 2E = qV" />


and the relation discovered by Euler on the formula (V - E + F = 2):

<img src="https://latex.codecogs.com/svg.latex?\LARGE&space;V - E + F = 2" title="V - E + F = 2" />

Check the correctness of this relations.

<!--
Python can do all of the normal basic math operations you'd expect.

```python
5 + 3
2 - 9
4 * 6
14 / 3
```

```
8
-7
24
4.666666666666667
```
{: .output}

This is a good opportunity to point out that the division between two integers resulting into a float number is one of the several, not many but important that make Python 3 not backward compatible to Python 2.

You can also use it to more complicated operations, like exponentiation (`**`):

```python
5 ** 2
```

```
25
```
{: .output}

Along with floor and remainder division.
Floor division (`//`) gives the results of division, rounded down.
Remainder division (`%`), gives the remainder after division.

```python
5 // 2  # floor division
5 % 2   # remainder division
```

```
2
1
```
{: .output}

Python follows the normal order of operations for math. The so called PEMDAS that stand for  "Parentheses, Exponents, Multiplication and Division, and Addition and Subtraction". This is the most common but not the only notation in existence.

```python
4 + 1 * 6
```

```
10
```
{: .output}

However, if you want Python to change the order it does things in,
you can use parentheses to specify what to do first.
Note that there is no limit to the number of parentheses you can use.

```python
(4 + 1) * 6
```

```
30
```
{: .output}

> ## PEMDAS
>
> In the United States, the acronym PEMDAS is common. It stands for Parentheses, Exponents, Multiplication/Division, Addition/Subtraction. PEMDAS is often expanded to the mnemonic "Please Excuse My Dear Aunt Sally".
>
> Canada and New Zealand use BEDMAS, standing for Brackets, Exponents, Division/Multiplication, Addition/Subtraction.
>
> The parentheses (or brakets) reduces ambiguity in expressions where otherwise will end up in different results.
>
> The PEMDAS is not the only notation in usage. The Reverse Polish notation (RPN), also known as Polish postfix notation or simply postfix notation, is a mathematical notation in which operators follow their operands and it is used in some old computers and calculators.
>
> An advantage of reverse Polish notation is that it removes the need for parentheses that are required by infix notation.
>
>
{: .testimonial}


## Variables

Of course, we will probably want to save our answers at some point.
We can do this by *assigning a variable*.
In Python, a variable is a name for a saved result.
We can set them with the `=` sign.

```python
weight_kg = 55
```


If we want to retrieve the information we've stored,
we can do it by simply typing the name of the variable again.

```python
weight_kg
```

```
55
```
{: .output}

We can perform math on variables the same way we would normally.

```python
print('weight in pounds:', 2.2 * weight_kg)
```

```
weight in pounds: 121.00000000000001
```
{: .output}

As the example above shows, we can print several things at once by separating them with commas.
Note that in this case, the number might appear as 121.00000000000001 due to the way numbers are internally represented in Python.

We can also change a variable’s value by assigning it a new one:

```python
weight_lb = 2.2 * weight_kg
print(weight_lb)
```

```
121.00000000000001
```
{: .output}

What happens when we change a variable?
Let's update `weight_kg` and see what happens to `weight_lb`.

```python
print('weight_kg starting value is', weight_kg)
weight_kg = 10000
print('after updating, weight_kg ending value is', weight_kg)
print('weight in lb ending value is', weight_lb)
```

```
weight_kg starting value is 55
after updating, weight_kg ending value is 10000
weight in lb ending value is 121.00000000000001
```
{: .output}


Notice how even though we changed the value of `weight_kg`, `weight_lb` did not update.
This demonstrates a very important property of programming languages:
a computer will not do anything unless you specifically tell it to - **nothing ever happens automatically**.
This is different from the behavior of a spreadsheets,
where a cell will automatically update when the cells it refers to are updated.

If we want to tell Python to update `weight_lb` to reflect the new value of `weight_kg`,
we will need to perform this operation explicitly.

```python
weight_lb = weight_kg * 2.2
print('new value for weight_lb is', weight_lb)
```

```
new value for weight_lb is 22000.0
```
{: .output}

One more thing to note:
what we just did is the best way to learn Python.
Don't know how something works?
Try it and find out!

> ## Where are variables stored?
> Your computer has two places where it stores information: hard disk and memory.
> What are they and what are they used for?
> Where do variables get stored?
>
> Memory is where temporary information on your computer gets placed.
> It is very fast and easy to access, but has one important drawback:
> data here is erased when your program quits or your computer shuts down.
> All information you save as variables in Python will be stored in memory!
> When programming, we always need to save our data as a file (on our hard disk) if we want to keep it!
>
> Your computer's hard disk is used to store information long-term.
> This is where files get stored, and the information on your hard drive is more or less permanent.
> Hard drives can also store lots of data very cheaply - a terabyte of hard drive space is very cheap, whereas the same amount of memory costs a lot more.
> So if hard drive space is permanent and super-cheap, why don't we use it to store all of our data?
> The biggest reason is speed - memory is typically hundreds, if not thousands of times faster to access.
> If we stored our variables to our hard disk, our programs would be incredibly slow!
{: .callout}

## Errors

Of course, not everything will always work perfectly.
We are going to run into errors.
For instance, what happens if we accidentally don't finish a command?

```python
1 +
```

```
SyntaxError: invalid syntax (<ipython-input-15-70475fc083df, line 1)
  File "<ipython-input-15-70475fc083df", line 1
    1 +
       ^
SyntaxError: invalid syntax
```
{: .error}

This is an error. Errors are good!
When we do something that Python doesn't like, it will give us an error message.
These error messages are called tracebacks, and often tell us exactly how to fix our stuff!

### Let's walk through this error:

```
SyntaxError: invalid syntax
```
{: .error}

All errors have types.
This one is a SyntaxError, indicating, well... an error in our syntax.
Syntax is "computer-speak" for how things are supposed to be typed.
Python only understands certain commands, and typos will mess it up.
If we type a command in such a way that Python can't understand it, we need to fix our syntax
(make sure we've typed a valid command).
**Takeaway message: We made an error when typing things.**

```
File "<ipython-input-15-70475fc083df", line 1
    1 +
       ^
```
{: .error}

Python is trying to be helpful and tell us exactly where our error occured.
The first thing it does is tell us which file had the error in it.
Since we are using the terminal,
it gives us the semi-confusing `<ipython-input-15-70475fc083df` instead of a filename.

The `line 1` bit tells us that our error was on line 1 of our last command.
Specifically, Python has printed out the offending line for us,
and pointed an arrow (`^`) at the bad part.
**Takeaway message: The error came right after we typed the `+` sign.**

## Different types of data

Computers are not smart, and have to be explicitly told how to handle different types of data.
Although a human might know that you can't do math on a word,
our computer does not.
To work around this problem, programming languages store different types of data in different ways.

For reasons that are likely obvious, we will need to store text differently than numbers.
What is less obvious is that Python also has special ways of handling integers vs. decmials,
boolean values (True/False), and a special value used to indicate no data whatsoever.

### Strings

We've already encountered 3 of these "data types" already.
The first is strings, which are used to store text.
Strings are indicated with either single (`'`) or double (`"`) quotes.

To see what data type something is, we can use the `type()` command.
It will print the data type of whatever is inside the parentheses.

```python
type('this is a string')
type("this is also a string")
```

```
str
str
```
{: .output}

We can also make multiline strings with 3 of either set of quotes.

```python
multiline = '''
    This string
    spans
    multiple
    lines
    !!!!
    '''
print(multiline)
type(multiline)
```

```
This string
spans
multiple
lines
!!!!

str
```
{: .output}

Python makes it very easy to work with basic text.
For instance, we can even use the `+` sign to put strings together!

```python
'some text' + 'MORE TEXT'
'repetition' * 3
```

```
'some textMORE TEXT'
'repetitionrepetitionrepetition'
```
{: .output}

Note that math operations on strings will only work within reason.
Attempting to add a string to a number doesn't work!

```python
'5' + 5
```

```
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-41-f9dbf5f0b234 in <module()
---- 1 '5' + 5

TypeError: Can't convert 'int' object to str implicitly
```
{: .error}

This error indicates that Python doesn't know how to convert a string to an integer (without our help)!

### Numbers

Integers are used to store any whole number, either positive or negative.
Any number without a decimal place is an int, or integer.

```python
type(5)
type(-1000)
type(6 + -33)
```

```
int
int
int
```
{: .output}

But what happens when we perform a math operation that would result in a decimal?

```python
type(10 / 3)
```

```
float
```
{: .output}

Any operation that would result in a decimal being created converts the number to a "float".
Floats are used to represent decimals in Python.
To explicitly set a number as a float, just add a decimal point.

```python
type(1.3)
type(22.)
```

```
float
float
```
{: .output}

### Other data types

Python has two special "boolean" values to indicate whether or not something is true or false.
Unsurprisingly, these are defined as `True` and `False`.

```python
type(True)
type(False)
```

```
bool
bool
```
{: .output}

Finally, there is a special value called `None` used to indicate no data.
We will revisit `None` in more detail later, so for now, just be aware it exists.

```python
type(None)
```

```
NoneType
```
{: .output}

> ## Converting between data types
> Data often isn't the format you want it to be.
> For instance, we got an error earlier while attempting to
> perform addition between a string and a number (`'5' + 5`).
> What if we really needed to do that?
> Fortunately, Python makes it rather easy to convert between data types.
> Each data type has a function used to convert another piece of data.
>
> To convert a string to an integer, for instance, we can use the `int()` command:
>
> ```python
> print(int('5') + 5)
> ```
>
> ```
> 10
> ```
> {: .output}
>
> Likewise, we can use the following commands to convert data to other types:
>
> * `str()` - creates a string
> * `int()` - creates an integer
> * `float()` - creates a float
> * `bool()` - creates a boolean
>
> Using this information,
> see if you can fix the left side of these statments to equal the right side of each statement.
> Use only the commands shown above.
>
> ```python
> 1 + '1' == '11'  
> '6' - 7 == -1  
> 7.23 == 7  
> '5' == True  
> 4 / 1.3 == 4  
> ```
{: .challenge}

> ## Data type conversion pitfalls
> You may have noticed something weird when converting a float to an int in the last example.
> Is Python simply rounding floats to the nearest integer, or is it doing something else?
{: .challenge}

-->

{% include links.md %}
