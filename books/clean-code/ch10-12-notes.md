Clean Code notes
================

Chapter 10 - Classes
--------------------
* Class Organization
  * A class should begin with a list of variables. Public static
    constants, if any, should come first. Then private static variables,
    followed by private instance variables. There is seldom a good reason to
    have a public variable (this is in accordance with Java conventions)
  * Public functions should follow the list of variables. We like to put
    the private utilities called by a public function right after the
    public function itself. This follows the stepdown rule and helps the
    program read like a newspaper article
* Encapsulation
  * We like to keep our variables and utility functions private, but
    we're not fanatic about it
  * Sometimes we need to make a variable or utility function protected
    so that it can be accessed by a test. For us, tests rule
  * If a test in the same package needs to call a function or access a
    variables, we'll make it protected or package scope. However, we'll
    first look for a way to maintain privacy. Loosening encapsulation is
    always a last resort
* Classes Should Be Small!
  * The first rule of classes is that they should be small. The second
    rule of classes is that they should be smaller than that
  * With functions we measured size by counting physical lines. With
    classes we use a different measure. We count *responsibilities*
  * The name of a class should describe what responsibilities. In fact,
    naming is probably the first way of helping determine class size
  * If we cannot derive a concise name for a class, then it's likely too
    large. The more ambiguous the class name, the more likely it has too
    many responsibilites
  * Class names including words like `Processor`, `Manager`, or `Super`
    often hint at unfortunate aggregation of responsibilites
  * We should also be able to write a brief description of the class in
    about 25 words w/o using the words "if", "and", "or", or "but"
* The Single Responsibility Principle
  * The SRP states that a class or module should have one and only one,
    *reason to change*. This principle gives us both a definition of
    responsibility and a guideline for class size. Classes should have one
    responsibility - one reason to change
  * We want our systems to be composed of many small classes, not a few
    large ones. Each small class encapsulates a single responsibility,
    has a single reason to change, and collaborates w/ a few others to
    achieve the desired system behavior
* Cohesion
  * Classes should have a small number of instance variables. Each of
    the methods of a class should manipulate one or more of those
    variables
  * In general, the more variables a method manipulates, the more
    cohesive that method is to its class. A class in which each variable
    is used by each method is maximally cohesive
  * In general it is neither advisable nor possible to create such
    maximally cohesive classes; on the other hand, we would llike
    cohesion to be high
  * When cohesion is high, it means that the methods and variables of
    the class are co-dependent and hang together as a logical whole
  * The strategy of keeping functions small and keeping parameter lists
    short can sometimes lead to a proliferation of instance variables
    that are used by a subset of methods. When this happens, it almost
    always means that there is at least one other class trying to get out of
    the larger class. You should try to separate the variables and methods
    into two or more classes such that the new classes are more cohesive
* Maintaining Cohesion Results in Many Small Classes
  * Breaking a large function into many smaller functions often gives
    the opportunity to split several smaller classes out as well. This
    gives our program a much better organization and a more transparent
    structure
* Organizing for Change
  * For most systems, change is continual. Every change subjects us to
    the risk that the remainder of the system no longer works as
    intended. In a clean system we organize our classes so as to reduce the
    risk change
  * We want to structure our systems so that we muck w/ as little as
    possible when we update them w/ new or changed features
  * In an ideal system, we incorporate new features by extending the
    system, not by making modifications to existing code
    * This follows the Open-Closed Principle, classes should be open for
      extension but closed for modification
* Isolating from Change
  * If a system is decoupled enough to be tested, it will also be more
    flexible and promote more reuse. The lack of coupling means that the
    elements of our system are better isolated from each other and from
    change. This isolate makes it easier to understand each element of a
    system
  * By minimizing coupling in this way, our classes adhere to another
    class design principle known as Dependency Inversion Priciple. In
    essence, the DIP says that our classes should depend upon abstractions,
    not on concrete details
