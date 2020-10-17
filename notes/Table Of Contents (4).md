---
title: Table Of Contents
tags: [Import-b418]
created: '2019-11-24T05:21:40.524Z'
modified: '2020-10-17T20:06:53.348Z'
---

# Table Of Contents
1. [ Null and Undefined. ](#null_undefined)
2. [Type annotation and Type inference ](#annotation_inference)



<a name="null_undefined"></a>
### Null and Undefined:
They are intended to mean different things:
* Something hasn't been initialized : **undefined** .
* Something is currently unavailable: **null** .
```
console.log(null == null); // true (of course)
console.log(undefined == undefined); // true (of course)
console.log(null == undefined); // true


console.log(0 == undefined); // false
console.log('' == undefined); // false
console.log(false == undefined); // false

```

<a name="annotation_inference"></a>
### Type annotation and Type inference:
```
  Type annotation : We(developers) tell typescript the type.
  Type inference  : Typescript guesses the type. 
```
