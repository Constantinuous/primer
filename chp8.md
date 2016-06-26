# RichCode
## Chapter 8: Support

Sooner or later someone will find a bug in your software. And probably it's not in your code. Maybe the bug is in software you have never written a single line for. It is "someone elses code" but it is definately your problem. 

1. The first rule, a very pragmatic one, is "don't panic".
2. The second rule is to inspect all the data the customer has provided. It's usually not enough.
3. The third rule is accordingly: ask the customer clarifying questions. Ask questions to figure out what the problem is and how to reproduce it. 
4. Then forget about the bug. You could waste hours trying to figure out what the customer didn't say. Or you could save money by asking questions. About 50% of the time you can stop here. No one responds, so the bug is probably not important.

How to solve a bug:

1. Reproduce the bug. 
	* Start the application version the customer had.
	* Do the steps the customer did. IF this did not help, try
	* … importing the required database snapshot into your dev database (probably hard to get). If you use event sourcing just replay the required events in your dev environment.
	* If the bug is not reproducable you can only modify code to fix what your think is *probably* wrong. But how can you then mark it as solved? Do you have a test to show that it is solved?  That is when we reject the bug and mark it as not-reproducable.
2. Write a test for the bug.
3. Fix the bug.
4. You have now seen what was wring. Maybe you discovered other bugs. Write tests for them and fix them as well.
4. Mark as solved. The evidence is the passing test(s).
