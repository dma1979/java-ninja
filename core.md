[All questions](README.md)

# Common Java questions
+ [What does PECS stand for?](#what-does-pecs-stand-for)

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
+ Use an explicit type when you plan to do both


[Table of content](#common-java-questions)


[All questions](README.md)