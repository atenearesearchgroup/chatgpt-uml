# Twitter Metamodel

## Context

We want to develop a metamodel for a basic subset of Twitter.

## Questions

Develop a UML model with the abstract syntax of a subset of the Java programming language to allow the definition of classes, their attributes and methods. More specifically, it must be able to represent at least the following concepts: Basic Type (int, byte, short, long, float, double, boolean and char), Class, Attribute, Method and Parameter (of a method). Attributes, methods and parameters must have a name and a type, which can be a basic type or a previously defined class. It must also be possible to describe the cardinality and visibility (public, protected, default or private) of the language elements. Finally, it must be possible to define inheritance relationships between classes.

1. Develop a metamodel (i.e., a UML model with its abstract syntax) for Twitter, with its main concepts. It should include at least the  concepts of Tweet, User, DirectMessage, List, and Hashtag, as well as the relationships between them, e.g., Followers of a user, Mentions of a tweer, etc. Specify the appropriate integrity constraints (invariants) so that the models that can be built with that metamodel are correct.

2. Add methods to the Twitter metamodel developed above to perform the following operations: post a tweet; follow and unfollow a user; and retweet, like or reply to a tweet. Also include operations (queries) to be able to know the tweets of a user, their followers and the lists a user is in.  Specify their behavior using pre- and post-conditions in OCL.



 









