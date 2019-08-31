# Table of Contents
1. [Example](#example)
2. [Example2](#example2)
3. [Third Example](#third-example)
4. [Fourth Example](#fourth-examplehttpwwwfourthexamplecom)


## Example
## Example2
## Third Example
## [Fourth Example](http://www.fourthexample.com) 


## Pythonic Thinking

item1 : know which version of python you're using:
```
      python --version
      python3 --version 
      
      Also we can find versions at runtime as follows:
          import sys
          print(sys.version_info)
          print(sys.version)
          
```

item2 : Follow the PEP8 style guide:
 
 
item3 : Know the difference between 'bytes', 'str', and 'unicode' :


item4: Write Helper Functions Instead of Complex Expressions:


item5: Know How to Slice Sequences:
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
               
               
4. The result of list slicing is a whole new list. Modifying the result of slicing won't affect the original list. References to the objects from the original list are maintained.
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

