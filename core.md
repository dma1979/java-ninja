[All questions](README.md)

# Common Java questions
+ [What does PECS stand for?](#what-does-pecs-stand-for)
+ [What are wildcards and their types?](#what-are-wildcards-and-their-types)
+ [What are covariant, contravariant and invariant?](#what-are-covariant-contravariant-and-invariant)

[Table of content](#common-java-questions)

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

[All questions](README.md)