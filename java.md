# Table Of Contents
1. [ Constructors. ](#constructors)
2. [ Maven. ](#maven)



<a name="constructors"></a>
## constructors:

1.Every class has a constructor whether it’s a **normal class** or an **abstract class**.

2.Like constructors method can also have name same as class name, but still they have 
  return type, though which  we can identify them that they are methods not constructors.
  
3.this() and super() should be the **first statement** in the constructor code. 
  If you don’t mention them, compiler does it for you accordingly.
  
4.Constructor **overloading** is **possible** but **overriding** is **not possible**. 
  Which means we can have overloaded   constructor in our class but we can’t override a constructor.
  
5.Constructors can not be inherited.

6.Interfaces do not have constructors.

7.Abstract class can have constructor and it gets invoked when a class, which implements 
  interface, is instantiated. (i.e. object creation of concrete class).
  
8.A constructor can also invoke another constructor of the same class – By using this(). 
  If you want to invoke a parameterized constructor then do it like this: this(parameter list).
  
9.If Super class doesn’t have a no-arg(default) constructor then compiler would not insert a default constructor
  in child class as it does in normal scenario.

<a name="maven"></a>
## Maven
- dependency management
- build tool

### Project Coordinates
1. Project Coordinates uniquely identify a project.
2. Similar to GPS coordinates for your house:  latitude/longitude.
3. Similar to Precise information for finding your house (city , street, house #)
```
Example Analogy:

<groupId>com.bala.reservations</groupId>   -- city
<artifactId>reservations</artifactId>      -- street
<version>0.0.1-SNAPSHOT</version>          -- house number

In general, the usage is as follows:

Groupd ID    -- Name of company, group or organisation(convention to use reverse domain name as com.luv2code)
Artifact ID  -- Name of project 
Version      -- A specific release version like : 1.0, 1.6, 2.0
                If project is under active developement then : 1.0-SNAPSHOT

```
#### Note: Sometimes project coordinates are referred as GAV(GroupID, ArtifactID, Version)


## Variable Types:
1. Local variables:
- Local variables are declared in methods, constructors, or blocks.
- Access modifiers cannot be used for local variables.
- Local variables are visible only within the declared method, constructor, or block.
- Local variables are implemented at stack level internally.
- There is no default value for local variables, so local variables should be declared and an initial value should be assigned before the first use.

2. Instance variables:
- Instance variables are declared in a class, but **outside a method, constructor or any block**.
- Instance variables have default values. 
    - For numbers -> 0, for Booleans ->  false, and for object references -> null
3. Class/Static variables:
- **Class variables** also known as **static variables** are declared with the static keyword in a class, but **outside** a method, constructor or a block.
- **Static variables** are stored in the static memory. It is rare to use **static variables** other than declared final and used as either public or private constants.
- Static variables are rarely used other than being declared as constants. Constants are variables that are declared as **public/private, final, and static**. Constant variables never change from their initial value.

