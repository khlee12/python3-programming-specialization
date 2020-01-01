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

Parentheses > Exponentiation > Multiplication/Division > Addition/Subtraction
operators with the same precedence are evaluated from left-to-right, except exponentiation operator `**`.
```
2**3**2 # when there's no parentheses and the operator priority level are the same, 
        # the right-most ** operator gets done first
```
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

### First Turtle Program

### Instances: A Herd of Turtles

### Repetition with a For Loop

### More Turtle Methods

### Importing Modules

### Conclusion

## 3. The Way of the Programmer

### Introduction Debugging

### Syntax, Runtime, and Semantic Errors

### Know Your Error Messages

### Incremental Programming

### Common Errors

### Conclusion Debuging




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

Statements
- assignment statement
- reassignment statement
  - increment
  - decrement
- while statement
- for statement
- if statement
- import statement
- print statement
  



Data Structure and Algorithms
Data Structure
- Array
- HashTable
- Set
...

Algorithms
- Loop
