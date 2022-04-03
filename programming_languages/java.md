# Java Notes

[toc]

## Java Features

- Java is a **platform independent** language.



## Java Basics

Float vs Double

- Difference between float and double is their storage requirement, double is more expensive than float. It takes 8 bytes to store a variable while float just takes 4 bytes.

- It's also worth noting that floating-point numbers or real numbers are `by default double` in Java.

- Both double and float are approximate types, they are not precise.

- You should use logical operator e.g  > or < to compare both float and double variables, instead of = and != because they are not precise.

  ```
  public static final float PIE = 3.14; // compile time error
  
  Use cast
  public static final float PIE = (float) 3.14;
  
  or suffix 'f' or 'F'
  
  public static final float PIE = 3.14f;
  public static final float GRAVITY = 9.8F;
  
  ```

  







## Object Oriented Concepts

### Variable Types

#### 1. Local Variables

- Local variables are declared in methods, constructors, or blocks.
- `Access modifiers` cannot be used for local variables.
- Local variables are visible only within the declared method, constructor, or block.
- Local variables are implemented at stack level internally.
- There is `no default value for local variables`, so local variables should be declared and an initial value should be assigned before the first use.

#### 2. Instance variables

- Instance variables are declared in a class, but **outside a method, constructor or any block**.
- Instance variables have default values. 
    - For numbers -> 0, for Booleans ->  false, and for object references -> null
#### 3. Class/Static variables
- **Class variables** also known as **static variables** are declared with the static keyword in a class, but **outside** a method, constructor or a block.
- **Static variables** are stored in the static memory. It is rare to use **static variables** other than declared final and used as either public or private constants.
- Static variables are rarely used other than being declared as constants. Constants are variables that are declared as **public/private, final, and static**. Constant variables never change from their initial value.



### Constructors

- Every class has a constructor whether it’s a **normal class** or an **abstract class**.
- Like constructors method can also have name same as class name, but still they have 
  return type, though which  we can identify them that they are methods not constructors.
- this() and super() should be the **first statement** in the constructor code. 
  If you don’t mention them, compiler does it for you accordingly.
- Constructor **overloading** is **possible** but **overriding** is **not possible**. 
  Which means we can have overloaded   constructor in our class but we can’t override a constructor.
- Constructors can not be inherited.
- Interfaces do not have constructors.
- Abstract class can have constructor and it gets invoked when a class, which implements 
  interface, is instantiated. (i.e. object creation of concrete class).
- A constructor can also invoke another constructor of the same class – By using this(). 
  If you want to invoke a parameterized constructor then do it like this: this(parameter list).
- If Super class doesn’t have a no-arg(default) constructor then compiler would not insert a default constructor
  in child class as it does in normal scenario.

### Interfaces

- Interface provides full abstraction in java(as none of its methods have body)

- An Interface in java

	- cannot implement other interface.
	- has  all methods by default abstract and public
	- all variables are public, static and final by default

	```
	interface Try{
	   int a = 10;
	   public int a = 10;
	   public static final int a = 10;
	   final int a = 10;
	   static int a = 10;
	}
	
	// All these declarations are equal
	```

	

	- all variables must be initialized at the time of declaration otherwise compiler will throw an error

- A class can implement any number of interfaces

## Maven

- Dependency management
- Build tool

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
Note: Sometimes project coordinates are referred as **GAV Coordinates**(GroupID, ArtifactID, Version)

## Comprehensive Java Guide

### Java Strings
* String is a sequence of characters. But in Java, **string is an object** that represents a sequence of characters. 
* The **java.lang.String** class is used to create a string object.

### Creating a String object

```java
// using 'String Literal'(creating a new object if not exists, else assign a reference of already 
// existing object
String s="welcome";   

Note: String objects are stored in a special memory area known as the "string constant pool".

// using  'new keyword' (new object is created always)
String s=new String("Welcome");  

// using char array
char[] ch = {'j','a','v','a','t','p','o','i','n','t'};  
String s=new String(ch);

```

* **String objects are immutable**
* **Once String object is created its data or state can't be changed but a new String object is created**

### String compare methods
* **Comparing content**
   - **s1.equals(s2)** returns boolean value
   - **s1.equalsIgnoreCase(s2)** return boolean value
   - **s1.compareTo(s2)** compares values lexicographically and returns an integer value
       - s1 == s2  returns 0
       - s1 > s2   returns positive value
       - s1 < s2   returns negative value
* Comparing object reference
   - **s1==s2** return boolean value
   
### String concatenation

  - using **+ (string concatenation) operator**
     - **String s="Sachin"+" Tendulkar";**  returns new String object
  - using **concat() method**
     - **String s3=s1.concat(s2);** returns new String object
** Typical concatenation example**  
```java
class TestStringConcatenation2{  
 public static void main(String args[]){  
   String s=50+30+"Sachin"+40+40;  
   System.out.println(s);  //80Sachin4040  
 }  
}  

Note: After a string literal, all the + will be treated as string concatenation operator.
```
### String substring
```
public class TestSubstring{  
 public static void main(String args[]){  
   String s="SachinTendulkar";  
   System.out.println(s.substring(6));//Tendulkar  
   System.out.println(s.substring(0,6));//Sachin  
 }  
}
```

### String intern method
* A pool of strings, initially empty, is maintained privately by the class String.
* When the intern method is invoked, if the pool already contains a string equal to this String object as determined by the     equals(Object) method, then the string from the pool is returned. Otherwise, this String object is added to the pool and a reference to this String object is returned.

```java
String s=new String("Sachin");  
String s2=s.intern();  
System.out.println(s2);//Sachin  

```

### Common String methods
```java
// 1. UpperCase and LowerCase
String s="Sachin";  
System.out.println(s.toUpperCase());//SACHIN  
System.out.println(s.toLowerCase());//sachin

// 2. trim() method eliminates white spaces before and after string
String s="  Sachin  ";  
System.out.println(s);//  Sachin    
System.out.println(s.trim());//Sachin

// 3. startsWith() and endsWith() method
String s="Sachin";  
System.out.println(s.startsWith("Sa"));//true  
System.out.println(s.endsWith("n"));//true

// 4. charAt() method returns a character at specified index
String s="Sachin";  
System.out.println(s.charAt(0));//S  
System.out.println(s.charAt(3));//h  

// 5. length() method returns length of the string.
String s="Sachin";  
System.out.println(s.length());//6  

// 6. valueOf() method coverts given type such as int, long, float, double, boolean, char 
// and char array into string
int a=10;  
String s=String.valueOf(a);  
System.out.println(s+10); //1010

// 7. replace() method replaces all occurrence of first sequence of character 
// with second sequence of character
String s1="Java is a programming language. Java is a platform. Java is an Island.";    
String replaceString=s1.replace("Java","Kava");//replaces all occurrences of "Java" to "Kava"    
System.out.println(replaceString);  
//Kava is a programming language. Kava is a platform. Kava is an Island.




```




