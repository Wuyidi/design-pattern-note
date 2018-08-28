## Singleton Pattern (1)

### Intent

> Ensure a class only has one instance, and provide a global point of access to it.



### Explanation

#### Real world example

It's important for some classes to have exactly one instance. There should be only one file system and one window manager. An accounting system will be dedicated to serving one company.



#### Structure
![Singleton Structure](./Images/SingletonStructure.svg)



#### Programmatic code sample

Joshua Bloch, Effective Java 2nd Edition p.18

>A single-element enum type is the best way to implement a singleton

```java
public enum Maze {
  // Enum instances/values should be declared first.
  // Use INSTANCE(arg1, ..) if constructor accepts agruments.
  INSTANCE;
  
  // Constructor can accept arguments as well.
  private Maze() {
  }
}
```

Usage:

```java
Maze foo = Maze.INSTANCE;
```



Lazy initialization

```java
public class Singleton {
	private static Singleton singleton = null;
    public static Singleton getInstance(){
    	if(singleton == null){
			synchronized(Singleton.class){
				if(singleton == null){
					singleton = new Singleton();
				}
			}
		}
		return singleton;
    }	
} 
```



Initialization on Demand Holder (IoDH)

```java
class Singleton {
  private Singleton() {
  }
  
  private static class HolderClass {
    private final static Singleton instance = new Singleton();
  }
  
  public static Singleton getInstance() {
    return HolderClass.instance;
  }
}
```



### Applicability

Use the singleton pattern when

* there must be exactly one instance of a class, and it must be accessible to clients from a well-known access point

* when the sole instance should be extensible by subclassing, and clients should be able to use an extended instance without modifying their code

  ​

### Typical Use Case

- the logging class
- managing a connection to a database
- file manager





### Real world examples

- [java.lang.Runtime#getRuntime()](http://docs.oracle.com/javase/8/docs/api/java/lang/Runtime.html#getRuntime%28%29)
- [java.awt.Desktop#getDesktop()](http://docs.oracle.com/javase/8/docs/api/java/awt/Desktop.html#getDesktop--)
- [java.lang.System#getSecurityManager()](http://docs.oracle.com/javase/8/docs/api/java/lang/System.html#getSecurityManager--)




### Consequence

* Violates Single Responsibility Principle (SRP) by controlling their own creation and lifecycle.
* Encourages using a global shared instance which prevents an object and resources used by this object from being deallocated.
* Creates tightly coupled code. The clients of the Singleton become difficult to test.
  * Singletons can hide dependencies. One of the features of an efficient system architecture is minimizing dependencies between classes. This will in turn help you while conducting unit tests and while isolating any part of the program to a separate assembly. A singleton will make you sacrifice this feature in your application. Since the object creation part is invisible to us, we cannot expect the singleton constructor to accept any parameters. This setback may look unimportant on the first glance but as the software complexity increases, it will limit the flexibility of the program.
* Singleton classes cannot be subclassed.

