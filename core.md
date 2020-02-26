[All questions](README.md)

# Common Java questions
+ [What does PECS stand for?](#what-does-pecs-stand-for)
+ [What are wildcards and their types?](#what-are-wildcards-and-their-types)
+ [What are covariant, contravariant and invariant?](#what-are-covariant-contravariant-and-invariant)

[Table of content](#common-java-questions)

### What is Class in Java? 
In Java, a class is a template used to create objects and define the data type. It acts as a building block for Java language-oriented systems.

### What Is the Difference Between Static and Dynamic Loading?
Static class loading involves the creation of objects and instances using new keywords, and dynamic class loading is done when the name of the class is not known at compile time.

### What Is Multi-Threading?
Multi-threading is a programming concept used to run multiple tasks in a concurrent manner within a single program.

### By Whom and When was Java developed?
Java was developed by James Gosling in Sun Microsystem in 1995.

### What are JDK, JRE, and JVM Stand for?
* JVM stands for Java Virtual Machine, which is a runtime environment for compiled Java class files.
* JRE stands for Java Runtime Environment
* JDK stands for Java Development Kit

# Name one of the most Important Features of Java?
Java is a platform independent language.

### Do Java have "pointers"?
No. Java doesn’t use pointers. It has a tough security. Instead of pointers, references are used in Java as they are safer and more secure when compared to a pointer.

### What Are the Functions of JVM and JRE?
* JVM provides a runtime environment for Java Byte Codes to be executed. 
* JRE includes sets of files required by JVM during runtime.

### What Is the Difference Between Overloading and Overriding?
When there are two methods of the same name but different properties, it is overloading. Overriding occurs when there are two methods of the same name and properties, one is in the child class and the other is in the parent class. 

### What Is the Default Size of the Load Factor in Hashing a Based Collection?
The default size is 0.75, and the default capacity is computed as `Initial capacity * Load factor`

### What Is a Package?
A package is a collection of related classes and interfaces.

### What's the Base Class of all Exception Classes?
`Java.lang.Throwable` is the superclass of all exception classes, and all exception classes are derived from this base class.  

### What Is the Difference Between `equals()` and `= =`  ?
* `Equals()` method is used for checking the equality of two objects defined by business logic.
*  `==` or the equality operator is used to compare primitives and objects.

### What are Differences Between an Inner Class and a Subclass?
* While Inner classes are in the same file, subclasses can be in another file. 
* While subclasses have the methods of their parent class, inner classes get the methods they want.

### What Is an Anonymous Class?
The class defined without a name in a single line of code using new keyword is known as an anonymous class.

### What Are Constructors in Java?
In Java, the constructor is a block of code used to initialize an object.

### What Are the Types of Constructors?
There are two types of constructors:
* Default constructor.  A constructor that has no parameter is known as default constructor.  If we don’t define a constructor in a class, the compiler creates a default constructor (with no arguments) for the class.
* Parameterized constructor. A constructor that has known parameters is a parameterized constructor. If we want to initialize fields of the class with your own values, then use a parameterized constructor.

### How Are Destructors Defined in Java?
Since Java has its own garbage collection, no destructors are required to be defined.       Destruction of objects is automatically carried by the garbage collection mechanism.

### What is Garbage Collection in Java?
When an object is no longer used or referenced, garbage collection is called and the object is destroyed automatically.

### How Java achieves platform independence? 
Combination of byte code and JVM makes Java program platform independent. 
Java programs are platform independent but JVM is not.

### What is ClassLoader in Java?
ClassLoader in Java is a class which is used to load class files in Java. 
Java code is compiled into class file by javac compiler and JVM executes Java program, by executing byte codes written in class file. ClassLoader is responsible for loading class files from file system, network or any other source. There are three default class loader used in Java:
* Bootstrap class loader;
* Extension class loader;
* System/Application class loader. 

### Simpliest Java program to check if a number is Even or Odd without Modulus or Reminder Operator? 
```
//variant 1
if((number & 1) == 0){ 
  System.out.println("Even number"); 
}
//variant 2
int quotient = number/2; 
if(quotient*2== number) {
 System.out.println("Even number"); 
 }

```

### Difference between ArrayList and HashSet in Java? 
* First and most important difference between ArrayList and HashSet is that ArrayList implements List interface while HashSet implements Set interface in Java
* ArrayList allow duplicates while HashSet doesn't allow duplicates.
* ArrayList is an ordered collection and maintains insertion order of elements while HashSet is an unordered collection and doesn't maintain any order.
* Internally ArrayList is backed by an Array while HashSet is backed by an HashMap instance. 
* ArrayList's retrieve object by calling get(index) or remove objects by calling remove(index) while HashSet is completely object based. HashSet also doesn't provide get() method.

### What is double checked locking in Singleton?
```
class DCLSingleton {

    private static voaltile DCLSingleton _instance  = null;

    private DCLSingleton() {
    }

    public static DCLSingleton instance() {
        if (_instance == null) { // 1st check

            synchronized (DCLSingleton.class) {

                if (_instance == null) // 2nd check
                {
                    _instance = new DCLSingleton();
                }
            }
        }
        return _instance;
    }
}
```
### How do you create thread-safe Singleton in Java?
* Using Enum
```
public enum Singleton{
    INSTANCE;
 
    public void doAction() {
        System.out.println("Singleton using Enum in Java");
    }
}

```
* Using Static Field Initialization
```
private static final Singleton INSTANCE = new Singleton();
 
    private Singleton(){ }

    public static Singleton getInstance(){
        return INSTANCE;
    }
    public void doAction() {
        System.out.println("Singleon using static initialization in Java");
    }
```

### When to use volatile variable in Java? 
Volatile variable in Java is a special variable which is used to signal threads, a compiler that this particular variables value are going to be updated by multiple threads inside Java application. 
Scenarios:
1) Any variable which is shared between multiple threads should be made Volatile, in order to ensure that all thread must see the latest value of the volatile variable.
2) A signal to compiler and JIT to ensure that compiler does not change ordering or volatile variable and moves them out of synchronized context.
3) You want to save the cost of synchronization as volatile variables are less expensive than synchronization.

### What is transient variable in Java?
Transient variable is used to prevent any object from being serialized and you can make any variable transient by using transient keyword. 

### Difference between the transient and volatile variable in Java? 
Transient variables are used to prevent serialization or a field while volatile variables are used to prevent reordering and avoid reading cached value of field in multithreaded Java program. Only similarity between transient and volatile keyword is that they are only applicable to field or properties of class. You can not use transient or volatile keyword during class or method declaration in Java.

### Difference between Serializable and Externalizable in Java? 
* One of the obvious difference between Serializable and Externalizable is that Serializable is a marker interface i.e. does not contain any method but Externalizable interface contains two methods writeExternal() and readExternal().
*  responsibility of Serialization: when a class implements Serializable interface, default Serialization process gets kicked of and that takes responsibility of serializing super class state. When any class in Java implement java.io.Externalizable than its your responsibility to implement Serialization process i.e. preserving all important information.
* performance: you can not do much to improve performance of default serialization process except reducing number of fields to be serialized by using transient and static keyword but with Externalizable interface you have full control over Serialization process.
* maintenance: when your Java class implements Serializable interface its tied with default representation which is fragile and easily breakable if structure of class changes e.g. adding or removing field. By using java.io.Externalizable interface you can create your own custom binary format for your object.

### What does __PECS__ stand for?
The term __PECS__ stands for “Producer Extends, Consumer Super”.<BR/>
It means that if a parameterized type represents a producer, use extends . 
If it represents a consumer, use super . 
If the parameter is both, don’t use wildcards at all—the only type that satisfies both requirements is the explicit type
itself.<BR/>
The advice boils down to:
+ Use extends when you only get values out of a data structure
+ Use super when you only put values into a data structure
+ Use an explicit type when you plan to do both<BR>
Example: `<R> Stream<R> map(Function<? super T,? extends R> mapper)` where Function<T,R> consumes a T and produces an R.

[Table of content](#common-java-questions)

### What are wildcards and their types?
A __wildcard__ is a type argument that uses a question mark `?` , which may or may not
have an upper or lower bound.<BR/>
Types of wildcards:
* Unbounded Wildcards. F.e. `List<?> list`
* Upper Bounded Wildcards. An upper bounded wildcard uses the `extends` keyword to set a superclass limit. F.e. `List<? extends Number>`
* Lower Bounded Wildcards. A lower bounded wildcard means any ancestor of your class is acceptable. 
`super` keyword is used with the wildcard to specify a lower bound. F.e. `List<? super Number>`

[Table of content](#common-java-questions)

### What are covariant, contravariant and invariant?
* The term __covariant__ preserves the ordering of types from more specific to more gen‐
eral. In Java, f.e. arrays are covariant because String[] is a subtype of Object[]. 
Also when the `extends` keyword with a wildcard is used.

* The term __contravariant__ goes the other direction. 
F.e. when the `super` keyword with a wildcard is used.

* An __invariant__ means that the type must be exactly as specified. 
All parameterized types in Java are invariant unless we use `extends` or `super`.

[Table of content](#common-java-questions)

### What Are Getter and Setter?
Getter and setter are two conventional methods that are used for retrieving and updating the value of a variable.
A setter is a method that updates the value of a variable. 
A getter is a method that reads the value of a variable.
Getter and setter are also known as accessor and mutator in Java.

### Why Do We Need Getter and Setter?
The setter and getter methods protect a variable’s value from unexpected changes by the outside world — the caller code.
When a variable is hidden by the private modifier and can be accessed only through getter and setter, it is encapsulated.

### What is Naming Convention for Getter and Setter?
The naming scheme of setter and getter should follow the Java bean naming convention as  getXxx() and  setXxx(), where Xxx is the name of the variable. 

### What Are Serialization and Deserialization?
__Serialization__ allows to convert the state of an object into a byte stream, which then can be saved into a file on the local disk or sent over the network to any other machine. 
__Deserialization__ allows to reverse the process, which means reconverting the serialized byte stream to an object again.
In simple words, object serialization is the process of saving an object's state to a sequence of bytes and deserialization is the process of reconstructing an object from those bytes. 
The serialization process is platform independent, an object serialized on one platform can be deserialized on a different platform.

### What classes can be serialized?
Only Classes That Implement Serializable Can Be Serialized.
Interface Serializable works like a flag for the JVM. 
Any class that implements Serializable interface directly or through its parent can be serialized, and classes that do not implement Serializable can not be serialized.
When a class implements the Serializable interface, all its sub-classes are serializable as well. But when an object has a reference to another object, these objects must implement the Serializable interface separately. If our class is having even a single reference to a non Serializable class then JVM will throw NotSerializableException.

### Why Is Serializable Not Implemented by Object?
The Object class does not implement Serializable interface because we may not want to serialize all the objects, f.e. serializing a thread does not make any sense.

### What Is serialVersionUID? And Why Should We Declare It?
The JVM associates a version number to each serializable class to control the class versioning. 
It is used to verify that the serialized and deserialized objects have the same attributes and thus are compatible with deserialization. The version number is maintained in a field called serialVersionUID. If a serializable class doesn't declare a serialVersionUID, the JVM will generate one automatically at run-time.
The serialVersionUID is used to verify that the serialized and deserialized objects have the same attributes and thus are compatible with deserialization.
It is highly recommended that each serializable class declares its serialVersionUID as the generated one is compiler dependent and thus may result in unexpected InvalidClassExceptions.
We should create a serialVersionUID field in our class so if we change our class structure (adding/removing fields), the JVM will not through InvalidClassException. If we do not provide it, the JVM provides one that might change when our class structure changes.

### How to prevent the class from Serialization and Deserialization?
We can override the default serialization behaviour inside our Java class by providing the implementation of writeObject and readObject methods.
We can throw NotSerializableException exception from writeObject and readObject , if we do not want our class to be serialized or deserialized.

### What's the Difference Between Stack and Queue?
The difference between a stack and a queue is that the stack is based on the Last in First out (LIFO) principle, and a queue is based on FIFO (First In, First Out) principle.

[All questions](README.md)