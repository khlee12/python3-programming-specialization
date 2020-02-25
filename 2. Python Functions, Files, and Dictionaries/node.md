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

def changeit(lst):
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

## Return multiple values
-> Tuple Packing and Unpacking
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
for key,value in dict.items(): # key, value are unpacking
  # do something
```




