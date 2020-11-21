# Java Review

1. What does gc do? and how?

   The garbage collector is part of the java platform. It runs in the background in a low priority. It reclaims the objects and makes sure that the running program in its current state is never use them again.

   Algorithm: 

   - reference counting:  When an object's reference variable is assigned to a reference variable, the reference count is incremented by 1. When the reference variable no longer refers to an object, the reference count is decremented by 1.

   - Tracing algorithm: root set

     include: 

     • Reference variables in the Java stack for each thread
     • Static reference variables defined in loaded classes
     • Reference variables registered using the Java Native Interface (JNI)

   ​		The object that can be reach directly or undirectly from the root set are live other would be dead.

2. Difference between JDK JRE

   JDK=JRE+Development Tool

   JRE=JVM+Library classes

   JDK is only used by java develop

3.  4 Pillar

   Encapsulation

   - Grouping together data and behaviour into logical components.
   - High cohesion and low coupling

   Abstraction

   - Extracting relevant and essential information and behaviour

   Inheritance

   - Receiving the behaviors and attributes of another class or interface

   Polymorphism

   - have multiple forms or versions of the same type of things and the same types of behavior

4. Binding

   Joining the attributes and method calls to the actual objects and the behavior in the memory.

   How the program decides on the next action or piece of functionality which needs executing.

   Early binding: compile time

   Late Binding: run time

5. What is the main interface of collections?

   List Queue Set

6. Two way we can compare?

   Comparable compareTo

   Comparator compareTo and equals

7. 