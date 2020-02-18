Object-Oriented Design notes
============================

2020-02-11
----------
* Follow SOLID principles (Single responsibility, Open-closed, Liskov substitution, Interface segregation, Dependency injection)
* Examples of signle responsibility within classes and methods (using Structs to hide data structures, isolating extra responsibilites in classes,
extract extra responsibilites from methods)

2020-02-12
----------
* Focus on the messages that need to be sent in an app as opposed to its class (can reveal missing objects and classes that know too much about one another)
* Public interface should be stable and change little, private interfaces handle implementation details and should not be expected to be sent by others
* Depend on things that change less often than you do
* Think about using default hashes for class instantiation
* The Classes in your app should depend on code that you own: use a wrapping method to isolate external dependencies
* Use hashes for initialization argument to avoid depending on a fixed order of arguments
* Be sure to recognize dependencies and reduce them by injection (and delegate methods to avoid Law of Demeter violations)
* Tell, don't ask objects how to use data (make classes that can fill in for nil values - `Guest.new`)
* It is a tell don't ask violation when the object you're asking is the one performing the behavior
* Extract compound conditionals into private methods (`cond1 && cond2`)
* Extract implicit conditionals into explicit methods (try to keep methods short (1 line) and don't that don't any params)
* When about to use 3 conditional branches, try to extract into a new object that handles those conditionals and to answer the conditionals
* Organize methods in your class by descending order of abstraction (if having trouble with lvl of abstraction, there are probably too many methods in class)
* Don't use a control couple (i.e `comment.post(false)`, instead use 2 separate methods, i.e `comment.post` and `comment.post_without_notifying_admin`)

2020-02-14
----------
* Look out for duck types, methods shouldn't be too concerned about an object's class (look out for case statements w/ classes, `responds_to?`, `is_a?`, `kind_of?` methods)
* The best way to create an abstract superclass is by pushing code up from concrete subclasses
* Abstract superclasses use the template method pattern to invite inheritors to supply specializations and use hook methods to allow these inheritors to contribute these specializations without being force to send super
* Hook methods allow subclasses to contribute specializations w/o knowing the abstract algorithm. They remove the need for subclasses to send super and
thus reduces coupling between layers of the hierarchy and increase its tolerance to change
