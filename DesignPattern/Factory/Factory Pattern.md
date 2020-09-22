# Factory Pattern

## The Simple Factory

Not a real design pattern.

![image-20200922152146986](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200922152146986.png)

Every time you want to create a different concrete product you must 



## Factory Method Pattern

Defines an interface for creating an object, but lets subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclass.

![image-20200922153600022](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200922153600022.png)

Each ProductFactory would be responsible one concrete Product. Thus you can register your product factory and know which product you want.



## Abstract Factory Pattern

Provides an interface for creating families of related or dependent objects without specifying their concrete classes.

![image-20200922155736772](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200922155736772.png)