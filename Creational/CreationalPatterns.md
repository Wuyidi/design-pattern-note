## Creational Pattern

Creational design patterns abstract the instantiation process. They help make a system independent of how its objects are created, composed and represented. A class creational pattern use inheritance to vary the class that's instantiated, whereas an object creational pattern will delegate instantiation to another object.

Creational pattern become important as system evolve to depend more on object composition than class inheritance. As that happens, emphasis shifts away from hard-coding a fixed set of behaviours toward defining a smaller set of fundamental behaviors that can be composed into any number of complex ones. Thus creating objects with particular one behaviors requires more than simply instantiating a class.

These are two recurring themes in these patterns. First, they all encapsulate knowledge about which concrete classes they system use. Second, they hide how instance of these classes are created and put together. All the system at large knows about objects is their interfaces as defined by abstract class. Consequently, the creational pattern give you a lot of flexibility  in what gets created, who create it, how it gets created, and when. They let you configure a system with "product" objects that vary widely in structure and functionality. Configuration can be static (that is, specified at compile-time) or dynamic
(at run-time).


​			
​		
​	





