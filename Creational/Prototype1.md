## Prototype (1)

### Intent

> Specify the kinds of objects to create using a prototypical instance, and create new objects by copying this prototype.



### Motivation

Today’s programming is all about costs. Saving is a big issue when it comes to using computer resources, so programmers are doing their best to find ways of improving the performance When we talk about object creation we can find a better way to have new objects: cloning. To this idea one particular design pattern is related: rather than creation it uses cloning. If the cost of creating a new object is large and creation is resource intensive, we clone the object.

The Prototype design pattern is the one in question. It allows an object to create customized objects without knowing their class or any details of how to create them. Up to this point it sounds a lot like the Factory Method pattern, the difference being the fact that for the Factory the palette of prototypical objects never contains more than one object.

### Explanation

#### Structure

![Prototype](./Images/Prototype.svg)

- **Client** - creates a new object by asking a prototype to clone itself
- **Prototype** - declares an interface for cloning itself.
- **ConcretePrototype** - implements the operation for cloning itself.

#### Programmatic code sample

```java
public interface Prototype {
	public abstract Object clone ( );
}

public class ConcretePrototype implements Prototype { 
	public Prototype clone() {
		return super.clone();
	}
}

public class Client {

	public static void main( String arg[] ) 
	{
		ConcretePrototype obj1= new ConcretePrototype ();
		ConcretePrototype obj2 = (ConcretePrototype)obj1.clone();
	}

}
```

#### Copying object in Java

**clone**() is a **method** in the **Java** programming language for **object** duplication. In **java**, objects are manipulated through reference variables, and there is no operator for copying an **object**—the assignment operator duplicates the reference, not the **object**. The **clone**() **method provides** this missing functionality.

```java
class Prototype implements Cloneable { 
  @Override
  public Prototype clone() {
   	Object obj = null;
    try {
      obj = super.clone();
    } catch (CloneNotSupportedException e) {
      e.printStackTrace();
    }
    return (Prototype)obj;
  } 
}
```
