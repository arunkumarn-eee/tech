---
title: Identifiers
description: Python course syllabus.
authors:
  -
    name: Arun kumar N
    avatar: ../assets/image/favicon.png
    description: Creator
update_date : 2025-04-06
published_date : 2025-04-06
tags:
  - python course
hide:
  - navigation
---

## Identifiers

Identifier is a user-defined name given to a variable, function, class, module, etc. The identifier is a combination of character digits and an underscore. They are case-sensitive i.e., ‘num’ and ‘Num’ and ‘NUM’ are three different identifiers in python. It is a good programming practice to give meaningful names to identifiers to make the code understandable.

**Rules for Naming Python Identifiers**

- It cannot be a reserved python keyword.
- It should not contain white space.
- It can be a combination of A-Z, a-z, 0-9, or underscore.
- It should start with an alphabet character or an underscore ( _ ).
- It should not contain any special character other than an underscore ( _ ).


| Variables	| ✅ / ❌	| Reason |
|--|--|--|
|city |	✅	| Variable names can be in lower case and uppercase |
| for | ❌	| Reserved key words |
| break	| ❌	| Reserved key words |
| _sum|	✅|	Variable names can begin with _ or a letter|
| user name| 	❌| White space characters are not allowed in the naming of a variable|
| user_name| 	✅ |	Variable names can begin with _ or a letter|
| 2name	| ❌	| Variable names cannot start with a number|
| name2| ✅	| Variable names can begin with _ or a letter|

## Python Keywords 
Keywords in Python are reserved words that can not be used as a variable name, function name, or any other identifier.

Python keywords are the fundamental building blocks of any Python program. Understanding their proper use is key to improving your skills and knowledge of Python.


```python title="list of keywords"
>>> help("keywords")

Here is a list of the Python keywords.  Enter any keyword to get more help.

False               class               from                or
None                continue            global              pass
True                def                 if                  raise
and                 del                 import              return
as                  elif                in                  try
assert              else                is                  while
async               except              lambda              with
await               finally             nonlocal            yield
break               for                 not

```

To know more information about keywords we can use `help()` again by passing in the specific keyword that you need more information about. You can do this, for example,

```
>>> help("if")
The "if" statement
******************

The "if" statement is used for conditional execution:

   if_stmt ::= "if" assignment_expression ":" suite
               ("elif" assignment_expression ":" suite)*
               ["else" ":" suite]

It selects exactly one of the suites by evaluating the expressions one
by one until one is found to be true (see section Boolean operations
for the definition of true and false); then that suite is executed
(and no other part of the "if" statement is executed or evaluated).
If all expressions are false, the suite of the "else" clause, if
present, is executed.

Related help topics: TRUTHVALUE

```
### Keywords can be categorized

- Value Keywords: True, False, None
- Operator Keywords: and, or, not, in, is
- Control Flow Keywords: if, elif, else
- Iteration Keywords: for, while, break, continue, else
- Structure Keywords: def, class, with, as, pass, lambda
- Returning Keywords: return, yield
- Import Keywords: import, from, as
- Exception-Handling Keywords: try, except, raise, finally, else, assert
- Asynchronous Programming Keywords: async, await
- Variable Handling Keywords: del, global, nonlocal.

---

## Variables

A variable is a named area of the computers’ memory that can be used to hold data.

- A variable name can only contain alpha-numeric characters and underscores (A-Z, a-z, 0-9, and _ )
- Variable should not start with a number.
- Python Keywords are not allowed as variable names.
- Variable names are case-sensitive.

### Creating Variable

In Python, variables are created when we assign a value to it. we can assign values to the variable using  assignment operator `=`.

```python title="syntax"

name = "Aavishkarah"
pi = 3.14
connect = True

```

**Multiple assignment**

A single value can be assigned to several variables simultaneously. 

```python title="example"
a = b = c = 1
```

Python allows you to assign different values to multiple variables in one line:

```python title="example"
x, y, z = 2, 5, 6 

# Same as
# x = 2
# y = 5
# z = 6
```