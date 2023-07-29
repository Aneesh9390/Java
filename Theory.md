> ref site : https://www.digitalocean.com/community/tutorials/core-java-interview-questions-and-answers

## Important features of Java 8
### Default Interface methods
+ We use "**default method**" in interfaces for extending interfaces (which enables not to write in the classes which implemented it as we will define statements it does too in
interface itself)
+ Suppose there are 2 interfaces which has same default methods, with same or different function statements, then if there is a class which implements both interfaces then,
  + when this class calls the default method the compiler throws error, (as it doesn't know which one to execute), so the implementing class should definitely override (@override) the
  default method in it.
  + E.g
    ```java
    package com.journaldev.java8.defaultmethod;

    public interface Interface1 {

	    void method1(String str);
	
	    default void log(String str){
		    System.out.println("I1 logging::"+str);
	    }
    }

    public interface Interface2 {

	    void method2();
	
	    default void log(String str){
		    System.out.println("I2 logging::"+str);
	    }
    }

    public class MyClass implements Interface1, Interface2 {

	    @Override
	    public void method2() {
	    }

	    @Override
	    public void method1(String str) {
	    }

	    @Override
	    public void log(String str){
		    System.out.println("MyClass logging::"+str);
		    Interface1.print("abc");
	    }
    }
    ```
+ >java.lang.Object
  + Object is the base class for all the java classes.
+ Java interface default methods are also reffered to as **Defender Methods** or **Virtual Extension Methods**

### Dtatic Interface methods
+ Java interface static methods are part of interface, we can't use it for implementation class objects.
+ Java interface static methods helps us in providing security by not allowing implementation classes to override (@override) them.

### Java Functional Interfaces
+ Java, C++, Javascript are called the funtional programming language because we can write functions and use them when required.
```java
Runnable r = new Runnable(){
			@Override
			public void run() {
				System.out.println("My Runnable");
			}};
``` 
+ If you look at the above code, the actual part that is of use is the code inside run() method. Rest all of the code is because of the way java programs are structured. Java 8 Functional Interfaces and Lambda Expressions help us in writing smaller and cleaner code by removing a lot of boiler-plate code.
+ An interface with exactly one abstract method is called Functional Interface.
> @FunctionalInterface

annotation is added so that we can mark an interface as functional interface.

### Java Lambda Expressions
+ Objects are the base of java programming language and we can never have a function without an Object, that’s why Java language provide support for using lambda expressions only with functional interfaces.
+ Lambda Expressions syntax is (argument) -> (body).
+ Now let’s see how we can write above anonymous Runnable using lambda expression.
```java
Runnable r1 = () -> System.out.println("My Runnable");
```
+ what is happening in the lambda expression above :
	+ Runnable is a functional interface, that’s why we can use lambda expression to create it’s instance.
	+ Since run() method takes no argument, our lambda expression also have no argument.
	+ Just like if-else blocks, we can avoid curly braces ({}) since we have a single statement in the method body. For multiple statements, we would have to use curly braces like any other methods.
+ Why do we need Lambda Expression :
	1. Reduced Lines of Code
 	2. Sequential and Parallel Execution Support
  	3. Passing Behaviors into methods
  	4. Higher Efficiency with Laziness
