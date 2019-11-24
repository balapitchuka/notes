# Javascript Concepts

## Table Of Contents
- [Javascript Basics](#js-basics)
- [HTTP Request in Javascript ](#ajax)
- [ES6](#es6)
  - [ES6 Arrow Functions ](#es6arrow)





## Javascript basics<a name="js-basics"></a>

### What are javascript loading methods?

<!--  commented image height not possible here
![Javascript loading methods](static/js-loading-methods.png)
-->
<img src="static/js-loading-methods.png" width="500">
<a name="ajax"></a>
Figure : javascript loading methods 



### Basics javascript language rules and best practices:

- Javascript is **case sensitive**.
- Use **camelCase** while writing code.
  - `getElementByTagName();`
  - `var getDuck;`
  - `var aliceTheCamelHasFiveHumps;`

- **Variable names** start with **lowercase letters**
- **Objects and classes names** start with **uppercase letters**
- **Constants** names are all **capital letters**
- End each statement with a semicolon(not neccessary but a good practice)


> **Hoisting** : It is Javascript default behaviour of moving declarations to the top.
> Example : var x;
> **Note** : Initializations are not hoisted. Example var x = 5;





***



## HTTP Request in Javascript
   Making HTTP calls from the client-side wasn’t that easy a decade ago. A front-end developer would have to rely on XMLHttpRequest  which was hard to use and implement. The modern libraries and HTTP clients make the front-end features like user interactions, animations, asynchronous file uploads, etc., easier. 
  
  1. **AJAX** is a set of web development techniques used by client-side frameworks and libraries to make asynchronous HTTP calls to the server.
  2. **JQuery**.
  3. **Fetch API** -- new in ES6 uses promises.
  4. **Axios** -- is an open source library for making HTTP requests and provides many great features.
  5. **HttpModuleClient** -- Angular has its own  HTTP module that works with Angular apps. 
      It uses the RxJS library to handle asynchronous requests and provides many options to perform the HTTP requests.
  6. **SuperAgent** is a lightweight and progressive AJAX library that’s focused more on readability and flexibility.
  7.  **Request** - A Simplified HTTP Client.
      The Request library is one of the simplest ways to make HTTP calls. 
      The structure and   syntax are very similar to that of  how requests are handled in Node.js


***
# ES6<a name="es6"></a>

## ES6 Arrow Functions:<a name="es6arrow"></a>
Many ways to write arrow functions are:
```
// Explicit Return, Multi-Line
a => {
  return a
}


// Explicit Return, Single-Line
a => { return a }


// Implicit Return, Multi-line
a => (
  a
)

// Implicit Return, Single-Line
a => a

// Multiple Parameters, Parentheses Required
(a, b) => a, b
```
#### Implicit vs Explicit Return:
1. When you use the return keyword --  **explicit return** . 
2. arrow functions allow something called **implied return** where the return keyword can be skipped.
###### Example A: Normal Function
```
const sayHi = function(name) {
  return name
}
```
##### Example B: Arrow Function with Explicit Return
```
// Multi-line
const sayHi = (name) => {
  return name
}

// Single-line
const sayHi = (name) => { return name }
```
##### Example C: Arrow Function with Implicit Return
```
// Single-line
const sayHi = (name) => name

// Multi-line
const sayHi = (name) => (
  name
)
```
##### Notes:
- Block body ➡️ return keyword is required  ( block body is where curly braces{} are used).
- Concise body ➡️ return keyword is implied and not needed 
- Parentheses are optional for a SINGLE parameter (here parentheses implies ())

##### Example
```
const me = () => { name: "samantha" };
me(); // undefined 

Note : For a concise body, wrap object literal in parentheses

const me = () => ({ name: "samantha" });
me(); // { name: "samantha" } ✅
```


