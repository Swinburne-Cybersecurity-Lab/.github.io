---
layout:     post
title:      "The Note of Learning Declarative Programming In Chapter One"
subtitle:   " \"HASKELL\""
date:       2019-03-13 11:13:00
author:     "Nastul"
header-img: "img/6FDD355F-D132-4929-98F7-04C1C722EA17.png"
tags:
    - Declarative Programming
---
> “Note.  colon ':'   parentheses '()'  ”
> 
Update -13/03/2019 

This is note from Declarative Programming、 Haskell

## **1.Why Declarative Programming** <br>
**definition:**<br> 
This programming language focuses on the problem you're trying to solve.

Rather than how you get it. you say this is what's the answer look like.   what is to be done rather than how. 

side effect

## **2.Functional Programming** <br>
Functional programming based on the eoncept of an expression.

The basis of functional programming is equational reasoning.

<br>
**List**<br>
Nevertheless, the most frequently used type in Haskell programs is probably the builtin list type.

The notation [] means the empty list, while x:xs means a nonempty list whose head (first element) is represented by the variable x, and whose tail (all the remaining elements) is represented by the variable xs.


`["a","b"] the same as "a":"b":[]`<br>

`len [] = 0<br>`<br>
`len (x:xs) = 1 + len xs<br>`

**Aside: syntax**<br>
    f fa1 fa2 fa3.

Comments start with two minus signs and continue to the end of the line. The names of functions and variables are sequences of letters, numbers and/or underscores that must start with a lower case letter.<br>
Suppose line1 starts in column n, and the following nonblank line, line2, starts in column m. The offside rule says that


**Recursion**<br>


**Expression evaluation**<br>
Follow loop:
- looks for a function call in the current expression,
- searches the list of equations defining the function from the top downwards, looking for a matching equation,
- sets the values of the variables in the matching pattern to the corresponding parts of the actual arguments, and
- replaces the left hand side of the equation with the right hand side.

The loop stops when the current expression contains no function calls, not even calls to such builtin “functions” as addition.<br>
The actual Haskell implementation is more sophisticated than this loop, but the effect it achieves is the same.

**Church-Rosser theorem**<br>


**Referential transparency**<br>
you dont have to know what's around something.





A Single assignment


    let pi = 3.1415 in ...
	len (x:xs) = 1 + len xs


----------

# Part two #

ghci Haskell的解释器

:let 赋值<br>
:load 加载hs 文件<br>
:t type<br>
:set 设置<br>
++ 链接 list

**Function Types**

isEmpty [] = Ture<br>
isEmpty (_:_) = False<br>
( _ is a special pattern that matches anything.)


isEmpty :: [t] -> Bool

isEmpty _ = False<br>

Programmers should declare the type of each function. The syntax for this is similar to the notation printed by ghci: the function name, a double colon, and the type.<br>
Declaring the type of functions is required only by good programming style. The Haskell implementation will infer the types of functions if not declared.



Number types -  Num class


**if-then-else**<br>

--definition A<br>
    iota n = if n == 0 then [] else iota (n-1) ++ [n]

**Guards**<br>

--definition B<br>

	iota n
		| n == 0 =[]
		| n > 0 = iota (n-1) ++ [n]


**Structured definitions**
--definition C<br>

	iota n =
		if n == 0
		then
			[]
		else
			iota (n-1) ++ [n]



**Parametric polymorphism**


**Type definitions**<br>
data Gender = Female | Male<br>
data Role = Staff | Student


| show  |   Eq    |    Ord   |
