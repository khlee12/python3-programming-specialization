Python is an object-oriented programming language.
```
 some of the programs we have been writing use a procedural programming paradigm. In procedural programming the focus is on writing functions or procedures which operate on data. In object-oriented programming the focus is on the creation of objects which contain both data and functionality together. Usually, each object definition corresponds to some object or concept in the real world and the functions that operate on that object correspond to the ways real-world objects interact.
```
In Python, every value is actually an object. Whether it be a dictionary, a list, or even an integer, they are all objects. Programs manipulate those objects either by performing computation with them or by asking them to perform methods.

# Classes
```
class <classname>:
  ...
```
## constructor
a special method that to initialize Python instances, including instance variables.
```
class Point:
  def __init__(self, param1, param2):
    self.x = param1
    self.y = param2
  ...
```
**self here means instance itself.**

## instance as parameters
```
class Point:
  ...
  def getX(self):
    return self.x
  def distance(self, point2):
    xdiff = point2.getX()-self.getX()
    ydiff = point2.getY()-self.getY()

    dist = math.sqrt(xdiff**2 + ydiff**2)
    return dist
```
use `self` as parameter

## instance variable search order
it first looks inside of the instance, and then it looks inside of the class.

## special methods
1. __init__
constructer
2. __str__
represent how we represent any instance as a string
3. __add__
how to add two instances
4. __sub__
how to substract two instances

## sort lists of instances
define a sort function in a class and pass that function as a `key` of `sorted` function
```
class Fruit():
  def __init__(self, name, price):
    self.name = name
    self.price = price
    
  def sort_priority(self):
    return self.price

L = [
  Fruit('Cherry', 10),
  Fruit('Apple',5)
  Fruit('Blueberry', 20)
]
for f in sorted(L, key=Fruit.sort_priority()):
  print(f.name)
# -> Apple
# -> Cherry
# -> Blueberry
```
or, you can also use lambda function
```
for f in sorted(L, key=lambda x:x.sort_priority()):
  print(f.name)
```
# Class variables
```
class Point:
  pi = 3.14 # -> class variable shared by all instances
  
  def __init__(self, x, y):
    self.x = x # --> instance variable unique to each instance
    self.y = y
```
**good design of the class should use instance variable instead**

# Inheritance
Inherit class can take all of the instance variables, all of the methods that other class has, and then they can add more instance variables and more methods.
```
class Person:
  def __init__(self, name, year_born):
    self.name = name
    self.year_born = year_born

class Student(Person):
  def __init__(self, name, year_born):
    Person.__init__(self, name, year_born)
    self.knowledge = 0
```

Whenever Python is looking for any method or instance variables, it's always
- first, going to look inside of the instance, and it's going to ask does the instance have that thing
- if it doesn't, then it's going to look inside of that instances class and it's going to ask does that instance class have that instance variable or method?
- if it doesn't, then it's going to look into the superclass.










# Testcases

# Exceptions

