## Factory Method Pattern (1)

### Intent

> Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.

### Motivation

The disadvantage of implementing Simple Factory Pattern is that when add a new product type to the system, the simple factory must be modified which deviate Open Close Principle. Additionally, when implementing simple factory pattern, all the product will be created by the same factory so the business logic of the factory class will be more complicated which cause a high coupling between factory class and concrete product class. The Factory Method pattern offers a solution. It encapsulates the knowledge of
which document subclass to create and moves this knowledge out of the framework.

Simple Factory Pattern is introduced in the following content.

#### Simple Factory Pattern (Code example)

####Structure

![Simple Factory](./Images/SimpleFactoryPattern.svg)

#### Code Sample

configWeapon.xml

```xml
<?xml version="1.0"?>
<config>
	<weapon>Elvish</weapon>
</config>
```

XMLUtilWeapon.java

```java
import javax.xml.parsers.*;
import org.w3c.dom.*;
import org.xml.sax.SAXException;
import java.io.*;

public class XMLUtilWeapon {
	// Extract the weapon name from the xml configure file
  public static getWeaponType() {
    try {
      // Create document object
			DocumentBuilderFactory dFactory = DocumentBuilderFactory.newInstance();
			DocumentBuilder builder = dFactory.newDocumentBuilder();
			Document doc;							
			doc = builder.parse(new File("configWeapon.xml")); 
		
			// Get node that contains the weapon name
			NodeList nl = doc.getElementsByTagName("weapon");
            Node classNode = nl.item(0).getFirstChild();
            String weapon = classNode.getNodeValue().trim();
            return weapon;
    } catch (Exception e) {
      	e.printStackTrace();
           		return null;
    } 
  }
}
```

Weapon.java

```java
public interface Weapon {
  public void attack();
}
```

ElvishWeapon.java

```java
public class ElvishWeapon implements Weapon {
  public void attack() {
    // Do something...
  }
}
```

OrcishWeapon.java

```java
public class OrcishWeapon implements Weapon {
  public void attack() {
    // Do something...
  }
}
```

BlackSimth.java

```java
public class BlackSmith {
  public static Weapon manufactureWeapon(String weapon) throws Exception {
    if(weapon.equalsIngoreCase("Elvish")) {
      return new ElvishWeapon();
    } else if(weapon.equalsIngoreCase("Orcish")) {
      return new OrcishWeapon();
    } else {
      throw new Exception("Weapon is not exist!");
    }
  } 
}
```

Elf.java

```java
public class Elf {
  public static void main(String args[]) {
    try {
      String type = XMLUtilWeapon.getWeaponType();
      Weapon weapon = BlackSmith.manufactureWeapon(type);
      weapon.attack();
    } catch (Exception e) {
      // TODO: ...
    }
  }
}
```



