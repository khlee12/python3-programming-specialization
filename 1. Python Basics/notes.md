- [1. Programming in Python]()
- [2. Turtle Graphics]()
- [3. The Way of the Programmer]()

programming is giving a list of instructions for a computer to follow. In the contest of programming, this instructions are sometimes called algorithms. 
Difference between Interpreter and Compiler

## 1. Programming in Python
### Values and Data Types
A Value is one of the fundamental things - like a word or a number- that a program manipulates.
code = expression
every expression has value, every value has type
100 -> 100 -> Integer
```
100 -> python interpreter calculates the value
3.14
```
when you want to some output, use print statement to print instance
Data Types:
- Integer
- Float
- String

### Operators and Operands
Use Operators to combine expressions.
- +
- -
- *
- /
- %
- //
```
9//5 -> 1 (produce int result)
9.0//5.0 -> 1.0 (produce float result)
9.0//5 -> 1.0 (produce float result)
```
- **
the same as `//` example above
- +=
- -=

Precedence of Operators
Parentheses > Exponentiation(`**`) > Multiplication/Division(`*, /, //, %`) > Addition/Subtraction(`+, -`) > relational(`==, !=, <, <=, >, >=`)> logical (`not`) > logical(`and`) > logical(`or`)
operators with the same precedence are evaluated from left-to-right, except exponentiation operator `**`.
```
2**3**2 # when there's no parentheses and the operator priority level are the same, 
        # the right-most ** operator gets done first
```

- index operator
An index specifies a member of an ordered collection
indexing allows us to access a specific element of the sequence.
[i] ,i refers to the index from 0 to length of string or list, from left to right,
or index from -1 which is the rightmost index, from right to left.

*memo: For indexing from right to left, it might seem natural to do the analgous thing and start at -0. Unfortunately, -0 is the same as 0, so s[-0] can’t be the last item. 

[] can be used in 1) creating a list, 2) indexing.
indexing requires referencing an already created list while simply creating a list does not.

- slice operator
multiple choice of an ordered collection.
[i:j], elements from i-th element to j-1-th element
[i:], everything from i-th element
[:j], everything from start to j-1-th element
[:], select everything of an ordered collection

relational operator
- ==
- !=
- <
- <=
- >
- >=
logical operator
- and
- or
- not
-----
- in
- not in (returns the logical opposite result of `in`)


### Function Calls
One type of expression: Function call expression.
Function: take inputs, and does some work, then return the value
<name_of_the_functions>(<input_1>[, <input_2>, <input_3>...])
sub(x,2)
1. evaluates function itself (look up the variable sub to get the function object)
2. evaluates each arguments from left to right (look up variable x to get 1)
3. After knows what functions calling, and what the value of every argument is, 
call the function, and return the value

function is also an object.

### Data Types
use `type()` to see what is the type of given value is
```
type('This is a string') -> '' can create strings with double quotation " inside
type("This is a string") -> "" can create strings with single quotation ' inside
type('''This is a string''') -> '''''' can create strings with double quotation " and single quotation ' inside
type("""This is a string""") -> """""" can create strings even span multiple lines
-> return <class'str'>

# Though create strings 4 different ways, but all of them are strings.
```

### Type Conversion
- int()
- float()
- str()

### Variables
variables to store expression value
<variable_name>=<value>
every variable has its name and value
variable_name: 1) start with a letter or underscore 2) can only contain letters & numbers & underscore 3) not using Python Keywords
* python treats underscore `_` as a character, so you can use at variable names

variable functionality
1) remember an expression value (can use later)
2) give a nice name to the value of an expression (more human readable)
When reading or writing code, say to yourself “n is assigned 17” or “n gets the value 17” or 
“n is a reference to the object 17” or “n refers to the object 17”. Don’t say “n equals 17”.

Unlike Jara or C++, Variables in Python do not have types, values do.
That means that it is acceptable in Python to have a variable name refer to an integer and 
later have the same variable name refer to a string.

```
x = 15
y = x -> at this moment, x and y are pointing at the same object, so they appears to be equal, because they point to the same value
x = 22
-> x=22 and y=15
```
### Statements and Expressions
statement is a complete instruction that the Python program executes.

### Updating Variables
x=x+1
evaluate x+1 first then assign to x.

*reassignments*
before you update variables, you have to initialize it.
update with incretment, decretment

### Hard-Coding
Don't hard code your answer

### Input
- input(): asks user to input something
input always return a string.



## 2. Turtle Graphics

### Objects and Turtle Graphcs
To understand the use of loops as a way of repeating actions
To understand flow control and iteration through the for loop
To understand the idea of sequence (or list) of numbers
To introduce the idea of looking for patterns when problem solving
To distinguish between instances, attributes, and methods

### First Turtle Program
An Object have
- various of methods: things they can do
- various of attributes(properties): states to describe them

import statement loads module. We can use Types that module brings using module.<Type1>

Attributes do not need to be pre-declared; any code can add a new attribute to an instance just by assigning a value to it.

### Instances: A Herd of Turtles
We can have more than one instance of a class.

Object-Oriented Concepts
- User defined class
- instances
- Attributes(Instance variables)
- Methods

The only difference between a method invocation and other function calls is that the object instance itself is also passed as a parameter. 
Thus alex.forward(50) moves alex, while tess.forward(50) moves tess.

### Repetition with a For Loop
for loop with `range` function:  specify how many times the contents inside of the for loop will execute.
enumerate..

### More Turtle Methods

### Importing Modules
some functions are already in Python core: such as len(). They are part of a standard library of modules.
A module is a code file that defines some functions that can be used by other programs.
Before you can invoke a function that's from a standard library module, 
you need to tell the Python interpreter to make it available and that's what the import statement does.

```
import random -> make random module available
random.random() -> use random. to refer random module every time

from random import random, randrange
random()
put the function directory into the namespace, so we don't have to keep referring to the module they came from
```

import module syntax
- `import morecode`: import everything in morecode.py
- `import morecode as mc`: give the imported module an alias
- `from morecode import function1`: import SOME of the functionality from a module.

```
import turtle
t = turtle.Turtle() # from the turtle module, find Turtle Class
```

### Conclusion

## 3. The Way of the Programmer

### Introduction Debugging
objective:
distinguish three types of errors:
- Syntax errors,
- Runtime errors,
- Semantic errors

### Syntax, Runtime, and Semantic Errors
syntax error: python interpreter can not parse it
runtime error: interpreter can parse it, but during the running of the program, some illegal operation happens
semantic error: program was able to run all the way to completion, but produce the wrong thing

## Week2
- identify whether object is mutable or immutable
- recognize if the method is mutate original object or make a copy of it

Lists can be changed(or mutated) while strings are immutable

```
x = 1+2+3 is a statement
1+2+3 is an expression
```

Expressions: (expression has value and type)
- literal expression
- variable names
- function calls
 - type function
   - type()
 - type conversion function
   - int()
   - float()
   - str()
- operators 
  - add two numbers
  - ...
* Use Operators to combine expressions
- input expression
  - input()
- boolean expression 
expression that evaluates to a boolean value.
1) literal expression (True)
2) comparison expression　(a==b)
3) logical expression (a and b)
4) in & not in

Statements
- assignment statement
- reassignment statement
  - increment
  - decrement
- while statement
- for statement (see iteration part of sequences)
do some lines for multiple times(iteration)
- if statement(conditional execution)


- import statement
- print statement




Instances




Data Structure and Algorithms
Data Structure
0) build-in primitive (or atomic) data types
int
str
bool

1) Sequences (an ordered collection)
- String
sequential collections of characters.
- Lists
sequential collection of Python data values. elements of a list can have any type and for any one list.
Only item that can added to list, is a list.

- Tuples
like a list, is a sequence of items of any type. 
Key difference between lists and tuple is that a tuple is immutable.

- related operations:
1) len()
2) indexing
3) slicing
4) concatenation
use `+` operator concat two sequence items which have the same data type.
after concatenation, you will get a *new list*, (not a list with two sublists)
memo: do not adding different types together.
5) repetition
use `*` operator repeats the items in a list for a given number of times
```
arr = [0] * 4
```
6) count()
find out how many times an element appears in the ordered collection(stings/lists)
```
<strings/lists>.count(<element_want_to_count>)
```
7) index()
finds where an item is. returns the *leftmost* index where the argument is found.
if the item does not exist in the ordered collections, index() would return *error*.
```
<strings/lists>.count(<element_want_to_find>)
```
8) split()
take a string input, split string into words by space(if no argument), and return a list.
if there's an argument(or delimiter), it specifies what we actually want to split along.
```
<strings>.split()
```
9) join()
use seperator to join the list with the glue between each of the elements.
```
<glue_word or seperator>.join(<lists>)
```

10) iteration
  - for statement
  ```
  for <loop_var_name> in <sequence>:
    # do something
  ```
  - accumulator pattern (accumulate value using accumulator variable)
  ```
  1) initialization accumulator
  2) iterating:
    3) updating accumulator
  ```
  - range function
  ```
  range(5) produces a sequence: [0,1,2,3,4] # rangefunction returns an object that acts like the list.
  use list() to cast to a real list
  ```
  ```
  for i in range(5):
    # do something
  ```
  - enumerate function
*items are produced as needed rather than all produced in advance.

Collections
- HashTable
- Set
...

Algorithms
Sequence Mutation
