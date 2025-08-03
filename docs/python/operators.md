---
title: Operators
description: Python course syllabus.
authors:
  -
    name: Arun kumar N
    avatar: ../assets/image/favicon.png
    description: Creator
update_date : 2025-04-25
published_date : 2025-04-25
tags:
  - python course
hide:
  - navigation
---

Operators are special symbols which help the user to carry out arithmetic operations like addition, subtraction, etc. and logical operations like comparison, `xor`, `not` etc between operands.

The built-in [operator module](https://github.com/python/cpython/blob/3.13/Lib/operator.py title='operator module')[^1] exports a set of functions corresponding to the `intrinsic operators` of Python.  The operator module becomes particularly valuable when you need to pass an operation as an argument to another function, or when aiming for a more functional programming style.

???+ Abstract "Table of Contents"

    [TOC]


## Classification

The operators fall into categories that perform object comparisons, logical operations, mathematical operations and sequence operations.


- Arithmetic Operators
- Assignment Operators
- Comparison Operators
- Logical Operators
- Bitwise Operators
- Special Operators

## Arithmetic Operators

Arithmetic operators are used to perform mathematical operations as listed in the table.

| Operator | Operator Name                       |
| :------: | ----------------------------------- |
|    +     | Addition operator                   |
|    -     | Subtraction operator                |
|    *     | Multiplication operator             |
|    /     | Division operator                   |
|    %     | Modulus operator                    |
|    **    | Exponent operator                   |
|    //    | Floor division operator             |
|    @     | Matrix multiplication operator [^2] |


```python title="python interpreter"

>>> a = 10
>>> b = 3
>>>
>>> # Addition operator : +
>>> a + b
>>> 13
>>>
>>> # Subtraction operator : -
>>> a - b
>>> 7
>>>
>>> # Multiplication operator : *
>>> a * b
>>> 30
>>>
>>> # Division operator : /
>>> a / b
>>> 3.3333333333333335
>>>
>>> # Floor division operator : // (Quotient)
>>> a // b
>>> 3
>>>
>>> # Modulus operator : % (Remainder)
>>> a % b    
>>> 1
>>>
>>> # Exponent operator : **
>>> a ** b
>>> 1000
>>>
```

```python title="Matrix Multiplication operator @"
>>> import numpy as np
>>> matrix_1 = np.array( [ [1, 2], [3, 4] ] )
>>> matrix_2 = np.array( [ [5, 6], [7, 8] ] )
>>> 
>>> matrix_1
array([[1, 2],
       [3, 4]])
>>> matrix_2
array([[5, 6],
       [7, 8]])
>>> 
>>> # Matrix multiplication operator @
>>> matrix_1 @ matrix_2
array([[19, 22],
       [43, 50]])
```

!!! Tip "Operator + as concat"
    Operator `+`  is also used to concat two sequences like string, list, tuple etc..

    Eg:

    ```python title="string"
    >>> course = "Python "
    >>> tag = "Advanced"
    >>> course + tag
    Python Advanced
    ```
    ```python title="list"
    >>> positive_numbers = [1, 3, 5 , 7, 9]
    >>> negative_numbers = [-9, -7, -5, -3, -1, ]
    >>> negative_numbers + positive_numbers
    [-9, -7, -5, -3, -1, 1, 3, 5, 7, 9]
    ```

## Assignment Operators

Equal to `=` sign is used as an assignment operator in python to assign value to a variable. To simplify code and reduce redundancy, python includes arithmetic assignment and bitwise assignment operators.

| Operator | Operator Name                         |
| :------: | ------------------------------------- |
|    =     | Assignment                            |
|          | ^^**Arithmetic Assignment**^^         |
|    +=    | Addition Assignment                   |
|    −=    | Subtraction Assignment                |
|    *=    | Multiplication Assignment             |
|    /=    | Division Assignment                   |
|   **=    | Exponentiation Assignment             |
|   //=    | Floor division Assignment             |
|    %=    | Remainder Assignment                  |
|    @=    | Matrix multiplication Assignment [^2] |
|          | ^^**Bitwise Assignment**^^            |
|    &=    | Binary AND Assignment                 |
|   \|=    | Binary OR Assignment                  |
|    ^=    | Binary XOR Assignment                 |
|    ~=    | Binary Ones Complement  Assignment    |
|   <<=    | Binary Left Shift Assignment          |
|   >>=    | Binary Right Shift Assignment         |


```python title="python interpreter"
>>> a = 5
>>> b = 2
>>> 
>>> # a = a + 3 can be written as a += 3
>>> a += 3 
>>> a
8
>>>
>>> # b = b * 2 can be written as b *= 2
>>> b *= 2
>>> b
4
>>> # similarly for other operators.

```

## Comparison Operators

Comparison of relational operators compares the values. It either returns `True` or `False` according to the condition.

| Operator | Operator Name            |
| :------: | ------------------------ |
|    ==    | Equal to                 |
|    !=    | Not Equal to             |
|    >     | Greater than             |
|    <     | Lesser than              |
|    >=    | Greater than or equal to |
|    <=    | Lesser than or equal to  |

```python title="python interpreter"
>>> a = 5
>>> b = 2
>>> 
>>> a == b 
False
>>>
>>> a != b
True
>>> a > b 
True
>>>
>>> a < b
False
>>>
>>> a >= b
True
>>>
>>> a <= b
False

```

## Logical Operators

Logical operators are used to check whether an expression is True or False. They are used in decision-making.

| Operator | Operator Name |
| :------: | ------------- |
|   and    | Logical AND   |
|    or    | Logical OR    |
|   not    | Logical NOT   |

```python title="Automatic FAN"

temperature = 30
office = "Open"

# AND logic used to check if both the conditions are TRUE
# any one of the condition is false, AND login output will be False
if (set_temperature > 23 ) and (office == "Open"):
    print("Turn On the FAN 𖣘༄")
else:
    print("Turn Off the FAN 𖣘")

```

```python title="python interpreter"
>>> a = True
>>> b = False
>>> 
>>> a and b
False
>>>
>>> a or b
True
>>>
>>> not a
False
>>>
```

???+ Tip "Logic Truth Table"

    - **AND** Logic

    |   a   |   b   | Output |
    | :---: | :---: | :----: |
    | False | False | False  |
    | False | True  | False  |
    | True  | False | False  |
    | True  | True  |  True  |

    - **OR** Logic

    |   a   |   b   | Output |
    | :---: | :---: | :----: |
    | False | False | False  |
    | False | True  |  True  |
    | True  | False |  True  |
    | True  | True  |  True  |

    - **NOT** Logic

    | input | Output |
    | :---: | :----: |
    | False |  True  |
    | True  | False  |

## Bitwise Operator

In Python, bitwise operators are used to performing bitwise calculations on integers. The integers are first converted into binary (BASE 2) and then operations are performed on each bit or corresponding pair of bits, hence the name **bitwise operators**. The result is then returned in decimal (BASE 10) format.

| Operator | Operator Name          |
| :------: | ---------------------- |
|    &     | Binary AND             |
|    \|    | Binary OR              |
|    ^     | Binary XOR             |
|    ~     | Binary Ones Complement |
|    <<    | Binary Left Shift      |
|    >>    | Binary Right Shift     |

```python title="python interpreter"
>>> a = 10  # decimal 10 is equivalent to 1010 (Binary)  
>>> b = 4   # decimal 4 is equivalent to 0100 (Binary)
>>>
>>> a & b  # 0b1010 & 0b0100 = 0b0000  (0)
0
>>> a | b  # 0b1010 | 0b0100 = 0b1110  (14)
14 
```



## Special Operators

Python language offers some special types of operators like the identity operator and the membership operator.

### Identity Operators

`is` and `is not` are the identity operators both are used to check if two values are located on the same part of the memory. Two variables that are equal do not imply that they are identical.

- `is `    :     True if the operands are identical 
- `is not` :     True if the operands are not identical 


```python title="python interpreter"

>>> a = 10
>>> c = 10
>>>
>>> a is c
True
>>>
>>> even = [2, 4, 6, 8]
>>> number = [2, 4, 6, 8]
>>>
>>> even is number
False
>>> even[0] is number[0]
True
>>>

```

### Membership Operators

`in` and `not in` are the membership operators; used to test whether a value or variable is in a sequence.

- `in`   :         True if value is found in the sequence
- `not in`   :     True if value is not found in the sequence

```python title="python interpreter"

>>> name = "Aavishkarah"
>>> 'A' in name
True
>>>
>>> 'z' in name
False
>>>
>>> 'z' not in name
True
>>>

```

[^1]: https://github.com/python/cpython/blob/3.13/Lib/operator.py
[^2]: Added in python version 3.5