# Table Of Contents
1. [ Null and Undefined. ](#null_undefined)
2. [  ](#maven)



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
