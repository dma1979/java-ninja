[All questions](README.md)

# Java 8
## General
+ [What Main New Features Were Added in Java 8?](#what-main-new-features-were-added-in-java-8)
+ [What is Functional Interface?](#what-is-functional-interface)
## Method References
+ [What Is a Method Reference?](#what-is-a-method-reference)
+ [What Is the Meaning of `String::Valueof` Expression?](#what-is-the-meaning-of-stringvalueof-expression)
## Optional
## Default Methods
## Lambda Expressions
## Streams
## New Date and Time API

[Table of content](#java-8)

### What are Main New Features Added in Java 8?
The most significant features are the following:
+ __Lambda Expressions__ − a new language feature allowing treating actions as objects
+ __Method References__ − enable defining Lambda Expressions by referring to methods directly using their names
+ __Optional__ − special wrapper class used for expressing optionality
+ __Functional Interface__ – an interface with maximum one abstract method, implementation can be provided using a Lambda Expression
+ __Default methods__ − give us the ability to add full implementations in interfaces besides abstract methods
+ __Nashorn, JavaScript Engine__ − Java-based engine for executing and evaluating JavaScript code
+ __Stream API__ − a special iterator class that allows processing collections of objects in a functional manner
+ __Date API__ − an improved, immutable JodaTime-inspired Date API

Along with these new features, lots of feature enhancements are done under-the-hood, at both compiler and JVM level.

[Table of content](#java-8)

### What is Functional Interface?
__Functional interface__ is defined as an interface that contains only a single, abstract method (SAM).

[Table of content](#java-8)

### What Is a Method Reference?
A _method reference_ is a Java 8 construct that can be used for referencing a method without invoking it. 
<br/>It is used for treating methods as Lambda Expressions. They only work as syntactic sugar to reduce the verbosity of some lambdas. 
<br/>This way, the following code `(o) -> o.toString();` can become `Object::toString();` <BR/>
A method reference can be identified by a double colon separating a class or object name and the name of the method. 
It has different variations:
+ constructor reference: `String::new;`
+ Static method reference: `String::valueOf;`
+ bound instance method reference: `str::toString;`
+ unbound instance method reference: `String::toString;`

[Table of content](#java-8)

### What Is the Meaning of `String::Valueof` Expression?
It is a static method reference to the `valueOf` method of the `String` class.

[Table of content](#java-8)

### What Is Optional? How Can It Be Used?
__Optional__ is a new class in Java 8 that encapsulates an optional value i.e. a value that is either there or not.
 It is a wrapper around an object, and you can think of it as a container of zero or one element.<br/>

Optional has a special Optional.empty() value instead of wrapped null. 
Thus it can be used instead of a nullable value to get rid of NullPointerException in many cases.<br/>

The main purpose of Optional, as designed by its creators, was to be a return type of methods that previously would return null. 
Such methods would require you to write boilerplate code to check the return value and sometimes could forget to do a defensive check. 
In Java 8, an Optional return type explicitly requires you to handle null or non-null wrapped values differently.

It's worth noting that Optional is not a general purpose class like Option in Scala. 
It is not recommended to be used as a field value in entity classes, which is clearly indicated by it not implementing the Serializable interface.
    
### Describe Some of the Functional Interfaces in the Standard Library.
There are a lot of functional interfaces in the `java.util.function` package, the more common ones include but not limited to:
* Function – it takes one argument and returns a result
* Consumer – it takes one argument and returns no result (represents a side effect)
* Supplier – it takes not argument and returns a result
* Predicate – it takes one argument and returns a boolean
* BiFunction – it takes two arguments and returns a result
* BinaryOperator – it is similar to a BiFunction, taking two arguments and returning a result. The two arguments and the result are all of the same types
* UnaryOperator – it is similar to a Function, taking a single argument and returning a result of the same type
    
### What Is a Functional Interface? What Are the Rules of Defining a Functional Interface?
A __functional interface__ is an interface with no more, no less but one single abstract method (default methods do not count).

Where an instance of such interface is required, a Lambda Expression can be used instead. 
More formally put: Functional interfaces provide target types for lambda expressions and method references.

The arguments and return type of such expression directly match those of the single abstract method.

For instance, the Runnable interface is a functional interface.
Functional interfaces are usually annotated with the `@FunctionalInterface` annotation – which is informative and does not affect the semantics.
    
### What Is a Default Method and When Do We Use It?
A __default method__ is a method with an implementation – which can be found in an interface.

We can use a default method to add a new functionality to an interface while maintaining backward compatibility with classes 
that are already implementing the interface.
Usually, when a new abstract method is added to an interface, all implementing classes will break until they implement the new abstract method. 
In Java 8, this problem has been solved by the use of default method.

For example, Collection interface does not have forEach method declaration. Thus, adding such method would simply break the whole collections API.

Java 8 introduces default method so that Collection interface can have a default implementation of `forEach` method 
without requiring the classes implementing this interface to implement the same.
    
### Will the Following Code Compile?
```
@FunctionalInterface
public interface Function2<T, U, V> {
    public V apply(T t, U u);
 
    default void count() {
        // increment counter
    }
}
```
Yes. The code will compile because it follows the functional interface specification of defining only a single abstract method. 
The second method, count, is a default method that does not increase the abstract method count.
    
### What Is a Lambda Expression and What Is It Used For?
In very simple terms, a __lambda expression__ is a function that can be referenced and passed around as an object.

Lambda expressions introduce functional style processing in Java and facilitate the writing of compact and easy-to-read code.

Because of this, lambda expressions are a natural replacement for anonymous classes as method arguments. 
One of their main uses is to define inline implementations of functional interfaces.
    
### Explain the Syntax and Characteristics of a Lambda Expression
A lambda expression consists of two parts: the parameter part and the expressions part separated by a forward arrow as below:
```
params -> expressions
```
Any lambda expression has the following characteristics:
* Optional type declaration – when declaring the parameters on the left-hand side of the lambda, we don't need to declare their types as the compiler can infer them from their values. So int param -> … and param ->… are all valid
* Optional parentheses – when only a single parameter is declared, we don't need to place it in parentheses. This means param -> … and (param) -> … are all valid. But when more than one parameter is declared, parentheses are required
* Optional curly braces – when the expressions part only has a single statement, there is no need for curly braces. This means that param – > statement and param – > {statement;} are all valid. But curly braces are required when there is more than one statement
* Optional return statement – when the expression returns a value and it is wrapped inside curly braces, then we don't need a return statement. That means (a, b) – > {return a+b;} and (a, b) – > {a+b;} are both valid
    
### What Is __Nashorn__ in Java8?
__Nashorn__ is the new Javascript processing engine for the Java platform that shipped with Java 8. 
Until JDK 7, the Java platform used Mozilla Rhino for the same purpose. as a Javascript processing engine.
Nashorn provides better compliance with the ECMA normalized JavaScript specification and better runtime performance than its predecessor.
    
### What Is __jjs__?
In Java 8, __jjs__ is the new executable or command line tool used to execute Javascript code at the console.
    
### What is __jcmd__`
`jcmd` is a utility which sends diagnostic command requests to a running Java Virtual Machine i.e. JVM.
* It gets various runtime information from a JVM. 
* It must be used on the same machine on which JVM is running! (!)
* With this tool it is possible to tune the JVM on the fly
    
### What Is a Stream? How Does It Differ from a Collection?
In simple terms, a __stream__ is an iterator whose role is to accept a set of actions to apply on each of the elements it contains.<BR/>
The __stream__ represents a sequence of objects from a source such as a collection, 
which supports aggregate operations. They were designed to make collection processing simple and concise. 
Contrary to the collections, the logic of iteration is implemented inside the stream, 
so we can use methods like `map` and `flatMap` for performing a declarative processing.

Another difference is that the Stream API is fluent and allows pipelining.
Streams are inherently lazily loaded and processed.
    
### What Is the Difference Between Intermediate and Terminal Operations?
Stream operations are combined into pipelines to process streams. All operations are either intermediate or terminal. <BR/>

__Intermediate operations__ are those operations that return Stream itself allowing for further operations on a stream.
These operations are always lazy, i.e. they do not process the stream at the call site, 
an intermediate operation can only process data when there is a terminal operation. 
Some of the intermediate operations are `filter`, `map` and `flatMap`.<BR/>

__Terminal operations__ terminate the pipeline and initiate stream processing. 
The stream is passed through all intermediate operations during terminal operation call. 
Terminal operations include `forEach`, `reduce`, `collect` and `sum`.

The intermediate operations are only triggered when a terminal operation exists.!!!
    
### What Is the Difference Between Map and flatMap Stream Operation?
There is a difference in signature between `map` and `flatMap`. 
Generally speaking, a map operation wraps its return value inside its ordinal type while flatMap does not.
For example, in Optional, a map operation would return Optional<String> type while flatMap would return String type.<BR/>

So after mapping, one needs to unwrap (read “flatten”) the object to retrieve the value whereas, after flat mapping, 
there is no such need as the object is already flattened. The same concept is applied to mapping and flat mapping in Stream.<BR/>

Both map and flatMap are intermediate stream operations that receive a function and apply this function to all elements of a stream.

The difference is that for the map, this function returns a value, but for flatMap, this function returns a stream. 
The flatMap operation “flattens” the streams into one.


### What Is Stream Pipelining in Java 8?
__Stream pipelining__ is the concept of chaining operations together. 
This is done by splitting the operations that can happen on a stream into two categories: intermediate operations and terminal operations.<BR/>

Each intermediate operation returns an instance of Stream itself when it runs, an arbitrary number of intermediate operations can, 
therefore, be set up to process data forming a processing pipeline.<BR/>

There must then be a terminal operation which returns a final value and terminates the pipeline.
    
    
### Tell Us About the New Date and Time API in Java 8
    
In order to address different problems of existing API
(java.util.Date and SimpleDateFormatter aren’t thread-safe, java.util.Date- years start at 1900, months at 1, days at 0  end etc. ) 
and provide better support in JDK, a new date and time API, 
which is free of these problems, has been designed for Java SE 8 under the package java.time.

[All questions](README.md)
