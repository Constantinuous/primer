# A Primer About Software Engineering
# Chapter 4: Error Handling

## When to use Exceptions [Pragmatic Programmer]

Don't overuse exceptions to handle business logic. Exceptions should rarely be used be used in the normal program flow and instead reserved for exceptional events. 

For example if a configuration file __should__ exist, it probably warrants an exception. On the other hand, if we have __no idea__ whether a file should exist or not (a user supplies a file to the program) don't use an exception, it is not exceptional enough.  

Ask yourself: "Will this code still run if I remove all the exceptions and exception handlers?"

When you utilize exceptions, write your try,catch,finally blocks first. Then produce and verify the exceptions via tests. And lastly, write your happy path tests and code.

## When to use null
Never.

Never return null from a function and - even more important - never pass null to a function. Exceptions can be made for private functions, maybe. If you have a library which takes and returns null you should wrap it with your own class which again does not allow null passing or returning. One of the main purposes of your code is to reveal your intention to other developers. 


### Never return null
Null checking makes a code harder to read and it's easy to forget a null check somewhere if all returns can be null. You have a couple of choices instead of returning null:

* If a function returns a collection, just return an empty collection. *Collections.emptyList()* does the trick in Java.
* Return a [special case object](http://martinfowler.com/eaaCatalog/specialCase.html) that has the same interface as what the caller expects. The object is configured to handle the special case. Thus you don't need to change your happy, normal path code.
* Return a [Null Object](https://en.wikipedia.org/wiki/Null_Object_pattern) that has the same interface as what the caller expects. It has no or default behavior. It is also a singleton object. You can compare the functions result against the singleton (`result == A.NULL`) and find out if you got a null object.
* Return an Option, Maybe or May. It is a single-value container that either contains a value or doesn't (it is then said to be "empty"). This makes the absence of a return value very explicit.

In Java 8 you can return a *java.util.Optional* or write it yourself. In Scala it's called *Option[T]* and in Haskel *Maybe*. 

Kotlin does not have Optional. The type system itself enforces null safety. A variable which might be null can only be accessed with the elvis operator *?:*. Contrast this with C# 6.0 which also has the elvis operator but the type system does not enforce null safety. Here you can easily misuse the operator and make your code harder to read. You can indicate missing primitives with Nullable types but not the absence of an object. Thus write your own Option in C# as well.

### Never pass null

Returning null is bad. Passing null is worse. It’s better to use “empty” versions of the type that’s being expected, e.g. an empty array, string or object. Also passing null means that the passed argument is like a flag. And flags are ugly, because they indicate the method is doing too much. 

If you forbid passing null by default you never have to do ugly null checks and you can never *forget* to do null checks.
