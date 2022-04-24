# C Language Notes

## Pass By Value
```c
void func1(int x) //copy some value to local variable x (of type int)
{
   x = 5; //modify local variable. lost after function call
}

void func2(int *x) //copy some value to local variable x (of type int*)
{
   int a;
   x = &a; //modify local variable. lost after function call.
}


void func3(int *x) //copy some value to local variable x(of type int*)
{
   *x = 10; //x is local but *x is not! change is saved after function call!
}

```

- func1 and func2 are identical. Both modify a local variable. 
- Modification is lost after function is popped off the stack. 
- func3 has ability to change another memory location (a variable which is not local to the function).
- basically, every function call is "call by value". 
- But in the case of a pointer type, we have a way to change the content of a remote address in memory.
- `Pointers are passed by valu`e as anything else. That means the contents of the pointer variable (the address of the object pointed to) is copied. 
- That means that if you change the value of the pointer in the function body, that change will not be reflected in the external pointer that will still point to the old object. But you can change the value of the object pointed to.
- If you want to reflect changes made to the pointer to the external pointer (make it point to something else), you need two levels of indirection (pointer to pointer). When calling functions it's done by putting a & before the name of the pointer. It is the standard C way of doing things.
- When using C++, using references is preferred to pointer (henceforth also to pointer to pointer).
- For the why references should be preferred to pointers, there is several reasons:
  - references introduce less syntaxic noise than pointers in function body
  - references keep more informations than pointers, than can be useful for compiler
- Drawbacks of references are mostly:
  - they break the simple pass-by-value rule of C, what makes understanding the behavior of a function regarding of parameters (will they be changed ?) less obvious. You also need function prototype to be sure. But that is not really worse than the multiple pointer levels necessary when using C.
  - they are not supported by C, that can be a problem when you write code that should work with both C and C++ programs (but that's not the most usual case).
- In the specific case of pointer to pointer, the difference is mostly simplicity, but using reference it may also be easy to remove both levels of pointers and pass only one reference instead of a pointer to pointer.
