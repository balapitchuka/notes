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
