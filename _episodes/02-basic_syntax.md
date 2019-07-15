---
title: "Basic syntax"
teaching: 120
exercises: 60
questions:
- "Where do I start?"
objectives:
- "Understand basic Python syntax and data types."
keypoints:
- "Errors are there to help us."
---

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
{: .testimonial}

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


{% include links.md %}
