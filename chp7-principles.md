# A Primer About Software Engineering
# Chapter 7: Principles and Laws

Principles

* Single Responsibility Principle: A class should have only a single responsibility.
* Open/Closed Principle: Software entities … should be open for extension, but closed for modification.
* Liskov substitution principle: Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.
* Interface Segregation Principle: “many client-specific interfaces are better than one general-purpose interface.”
* Dependency Inversion Principle: One should Depend upon Abstractions. Do not depend upon concretions.
* Principle of least astonishment: "if a necessary feature has a high astonishment factor, it may be necessary to redesign the feature."

## Single Responsibility Principle

This principles is based on the principle of cohesion. A class should have only a single responsibility (i.e. only one potential change in the software's specification should be able to affect the specification of the class). This principle is about people, which stakeholders affect your class. If it is more than one, than you should change your design. Obviously this also has some technical implications. If your database table changes you should not have to change your entities, only your mappers.


## Law of Demeter
```java
class Demeter{
	private A a;
	private int getData(){
		// code here
	}
	
	// Law of Demeter:
	// A method 'm' of an object 'o' may only invoke methods on the following kinds of objects:
	void example(B b){
		int data = getData(); 	// 1. itself
		b.doSth();			// 2. the method's parameters
		a = new A();		
		a.doSthElse();		// 3. any objects created by m
		c.println();		// 4. global variables, accessible by 'o', in the scope of 'm '
	}
}
```
