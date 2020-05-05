# Nested Data
## list of functions
You can even have a list of functions.
```
def square(x):
  return x*x
L = [square, abs, lambda x:x+1]
```

## JSON
JavaScript Object Notation
*Load*
```
import json
d = json.loads(a_string)
type(d) -> <class 'dict'>
# load string as a dictionary(json)
```
*Dump*
```
json.dump(d, sort_keys=True, indent=2)
# print dictionary as a json format
```

# Nested Iteration
## Copy
- shallow copy
copy a list at the highest level.
```
c_list = original[:]
```
when you shallow copy a nested list, you do not also get copies of the internal lists. 
this means that if you perform a mutation operatiion on one of the original sublists, the copied version will also change.

- deep copy
we can have second-level aliasing.
```
import copy
c_list=copy.deepcopy(original)
```

```
list1 = [['dogs', 'puppies']]
list2 = ['dogs', 'puppies']
c1 = list1[:]
c2 = list2[:] # equals to deep copy
list1[0].append(['cc'])
list1.append(['dd'])
list2.append(['cc'])

print(list1) # [['dogs', 'puppies', ['cc']], ['dd']]
print(c1) # [['dogs', 'puppies', ['cc']]]
# -> 因为是shallow copy，只拷贝最上面的level，相当于c1的第0个元素指向list1的第0个元素。
# 所以在list1本身加元素（['dd']）的时候，它并不会添加。因为它只有一个元素，就是来自于list1的copy
# 但同时c1的第0个元素指向list1的第0个元素，所以第0个元素数组里面加['cc']的时候，c1的第0个元素也会跟着变化
print(list2)
print(c2)
```
<img src='https://github.com/khlee12/python3-programming-specialization/blob/images/images/course3-shallow-copy-and-deep-copy1.png' width="50%" height="50%" />
<img src='https://github.com/khlee12/python3-programming-specialization/blob/images/images/course3-shallow-copy-and-deep-copy2.png' width="60%" height="60%" />

# Map and Filter
## Map
map function makes a new list where each item in the original list is transformed in some way.
A map is a function, it takes a sequence as its second input and it takes a function as its first input.
```
def triple(value):
  return 3*value
new_list = map(triple, a_list)
```
*Note*
Technically, in a proper Python 3 interpreter, the map function produces an “iterator”, 
which is like a list but produces the items as they are needed. 

If you ever really need a list, you can explicitly turn the output of map into a list: `list(map(...))`

## Filter
```
nums = [1,2,3,4,5]
new_seq = filter(lambda num:num%2==0, nums)
# -> new_seq=[2,4]
```
With filter, you pass in a filtration function which takes an item and returns a boolean.
True if the item should be included, False if the item should be filtered out.

# List Comprehensions
- *[<transformer_expression> for <var_name> in <seq> if <filtration_expression>]*
```
things = [2,5,9]
new_list = [value*2 for value in things]
new_list2 = [value*2 for value in things if value%2==0]
```


# Zip
Zip is to step through a pair of lists (or several lists), 
doing something with all of the first items, then something with all of the second items, and so on.

zip also produces "iterator", if you need a list, you can explicitly turn the output of zip into a list: `list(zip(...))`

```
# traverse a 2-d array by column
grid = [[1,2,3],[4,5,6]]
cols = list(map(list, zip(*grid)))

# *grid = [1,2,3] [4,5,6] 
# zip(*grid) = [(3, 1), (4, 2), (5, 3)]
# map(list, zip(*grid)) = [[3, 1], [4, 2], [5, 3]]
# list(map(list, zip(*grid)) = [[3, 1], [4, 2], [5, 3]]
```
# Internet
**URLs**
{protocol}://{server}:{port}/{path}?{arguments}
- protocal: how to communicate with that remote server
- server: where to fetch something from
- arguments: what to fetch from remote server

- **Host(server) names**
host name is a name for the specific computer you're communicating with.

- **IP(Internet Protocol) Addresses**
>> unique identifier
can reuse when the computer disconnects
>> domain names map to IP addresses
domain names are stable, IP addresses not(每次access domain，有可能access不同的server)

- **DNS**
Domain Name System, mapping from domain names to IP addresses.

# REST APIs
- REST
REpresentational State Transfer.
- API
Application Programming Interface
- URL structure for REST APIs
1. the base URL
2. a `?` character
3. one or more key-value pairs, formatted as key=value pairs and separated by the `&` character

## Get response
```
import requests
page = requests.get(<url>)
page.text # contents
page.url # full url
page.json # converts the text into a python list or dictionary
page.status_code
page.headers
page.history # a list of previous responses, if there were redirects.
```
## request a page
```
import requests
base_url = "https://google.com/search"
d = {'q': '"violins and guitars"', 'tbm': 'isch'}
results = requests.get(base_url, params=d)
print(results.url)
# https://google.com/search?q=%22violins+and+guitars%22&tbm=isch
```

