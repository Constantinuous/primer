# RichCode
# Chapter 6: Component and Object Design

## Write Shy Code [Pragmatic]

We want to design components that are self-containted: independent and with a single, well-defined purpose (also called *cohesion*, [Structured Design](https://www.amazon.com/Structured-Design-Fundamentals-Discipline-Computer/dp/0138544719)). When components are isolated from one another you can change one without breaking the other. So design and maintain a well-designed external interface.

So don't build train wrecks `car.getModel().getMaker().getFounder().getAdress()` and when functionality is required consider adding it to the external interface `car.getTheAdressOfTheFounder()` or decide that the functionality is stupid. The train wreck code couples you four classes. Changes in one of them will propagate and crash your train wreck. Avoid coupling your code by following the [Law of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter). Each unit should only talk to its immediate friends; don't talk to strangers.

## Law of Demeter

	class Demeter{
	

	}
