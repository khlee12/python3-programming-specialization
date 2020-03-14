# 1. Files
Files and CSV output
## file
data stored at a hard disk or other storage that persists over time.

- open(filename, 'r') # open a file and use it for reading
- open(filename, 'w') # open a file and use it for writing
- <file_variable>.read() # get contents to a string
but if file is large, it would be a problem for your computer to handle all of that in memory at once.
- <file_variable>.readline() # get next line of strings
- <file_variable>.readlines() # get list of strings
- <file_variable>.write(<astring>) # add a string to the end of the file
- iterate lines over a file
  ```
  for line in <file_variable>.readlines():
    # do something
  ```
  ```
  for line in <file_variable>:
    # do something
    # python provides a built-in way to iterate through the contents of a file one line at a time,
    # without first reading them all into a list.
  ```

- use with to open files
```
with open('<filename>','r') as md: # == md = open('<filename>', 'r')
  # contents = md.realine() 
  # lines = md.readlines() -> both not be good to use when working with large data. use below↓
  for line in md:
    # do something to read line
  md.write('abc') # write to file
```
Python has the notion of a context manager that automates the process of doing common operations at the start of some task, as well as automating certain operations at the end of some task..

For reading and writing a file, the normal operation is to open the file and assign it to a variable,
and at the end of working with a file the common operation is to make sure that file is closed.

- <file_variable>.close() 

## CSV(Comma Separated Values) output
- parse csv file
1) manually: parse each line, split by comma
2) use Python csv module

- write data to csv file
1) manually: use format string, or join method, or string concatenation
```
olympians = [("John Aalberg", 31, "Cross Country Skiing, 15KM"),
             ("Minna Maarit Aalto", 30, "Sailing"),
             ("Win Valdemar Aaltonen", 54, "Art Competitions"),
             ("Wakako Abe", 18, "Cycling")]
for olympian in olympians:
  row_string = '"{}", "{}", "{}"'.format(olympian[0], olympian[1], olympian[2])
  row_string = '"{}", "{}", "{}"'.format(*olympian) # to print multiple value, should change variable type to tuple
  row_string = '"{}", "{}", "{}"'.format(olympian) # -> "('John Aalberg', 31, 'Cross Country Skiing, 15KM')", "", ""
```

# 2. Dictionaries
Collection of items, unordered, kind of a bag of key-value pairs.
## 1) create dictionary
```
dict = {}
dict['one'] = 'uno
```
## 2) delete key-value pair from dictionary
```
del dict{<key_name>}
```
## 3) reset value of key
```
dict{<key_name>} = <new_value>
```
## 4) number of key-value pairs
```
len(dict)
```
## 5) methods
method | memo
--|--
dict.keys() or list(dict.keys()) | use for loop to iterate every key without any guarantee of order
dict.values() or list(dict.values()) | 
dict.items() or list(dict.items()) | key-value pairs as tuples
if <key_name> in dict | if key exist in dictionary
dict.get(<key_name>) | return value of key, *if key does not exist, returns None*, which is different from simple dict[<key_name>]
dict.get(<key_name>, <value>) | if key exist, return the value, if not exist, use <value> as its value(which is adding key-value pair) and return this <value>
<key_name> in dict | check if key exist

.keys(), .values(), .items() don't return actual lists, they return objects that produce the items one at a time.

## 6) alias and copy
Dictionary is mutable, you need to be aware of aliasing.
```
dict = {'right': 'nothing'}
alias = dict # pointing to the same value(dictionary)
alias['right'] = 'left'
print(dict['right']) # -> changes value of dict
# -> print 'left'

acopy = dict.copy()
acopy['right'] = 'left' # does not change original dict variable
```

# Functions
## defining function
```
'''
def <function_name>(<parameter1, parameter2, ...>):
    # do something
    (return <some_value>)
'''
def hello():
    print("hello world")
hello() # -> function object
```
if we have a function that never executes any return statement at all, function will return special value None.

- Main effect of a function: return values
- Side effect of a function: change a mutable object like a list or a dictionary

## Local and Global Variables
In Python, there was one global or top-level namespace.
Then, each invocation of a function creates a new namespace.

Functions can call other functions, it's called COMPOSITION. You get multiple stack frames. When function executes,
each one has its own namespace and its own local variables.

Variables are local, but objects are not.
```
def double(y):
  y = 2*y

def changeit(lst): -> lst also is a local variable
  lst[0] = 'Michigan'
  lst[1] = 'Wolverines'

y = 5 # variable
double(y)
print(y) # -> print 5, not changed

mylst = ['our', 'students', 'are'] # object
changeit(mylst)
print(mylst) # -> ['Michigan', 'Wolverines', 'are', 'awesome'], changed
# mylst and lst of function, are still two different variables but because they're aliases for the same list,
# mylst has the mutated value -> side affect
```
If functions never ever have side effects, that's a style called functional programming.

When a variable name is used on the left hand side of an assignment statement Python creates a local variable.
When a local variable has the same name as a global variable we say that the local shadows the global. A shadow means that the global variable cannot be accessed by Python because the local variable will be found first. 

If you really want to change the value of a global variable inside a function, you can can do it by explicitly declaring the variable to be global, 
```
def powerof(x,p):
	    global power  # a really...
	    power = p     # ...bad idea, but valid code -> not recommended
	    y = x ** power
	    return y
	
power = 3
result = powerof(10,2)
```
local variable is a temporary variable that is **only known (only exists) in the function** it is defined in.

## Return multiple values
In Python, if a parameter passes a mutable value, it becomes the alias for the original object.
So the mutation to the object inside the function lives on if there is some other variable outside the function that also is an alias for the same list.

- Tuple Packing and Unpacking
tuples, a sequence type that works just like lists except that they are immutable.
```
def info(id):
  return (name, age) # packing
  
n, a = info('0123') # unpacking

def add(x,y):
  return x+y
z = (4,5) # packing
print(add(*z)) # use * to unpack z
print(add(z)) # cause an error, because z was treated as one variable which passed to x, and have nothing pass to y

dict = {}
for key,value in dict.items(): # unpacking into iterator variables:key, value
  # do something
```

You can use the same coding pattern to avoid confusing side effects with sharing of mutable objects. To do that, explicitly make a copy of an object and pass the copy in to the function. Then return the modified copy and reassign it to the original variable if you want to save the changes. The built-in list function, which takes a sequence as a parameter and returns a new list, works to copy an existing list. For dictionaries, you can similarly call the dict function, passing in a dictionary to get a copy of the dictionary back as a return value.

```
1	def changeit(lst):
2	   lst[0] = "Michigan"
3	   lst[1] = "Wolverines"
4	   return lst
5	
6	mylst = ['106', 'students', 'are', 'awesome']
7	newlst = changeit(list(mylst))
8	print(mylst)
9	print(newlst)
```

* Lister loop: it is not known at the beginning of the iteration, how many times the code block needs to be executed, we use listener loop.

## Optional Parameters
```
def f(x, y=3, z=7): # y and z are optional parameters which can be specified or omitted. the formal parameter is bound to a default value. When the optional parameter is included, then the formal parameter is bound to a default value.

    print(x)
    print(y)
    print(z)

f(3)
f(3,5)
f(3,z=5)
f(3,8,1)
```

## Lambda Functions
lambda expression `lambda arguments:expression` yields a function object. This unnamed object behaves just like the function object constructed below.
```
def fname(arguments):
    return expression
```
- when to use lambda VS function?
simple -> lambda, complicated -> function


# Sorting
- sequence_object.sort()
sort inplace, do not return anything. But can not use to immutable sequence such as strings
```
"Apple".sort() -> error
```
- sorted(sequence_object)
do not change the original object, return new sorted object. Also can use to strings.
```
sorted('apple') -> ['a', 'e','l','p','p']
```
USE sorted INSTEAD OF sort

## sorted()
- reverse parameter
```
arr = ['apple', 'peach', 'cherry']
print(sorted(arr, reverse=True))
print(sorted(arr, reverse=False))
```
- key parameter
If you want to sort things in some order other than the "natural" or its reverse, you can provide an additional parameter, the key parameter.
The value of `key` parameter is a function. Using key parameter is passing a function to a function.
```
L1 = [1, 7, 4, -2, 3]

def absolute(x):
    if x >= 0:
        return x
    else:
        return -x

L2 = sorted(L1, key=absolute)
print(L2)

#or in reverse order
print(sorted(L1, reverse=True, key=absolute)) # --> parameter value is a function name/object
# when we pass the function object, it is NOT automatically invoked. 
# Instead, it is just bound to the formal parameter key of the function sorted.
# What the sorted function does is call that key function once for each item in the list.
# Then rearranges the original items in order of the values returned by key function
```
The key parameter provides a function that says *how* to sort them.

- sorting a dictionary
```
d = {'A':2,'B':2,'C':1,'D':4,'E':2,'F':1,'I':2}
y = sorted(d.keys(), key=lambda k:d[k], reverse=True)
y = sorted(d, key=lambda k:d[k])
```

- sorting a tuple
```
fruits = ['peach', 'kiwi', 'apple', 'blueberry', 'papaya', 'mango', 'pear']
new_order = sorted(fruits, key=lambda fruit_name: (len(fruit_name), fruit_name))
```










