# SOLID

After considerable research and analysis of the problems we shall have to tackle while developing our solution, I have a suggestion of using **SOLID** principles.

**SOLID** principles was developed by Robert C. Martin in a 2000 essay _"Design Principles and Design Patterns"_ and the acronym **SOLID** was later coined by Michael Feathers. In his essay, Robert C. Martin conveyed:

_Successful software will change and develop. As, it changes, it becomes increasingly complex. Without good design principles, software becomes rigid, fragile, immobile and viscous with modifications and upgrades._

To tackle such problems and make the design easier to understand and easier to distribute work over developers, SOLID principles were developed.

**SOLID**, the acronym stands for:
- **S** -> _Single Responsibility Principle_
- **O** -> _Open-Closed Principle_
- **L** -> _Liskov-Substitution Principle_
- **I** -> _Interface Segregation Principle_
- **D** -> _Dependency Inversion Principle_

### Single Responsibility Principle:
- It states that "A single class should have only a single reason to change"
- This interprets to each class doing just one thing and each class and module having their own responsibility and functionality. i.e., interfaces and derived classes and abstraction and polymorphism to be implemented such that each class has only one functionality.
- The best example is Microservices, just as each Microservice has one functionality an when, if required, derived microservice of group of microservices is utilised, in the same manner classes should be implemented.
- Ex: Suppose we have to store and manage books, and print them. In such a case, the best way would be to have a class for book that stores details about books, a class bookReader for reading books, a class bookEditor for editing books and a class bookPrinter for printing books. This will have all classes with just one simple functionality.
```java
class Book{
    int bookId;
    String bookName;
}

class bookPrinter{
    public void print(Book book){
    //action
    }
}

class bookReader{
    public void read(Book book){
    //action
    }
}

class bookEditor{
    public void edit(Book book){
    //action
    }
}
```
### Open-Closed Principle:
- It states that "A class's behavior can be changed without modifying it."
- This basically interprets as instead of changing the base classes, extending them and adding functionalities is advisable for better implementation.
- - Open: open for extensions, meaning class's behaviors can be changed by extending the base class
  - Closed: closed for modification, i.e., source code is set and cannot be changed.
- Ex: Suppose we have a class Guitar with a certain behavior and now we need to add a behavior to it. So instead of modifying the existing source code, we extend a new class to Guitar and add the functionality and use the abstraction of this class to implement the new behaviors.

```java
class Guitar{
    int numberOfStrings;
    String typeOfGuitar;
}
```
```java
class GuitarWithAmplifier extends Guitar{
  boolean amplifierBeingUsed;
  public void useAmplifier()}
  //actions
  }
}
```

### Liskov-Substitution Principle:
- This principle states that "Every derived class should be substitutable for its parent class"
- It is a way of ensuring derived classes extend the base clas without changing behavior.

_Ex:  if for each object O1 of type A defining in program P, and each object O2 of type B.
If for program P, defined in terms of B, if substituting O2 for O1 the behavior of program P remains unchanged then A is a subtype of B, implying B is derived from A or A and B have the same parent and are substitutable for their parent class._

- Suppose, we have an interface Car which is implemented by MotorVehicle. Now, later there is a new type of car which has different behavior than what should be implemented from previous implementation of interface Car in our source code. So, we implement the interface Car in such a manner that the program bhaior remains the same for substitution of this new type of vehicle.

```java
public interface Car{
    void startEngine();
    void accelerate();
    void brake();
}
```
```java
class MotorVehicle implements Car{
    void startEngine(){
        System.out.print("Engine started");
    }
    void accelerate(){
        System.out.print("Accelerating");
    }
    void brake(){
    System.out.print("Braking");
    }
}
```
```java
class ElectricVehicle implements Car{
    void startEngine(){
        System.out.print("No Engine");
    }
    void accelerate(){
        System.out.print("Accelerating");
    }
    void brake(){
        System.out.print("Braking");
    }
}
```
- Now, ElectricVehicle also can substitute for its parent or its substitution and the program's behavior unchanged however functionality may change.

### Interface Segregation Principle:
- This principle states that "Fine grained interfaces that are client-specific should be made. Clients should not be forced to implement interfaces they do not use."
- This basically interprets to not making concetrated classes/interfaces but multiple interfaces and then let classes implement to these one or more interfaces at a time for composition of behavior using inheritance.
- This means, client does not need to interact with interfaces unnecessarily if they are not interested in using them.
-Instead of having a single interface for multiple tasks such as:
```java
public interface Bear{
    void feedBear();
    void petBear();
    void bathBear();
}
```
- Multiple interfaces should be made for each task to achieve single task for each interface:
```java
public interface petBear{
    void pet();
}

public interface feedBear{
    void feed();
}

public interface bathBear{
    void bath();
}
```
-So now, when we want to have a functionality that only requires to feed and pet but bath, we could simply implement them in our function instead of the intial Bear interface which would have required complex code to avoid bathing bear. This way, the design becomes simpler to understand.

```java
public class BearCarer implements petBear, feedBear{
    public void feed(){
        //actions
    }
    public void pet(){
        //actions
    }
}
```
### Dependency Inversion Principle:
- This principle focuses on having more abstractions than concretions i.e., High-level modules should not depend on low-level modules but rather on abstractions.
- Abstractions should not depend upon details. Details should depend upon abstractions.

## Conclusion

By following **SOLID** principles, we can keep our design issues to the minimum and make our code better in terms of readability, maintainability, design pattern and testability.

## _REFERENCES_
_[1] [https://www.baeldung.com/solid-principles](https://www.baeldung.com/solid-principles)_\
_[2] [https://en.wikipedia.org/wiki/SOLID](https://en.wikipedia.org/wiki/SOLID)_\
_[3] ["Design Principles and Design Patterns" by Robert C. Martin](http://staff.cs.utu.fi/~jounsmed/doos_06/material/DesignPrinciplesAndPatterns.pdf)_