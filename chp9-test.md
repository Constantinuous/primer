# A Primer About Software Engineering
# Chapter 9: Tests


It’s the tests that keep our code flexible, maintainable, and reusable. Tests act as living documentation. Tests remove the fear of change and thus tests enable change.

## Test Doubles
[Mocks aren't stubs](http://martinfowler.com/articles/mocksArentStubs.html). 

> __Dummy objects__ are passed around but never actually used. Usually they are just used to fill parameter lists.
> __Fake objects__ actually have working implementations, but usually take some shortcut which makes them not suitable for production (an in memory database is a good example).
> __Stubs__ provide canned answers to calls made during the test, usually not responding at all to anything outside what's programmed in for the test. Stubs may also record information about calls, such as an email gateway stub that remembers the messages it 'sent', or maybe only how many messages it 'sent'.
> __Mocks__ are objects pre-programmed with expectations which form a specification of the calls they are expected to receive. Mocks use behavior verification, where we check to see if the an object made the correct calls on the mock. We do this check by telling the mock what to expect during setup and asking the mock to verify itself during verification. 

> Of these kinds of doubles, only mocks insist upon behavior verification. The other doubles can, and usually do, use state verification. [...] Mock objects always use behavior verification, a stub can go either way. Meszaros refers to stubs that use behavior verification as a Test Spy.
