# Defold Basic

## 1. Introduction

Defold is a game engine that allows you to create games for mobile devices (and desktop environments).

!!! note
    Platforms that are supported: Windows, Android, iOS, macOS, HTML5, Linux.

Official manuals can be found here:https://defold.com/manuals

## 2. Getting Started

See website: https://defold.com/manuals/introduction/

!!! note
    Setup Defold engine and create a project, then continue reading.

## 3. Lua basic

Lua is kind of unique compared to other languages, I wouldn't recommend Lua for beginners. Hopefully you have another language for reference.

It is lightweight, small, also powerful at the same time. Some of its grammar looks like Javascript(in a way), some looks like Python.

Most feature Lua support are derived from the its C Library, so extensibility is not bad.

Also, Lua is procedure oriented, and use functional programming style.

!!! note
    About Lua, you can find all the information here:

    https://www.lua.org/

Here's something to help you get started with the Lua language.

### 1. Comment style

```lua
-- This is a one-line comment
--[[
    This is a multi-line comment
 --]]
```

### 2. Naming conventions

Naming in Lua is capital-sensitive, and should not start with numbers, the following are examples of legal names:

```lua
mohd         zara      abc     move_name    a_123
myname50     _temp     j       a23b9        retVal
```

### 3. Reserved names

| | | | |
|-|-|-|-|
|and	    |break	|do	    |else|
|elseif	    |end	|false	|for|
|function   |if	    |in	    |local|
|nil	    |not	|or	    |repeat
|return	    |then	|true	|until|
|while||||

!!! warning
    These names are not allowed as variable names or function names.

### 4. Scope

Lua is a dynamic language, so variables are not bound to a scope.

!!! note
    That means all variable are created to be "global", and referencing from a non-existing variable will return nil.(Instead of rasing a error)

Example here:

```lua
> print(b)
nil
> b=10
> print(b)
10
>
```
To delete a variable, use the `=nil` syntax.

```lua
> a=10
> a=nil
> print(a)
nil
```

### 5. Variables types

    - Numbers
    - Strings
    - Booleans
    - Tables
    - Functions
    - Userdata
    - Threads
    - Nil

!!! note
    Like Python, use `type()` to find out the type of a variable.

    Example here:

        type(a) --> nil

#### 5.1 Numbers

In lua, there's no `int` type, all variables are floating point numbers.

All following examples are valid:

```lua
print(type(2))
print(type(2.2))
print(type(0.2))
print(type(2e+1))
print(type(0.2e-1))
print(type(7.8263692594256e-06))
```

#### 5.2. Strings

In Lua, `Strings` are quoted in `"` or `'`, both are valid and equivalent.

```lua
print("Hello World")
print('Hello World')
```

Also, for multi-line string, use `[[]]` instead of `""`.

```lua
print([[
    Hello World
]])
```

!!! warning
    Attempting to run arithmetic operations on a string will **NOT result in an error**.

    Instead, it will try to convert the string into a number

```lua
> print("2" + 6)
8.0
> print("2" + "6")
8.0
> print("2 + 6")
2 + 6
> print("-2e2" * "6")
-1200.0
> print("error" + 1)
stdin:1: attempt to perform arithmetic on a string value
stack traceback:
 stdin:1: in main chunk
    [C]: in ?
```

!!! note
    Then rasing the problem to connect two strings head to tail, use `..` instead of `+`.

        print("2" .. "6") --> 26

!!! Tip
    A unique grammar in Lua to calculate the length of a string is to put `#` in front of the string.

        print(#"Hello World") --> 11

#### 5.3. Booleans

!!! warning
    Boolean type in Lua is a bit different from other languages.

    Pay attention!

There are only two kinds of boolean values: true and false.

**ALL values** except for `false` or `nil` are true**!!!**

```lua
print(type(true))
print(type(false))
print(type(nil))

if false or true then
    print("true")
else
    print("false")
end --> false
```

Number type in Lua cannot directly be used as `0->false` equivalent.

#### 5.4. Tables

Table is the only data structure in Lua.

!!! note
    Table is a collection of key-value pairs.

    Using hash-algorithm make its performance is much better than array.

To create a table, directly use:

```lua
local t = {}
```

or, to construct the table, use；

```lua
local t = {key1 = "value1", key2 = "value2"}
```

Tables in Lua is actually a `associative arrays`, which means it can be accessed by key.

```lua
local t = {key1 = "value1", key2 = "value2"}
print(t.key1) --> value1
print(t.key2) --> value2
```

This means that `Numbers` and `Strings` are both valid keys, and `"10"` and `10` are different keys.

!!! note
    In this way the table can be used as a dict(as in Python) or as a set(as in Java).

    Also you could use it as a array, but it is not recommended.

Notice that there are another way to construct a table, which do not have keys.

```lua
local t = {1, 2, 3, 4, 5}
print(t[1]) --> 1
```

!!! error
    Differ from most programming language, Lua starts counting from 1, not from 0.

`table` do not have a fixed size, so you can add or remove elements from it.

!!! tip
    That means adding or removing a value is the same as global variables.

    Example here:

        t={}
        t[1] = "value1"
        print(t[1]) --> value1
        t[1] = nil
        print(t[1]) --> nil
        print(t[2]) --> nil

    I hope this clears things out.

#### 5.5. Functions

In Lua, `functions` are considered a `first-class value`, that means it could be stored in variables.

```lua
function factorial1(n)
    if n == 0 then
        return 1
    else
        return n * factorial1(n - 1)
    end
end
print(factorial1(5))
factorial2 = factorial1
print(factorial2(5))
```

Functions could be passed through as `anonymous` functions.

```lua
function anonymous(tab, fun)
    for k, v in pairs(tab) do
        print(fun(k, v))
    end
end
tab = { key1 = "val1", key2 = "val2" }
anonymous(tab, function(key, val)
    return key .. " = " .. val
end)
```

#### 5.6. Userdata

Userdata is a way to store a C-like structure in Lua. Not commonly used by starters.

#### 5.7. Threads

In Lua is no thread, but coroutine. Not commonly used by starters.

### 6.