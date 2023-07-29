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
+ Java, C++, Javascript are called the funtional programming language because we can write functions and use them when required.

### J
