# A Primer About Software Engineering
# Chapter 6: Component and Object Design

## Write Shy Code [Pragmatic]

We want to design components that are self-containted: independent and with a single, well-defined purpose (also called *cohesion*, [Structured Design](https://www.amazon.com/Structured-Design-Fundamentals-Discipline-Computer/dp/0138544719)). When components are isolated from one another you can change one without breaking the other. So design and maintain a well-designed external interface.

So don't build train wrecks `car.getModel().getMaker().getFounder().getAdress()` and when functionality is required consider adding it to the external interface `car.getTheAdressOfTheFounder()` or decide that the functionality is stupid. The train wreck code couples you four classes. Changes in one of them will propagate and crash your train wreck. Avoid coupling your code by following the [Law of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter). Each unit should only talk to its immediate friends; don't talk to strangers.

## Object-Oriented Style
### Object Peer Stereotypes [Growing Object-Oriented Systems]
> We categorize an object’s peers (loosely) into three types of relationship. An object might have:
> __Dependencies__
> Services that the object requires from its peers so it can perform its responsibilities. The object cannot function without these services. It should not be possible to create the object without them.
> 
> __Notifications__
> Peers that need to be kept up to date with the object’s activity. The object will notify interested peers whenever it changes state or performs a significant action. Notifications are “fire and forget”; the object neither knows nor cares which peers are listening. Similarly, the listeners expect to be called but know nothing of the way the user interface dispatches its events. 
> __Adjustments__
> Peers that adjust the object’s behavior to the wider needs of the system. This includes policy objects that make decisions on the object’s behalf (the Strategy pattern) and component parts of the object if it’s a composite. For example, a Swing  JTable will ask a  TableCellRenderer to draw a cell’s value, perhaps as RGB (Red, Green, Blue) values for a color. If we change the renderer, the table will change its presentation, now displaying the HSB (Hue, Saturation, Brightness) values.

Dependencies are passed in through the constructor. Notifications and Adjustments can be passed in to the constructor. Adjustments can be initialized to common values, and notifications to a null object or an empty collection. Setters can be provided to change these later on.

### Composite Simpler Than the Sum of Its Parts
> All objects in a system, except for primitive types built into the language, are composed of other objects. When composing objects into a new type, we want the new type to exhibit simpler behavior than all of its component parts considered together.
