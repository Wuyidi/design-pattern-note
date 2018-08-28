## Factory Method (2)

### Explanation

#### Structure

![Factory Method](./Images/FactoryMethod.svg)



BlackSmith subclasses redefine an abstract manufacture operation on BlackSmith to return the appropriate Weapon subclass. Once an BlackSmith subclass is instantiated, it can then instantiate specific weapon without knowing their class. We call manufactureWeapon a factory method because it's responsible for "manufacturing" an object.

#### Programmatic code sample

```java
public interface BlackSmith {
  public Weapon manufactureWeapon(WeaponType type);
}

public class ElfBlackSmith implements BlackSmith {
  @Override
  public Weapon manufactureWeapon(WeaponType type) {
    return new ElvishWeapon(type);
  }
}

public class OrcBlackSmith {
  @Override
  public Weapon manufactureWeapon(WeaponType type) {
    return new OrcishWeapon(type);
  }
}
```

Now as the customers come the correct type of blacksmith is summoned and requested weapons are manufactured

```java
Blacksmith blacksmith = new ElfBlacksmith();
blacksmith.manufactureWeapon(WeaponType.SPEAR);
blacksmith.manufactureWeapon(WeaponType.AXE);
// Elvish weapons are created
```

How to hide factory method followed by an example

![LoggerDiagram](./Images/LoggerDiagram.svg)

```java
public abstract class LoggerFactory {
  public void writeLog() {  
        Logger logger = this.createLogger();  
        logger.writeLog();  
    }  
  public abstract Logger createLogger();
}

public class FileLoggerFactory extends LoggerFactory {
  @Override
  public Logger createLogger() {
    Logger logger = new FileLogger();
    return logger;
  }
}
```

Create an utility class

```java
import javax.xml.parsers.*;  
import org.w3c.dom.*;  
import org.xml.sax.SAXException;  
import java.io.*;  

public class XMLUtil {  
// Extract class name from xml config
    public static Object getBean() {  
        try {    
            DocumentBuilderFactory dFactory = DocumentBuilderFactory.newInstance();  
            DocumentBuilder builder = dFactory.newDocumentBuilder();                              
            Document doc = builder.parse(new File("config.xml"));   
          
            NodeList nl = doc.getElementsByTagName("className");  
            Node classNode = nl.item(0).getFirstChild();  
            String cName = classNode.getNodeValue();  
			
            // Create a class from its name
            Class c = Class.forName(cName);  
            Object obj = c.newInstance();  
            return obj;  
        }     
        catch(Exception e) {  
            e.printStackTrace();  
            return null;  
        }  
    }  
}
```



```xml
<!— config.xml -->  
<?xml version="1.0"?>  
<config>  
    <className>FileLoggerFactory</className>  
</config>
```




```java
public class Client {
  public static void main(String args[]) {  
        LoggerFactory factory = (LoggerFactory)XMLUtil.getBean();  
        factory.writeLog();
    }  
}
```



### Real world examples

- [java.util.Calendar](http://docs.oracle.com/javase/8/docs/api/java/util/Calendar.html#getInstance--)
- [java.util.ResourceBundle](http://docs.oracle.com/javase/8/docs/api/java/util/ResourceBundle.html#getBundle-java.lang.String-)
- [java.text.NumberFormat](http://docs.oracle.com/javase/8/docs/api/java/text/NumberFormat.html#getInstance--)
- [java.nio.charset.Charset](http://docs.oracle.com/javase/8/docs/api/java/nio/charset/Charset.html#forName-java.lang.String-)
- [java.net.URLStreamHandlerFactory](http://docs.oracle.com/javase/8/docs/api/java/net/URLStreamHandlerFactory.html#createURLStreamHandler-java.lang.String-)
- [java.util.EnumSet](https://docs.oracle.com/javase/8/docs/api/java/util/EnumSet.html#of-E-)
- [javax.xml.bind.JAXBContext](https://docs.oracle.com/javase/8/docs/api/javax/xml/bind/JAXBContext.html#createMarshaller--)



### Applicability

Use the Factory Method when

* a class can't anticipate the class of objects it must create
* a class wants its subclasses to specify the objects it creates
* classes delegate responsibility to one of several helper subclasses, and you want to localize the knowledge of which helper subclass is the delegate



### Consequences

> Factory methods eliminate the need to bind application-specific classes into your code. The code only deals with the Product interface; therefore it can work with any user-defined Concrete Product classes.
>
> A potential disadvantage of factory methods is that clients might have to subclass the Creator class just to create a particular Concrete Product object. Subclassing is fine when the client has to subclass the Creator class any way, but otherwise the client now must deal with another point of evolution.

Here is two additional consequences of the Factory Method pattern:

> 1. Provides hooks for subclasses. Creating objects inside a class with afactory method is always more flexible than creating an object directly.Factory Method gives subclasses a hook for providing an extended versionof an object.
> 2. Connects parallel class hierarchies. Parallel class hierarchies result when a class delegates some of its responsibilities to a separate class.