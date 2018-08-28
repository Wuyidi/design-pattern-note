## Design Pattern Concept (2)

> **Misconception: "Patterns guarantee reusable software, higher productivity, world peace, etc."**
>
> Patterns don't guarantee anything. They don't remove humans from the creative process. They do help humans engaged in the creative process by describing known solutions to common problems in the domain. They are another tool in the designer's toolbox, not a silver bullet!

### The catalog of design patterns (Organize the catalog)

> We classify design patterns by two criteria. 
>
> 1. The first criterion, called purpose, reflects what a pattern does. Patterns can have either creational, structural, or behavioral purpose. Creational patterns concern the process of object creation. Structural patterns deal with the composition of classes or objects. Behavioral pattern characterize the ways in which classes or objects interact and distribute responsibility.
> 2. The second criterion, called scope, specifies whether the pattern applies primarily to classes or to objects. Class patterns deal with relationships between classes and their subclasses. These relationships are established through inheritance, so they are static—fixed at compile-time. Object patterns deal with object relationships, which can be changed at run-time and are more dynamic. Almost all patterns use inheritance to some extent. So the only patterns labeled "class patterns" are those that focus on class relationships. Note that most patterns are in the Object scope.

| Purpose    | Pattern Name                           | Scope        |
| ---------- | -------------------------------------- | ------------ |
| Creational | Singleton Pattern (单例模式)               | Object       |
| Creational | Simple Factory Pattern (简单工厂模式)        | Class        |
| Creational | Factory Method Pattern (工厂方法模式)        | Class        |
| Creational | Abstract Factory Pattern (抽象工厂模式)      | Object       |
| Creational | Prototype Pattern (原型模式)               | Object       |
| Creational | Builder Pattern (建造者模式)                | Object       |
| Structural | Adapter Pattern (适配器模式)                | Object/Class |
| Structural | Bridge Pattern (桥接模式)                  | Object       |
| Structural | Composite Pattern (组合模式)               | Object       |
| Structural | Decorator Pattern (装饰模式)               | Object       |
| Structural | Facade Pattern (外观模式)                  | Object       |
| Structural | Flyweight Pattern (享元模式)               | Object       |
| Structural | Proxy Pattern (代理模式)                   | Object       |
| Behavioral | Chain of Resposibility Pattern (职责链模式) | Object       |
| Behavioral | Command Pattern (命令模式)                 | Object       |
| Behavioral | Interpreter Pattern (解释器模式)            | Class        |
| Behavioral | Iterator Pattern (迭代器模式)               | Object       |
| Behavioral | Mediator Pattern (中介者模式)               | Object       |
| Behavioral | Memento Pattern (备忘录模式)                | Object       |
| Behavioral | Observer Pattern (观察者模式)               | Object       |
| Behavioral | State Pattern (状态模式)                   | Object       |
| Behavioral | Strategy Pattern (策略模式)                | Object       |
| Behavioral | Template Method Pattern (模板方法模式)       | Class        |
| Behavioral | Visitor Pattern (访问者模式)                | Object       |

