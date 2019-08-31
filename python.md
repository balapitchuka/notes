
## pythonic thinking

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
               
     
```

