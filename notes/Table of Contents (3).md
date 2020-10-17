---
title: Table of Contents
tags: [Import-b418]
created: '2019-11-24T05:21:40.522Z'
modified: '2020-10-17T20:06:51.488Z'
---

# Table of Contents
1. [Pythonic Thinking](#Pythonic-Thinking)
2. [Example2](#example2)
3. [Third Example](#third-example)
4. [Fourth Example](#fourth-examplehttpwwwfourthexamplecom)


## Example
## Example2
## Third Example
## [Fourth Example](http://www.fourthexample.com) 





## Pythonic-Thinking

#### Item1 : Know the version of python you're using:
```
      python --version
      python3 --version 
      
      Also we can find versions at runtime as follows:
          import sys
          print(sys.version_info)
          print(sys.version)
          
```

#### Item2 : Follow the PEP8 style guide:
 
 
#### Item3 : Know the difference between 'bytes', 'str', and 'unicode' :


#### Item4: Write Helper Functions Instead of Complex Expressions:


#### Item5: Know How to Slice Sequences:
```
1. slicing syntax :  somelist[start:end]
2. avoid using start of list, end of list to reduce visual noise.
          
       eg: 
               assert a[:5] == a[0:5]
               assert a[5:] == a[5:len(a)]
               
3. slicing deals properly with start and end indexes that are beyond the boundaries of list.

      eg:
                a = ['a', 'b', 'c', 'd' ,'e', 'f' , 'g' ]
                first_twenty_items = a[:20]    # this will not throw error
                last_twenty_items = a[-20:]    # this also will not throw error
                
                but a[20] will throw 'IndeError'
               
               
4. The result of list slicing is a whole new list. Modifying the result of slicing won't affect the 
    original list. References to the objects from the original list are maintained.
      eg:
            b = a[4:]
            print("before: ", b)
            b[1] = 99
            print("after: ", b)
            print("no change in a: ", a)
            
5. when used in assignments, slices will replace the specified range in the original list.

     eg:
          print("before ", a)
          a[2:7] = [99, 34, 33]      # this is ok unlike tuple assignments x, y = c[:2]
          print("after ", a)

6. if you leave out both start and end index when slicing, we get a copy of original list.
   
       eg: 
           b = a[:]
           assert b == a and b is not a

7.  
```
#### Item6: Avoid using start, end, and stride in a single slice

#### Item7: Use List comprehensions instead of map and filter.


#### Item8: Avoid more than two expressions in  list comprehensions.

#### Item9: Consider Generator expressions for large comprehensions.

#### Item10: Prefer enumerate over range
```
colors = ['red', 'black', 'orange', 'yellow']
for colr in colors:
    print(colr)

for colr_i in range(len(colors)):
    print("%d: %s"%(colr_i, colors[colr_i])
    
for index, colr in enumerate(colors):
    print("%d: %s"%(colr_i, colors[colr_i])
    
# we can also add number from which enumerate should begin counting from 
   
for index, colr in enumerate(colors, 2):
    print("%d: %s"%(colr_i, colors[colr_i])
```

#### Item11: Use zip to process Iterators in parallel



#### Item12: Avoid else blocks after for and while loops
```

```

#### Item13: Take advantage of each block in try/except/else/finally

# Functions
