# RichCode
# Chapter 4: Exceptions

## When to use Exceptions [Pragmatic Programmer]

Don't overuse exceptions to handle business logic. Exceptions should rarely be used be used in the normal program flow and instead reserved for exceptional events. 

For example if a configuration file __should__ exist, it probably warrants an exception. On the other hand, if we have __no idea__ whether a file should exist or not (a user supplies a file to the program) don't use an exception, it is not exceptional enough.  

Ask yourself: "Will this code still run if I remove all the exceptions and exception handlers?" 