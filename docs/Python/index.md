# Getting Started in Python && basic grammar

This is where some of my notes while learning Python, but mostly written afterwards considering I didn't really know how to code before learning Python...

!!! note
    This site is written in kinda hurry, so some part the code might be directly copied from some site without mentioning, which I hope is not considered offensive in the spirit of sharing knowledge.

    But in case you feel uncomfortable about this, email me directly.


# Getting Started

!!! note
    This article is about setting up Python development.

!!! warning
    Some of the document below is copied from `https://www.runoob.com/python3/python3-install.html`, greatly appreciated.

!!! warning
    I would recommend to use `git` along with `github` to manage your Python code.

    Guide Here: `https://www.runoob.com/git/git-install-setup.html`

## Windows Platform

Installing Python on Windows is recommended to be done through the Visual Studio.

!!! note
    This method is recommended because Visual Studio comes with better support when updating Python, also it helps setup environment variables automatically.

Other recommended ways to install Python on Windows are:

1. Through official release on `https://www.python.org/downloads/`
2. Through `winget` command:
    ```
    winget install python
    ```

    !!! note
        `winget` is a command line tool that comes with Windows 10/11, see `https://docs.microsoft.com/zh-cn/windows/package-manager/winget/`

3. Through Windows Store.

    (**Least recommended** due to update and environment variable reasons)

!!! Warning
    Setting up environment variables:

    See article `https://www.runoob.com/python3/python3-install.html`

    You might want to set this **NOW**, otherwise you might run into errors.


## macOS Platform

Recommended way to install Python on macOS is through `homebrew`:

```bash
brew install python
```
!!! note
    `brew` is a package manager for macOS, see `https://brew.sh/`

!!! note
    Installing `git` is the same, simply run `brew install git`.

## Linux Platform

See your Linux distribution's documentation for how to install Python.

Take Ubuntu as an example:

```bash
sudo apt install python3
```

!!! note
    `git` should already be installed on your system, if not, run `sudo apt install git` to install it.


## IDE environments

### Visual Studio Code

!!! note
    `Visual Studio Code` is a powerful IDE for Python development.
    It comes with a lot of features, including syntax highlighting, code completion, and more.
    It is recommended to use it for **ALL** Python development.

You can download it from `https://code.visualstudio.com/download`

!!! note
    `Visual Studio Code` is available as a command line tool, you can run it by typing `code` in your terminal.

    You can also install it through `npm`: `npm install -g code`

### Pycharm

!!! note
    `Pycharm` is great for starters, but it is not recommended for large-scale Python development, mainly because lack of extensions support.

    That is to say, if you want a simple guide-free Python environment setup, you can use `Pycharm` to get started.

    You can download it from `https://www.jetbrains.com/pycharm/download/`

# Basic Grammar

!!! note
    This article is about basic Python grammar.

    For more details, see `https://docs.python.org/3/reference/grammar.html`


## Variable types:

> One should always start with learning the variable types.

In Python, there are six main types of variables:

* `number`: number
* `str`: string
* `list`: list
* `tuple`: tuple
* `set`: set
* `dict`: dictionary

Let's start one by one:

### `number` type

In Python, `number` type is used to represent all kinds of numbers,including `integers`, `floats`, and `complex numbers`, as well as `bool`.

---
#### SubNote I - `type()` and `isinstance()`

!!! note
    In order to find out the type of variable, type `type(variable)` to find out:

```python
>>> type(3.0)
<class 'float'>
```
!!! warning
    Another method to determine what kind of variable is is to use `isinstance()`:

```python
>>> isinstance(3.0,float)
True
```

!!! warning
    There's a difference between `isinstance()` and `type()`:

    However, you won't encounter the problem until you learn `class`.

    For further answers, see [here](about:blank), right now you can consider the following as true:

```python
isinstance(_variable,_type)
# equals to
type(_variable) == _type
```

!!! TODO
    Need to replace the link!

---
#### Basic operations

`number` type has the following arithmetic operations:

* `add`: `+`
* `subtract`: `-`
* `multiply`: `*`

> The three functions above will only return `int` when two `int` are given, otherwise it will return `float`, or `complex`.

* `divide`: `/` (This will return a `float`, even the result is an integer):

```python
>>> 4/2
2.0
```

* `floor division`: `//` (This will return an integer):

```python
>>> 5//3
1
```

* `modulo`: `%` (This will return an integer):

```python
>>> 5%3
2
```

* `power`: `**`

```python
>>> 2**3
8
```

---
#### SubNote II - `type` "conversion" and assigning

!!! Tip
    Python supports assigning two variables at the same time:

```python
a,b=1,2
```

!!! Tip
    Like a scripting language, Python support changing variable types, just assign whatever you want to the variable:

```python
a=1 # a is now an integer
a='hello' # a is now a string
```

!!! error
    Although the example given is legal, **DO NOT USE PYTHON LIKE THAT.**

---
#### Complex type

!!! Tip
    `Complex` type is usually ignored in most getting-started document.

    However, it's something quite interesting and new(?) in computer science.

!!! note
    In Python, the notation for imaginary number is `j`, NOT `i`(in some countries are taught as `i`).

An example:

```python
>>> 1+2j
(1+2j)
```

Arithmetic operations on `complex` type are the "same" as other `number`

!!! note
    `floor division` and `modulo` are not supported in `complex` type, no matter the position.

    This will result in a `TypeError`:

```python
>>> 1//2j
TypeError: unsupported operand type(s) for //: 'int' and 'complex'
```

!!! Tip
    **ALL** arithmetic operations on `complex` type will return `complex` type:

```python
>>> (1.0+4j)+(1.0-4j) 
(2+0j)
>>> (1.0+4j)/(1.0-4j) 
(-0.8823529411764706+0.47058823529411764j)
>>> (5+3j)**(2+3j)
(6.694563360967683+0.585212825721j)
```

Complex numbers have some unique properties:

