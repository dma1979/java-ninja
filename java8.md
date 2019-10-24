[All questions](README.md)

# Java 8
## General
+ [What Main New Features Were Added in Java 8?](#what-main-new-features-were-added-in-java-8)
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


### What Is a Method Reference?
A _method reference_ is a Java 8 construct that can be used for referencing a method without invoking it. 
<br/>It is used for treating methods as Lambda Expressions. They only work as syntactic sugar to reduce the verbosity of some lambdas. 
<br/>This way, the following code `(o) -> o.toString();` can become `Object::toString();`

A method reference can be identified by a double colon separating a class or object name and the name of the method. 
It has different variations:
+ constructor reference: `String::new;`
+ Static method reference: `String::valueOf;`
+ bound instance method reference: `str::toString;`
+ unbound instance method reference: `String::toString;`

[Table of content](#java-8)

### What Is the Meaning of `String::Valueof` Expression?
It is a static method reference to the valueOf method of the String class.

[Table of content](#java-8)

[All questions](README.md)