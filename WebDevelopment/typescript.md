# Table Of Contents
1. [ null and undefined. ](#null_undefined)
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
