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

Chapter 11 - Systems
--------------------
* Separate Constructing a System from Using It
  * Software systems should separate the startup process, when the
    application objects are constructed and the dependencies are "wired"
    together, from the runtime logic that takes over after startup
  * The startup process is a *concern* that any application must address.
    The *separation of concerns* is one of the oldest and most important
    design techniques in our craft
  * Unfortunately most apps don't separate this concern. The code for
    the startup process is ad hoc and it is mixed in with the runtime
    logic
  * If we are *diligent* about building well-formed and robust systems,
    we shuld never let little, *convenient* idioms lead to modularity
    breakdown
  * The startup process of object construction and wiring is no
    exception. We should modularize this process separately from the
    normal runtime logic and we should make sure that we have a global,
    consistent strategy for resolving our major dependencies
* Separation of Main
  * One way to separate construction from use is simply to move all
    aspects of construction to `main`, or modules called by `main`, and
    to design the rest of the system assuming that all objects have been
    constructed and wired up appropriately
  * The flow of control is easy to follow. The `main` function builds
    the objects necessary for the system, then passes them to the app,
    which simply uses them
* Dependency Injection
  * A powerful mechanism for separating construction from use is
    *Dependency Injection*, the application of *Inversion of Control* to
    dependency management
  * Inversion of Control moves secondary responsibilities from an object
    to other objects that are dedicated to the purpose, thereby
    supporting the *Single Responsibility Principle*
  * In the context of dependency management, an object should not take
    responsiblity for instantiating dependencies itself. Instead, it
    should pass this responsibility to another "authoritative" mechanism,
    thereby inverting the control
  * Because setup is a global concern, this authoritative mechanism will
    usually be either the "main" routine or a special purpose
    *container*
  * True Dependency Injection goes one step further. The class takes no
    direct steps to resolve its dependencies; it is completely passive.
    Instead, it provides setter methods or constructor arugments (or both)
    that are used to *inject* the dependencies. During the construction
    process, the DI container instantiates the required objects (usually on
    demand) and uses the constructor arguments or setter methods provided to
    wire together the dependencies. Which dependent objects are actually
    used is specified through a configuration file or programmatically in a
    special-purpose construction module
* Scaling Up
  * Software systems are unique compared to physical systems. Their
    architectures can grow incrementally, if we maintain the proper
    separation of concerns
* Test Drive the System Architecture
  * An optimal system architecture consists of modularized domains of
    concern, each of which is implemented w/ Plain Old Java (or other)
    Objects. The different domains are integrated together w/ minimally
    invasive Aspects or Aspect-like tools. This architecture can be
    test-driven, just like the code
* Optimize Decision Making
  * The agility provided by a POJO system with modularized concerns
    allows us to make optimal, just-in-time decisions, based on the most
    recent knowledge. The complexity of these decisions is also reduced
* Use Standards Wisely, When They Add Demonstrable Value
  * Standards make it easier to reuse ideas and components, recruit
    people w/ relavent experience, encapsulate good ideas, and wire
    components together. However, the process of creating standards can
    sometimes take too long for industry to wait, and some standards lose
    touch w/ the real needs of the adopters they are intended to sever
* Systems Need Domain-Specific Language
  * Domain-Specific Language allow all levels of abstraction and all
    domains in the application to be expressed as POJOs, from high-level
    policy to low-level details
* Conclusion
  * Whether you are designing systems or individual modules, never
    forget to *use the simplest thing that can possibly work*

Chapter 12 - Emergence
----------------------
* Getting Clean via Emergent Design
  * According to Kent, a design is "simple" if it follows these rules:
    * Runs all the tests
    * Contains no duplication
    * Expresses the intent of the programmer
    * Minimizes the number of classes and methods
* Simple Design Rule 1: Run All the Tests
  * A system that is comprehensively tested and passes all of its tests
    all of the time is a testable system
  * Systems that aren't testable aren't verifiable. Arguably, a system
    that can't be verified should never be deployed
  * Fortunately, making our systems testible pushes us toward a design
    where our classes are small and single purpose
  * The more tests we write, the more we'll continue to push toward
    things that are simpler to test
  * Tight coupling makes it difficult to write tests. So, similarly, the
    more tests we write, the more we use principles like DIP and tools
    like dependency injection, interfaces, and abstraction to minimize
    coupling. Our designs improve even more
* Simple Design Rule 2-4: Refactoring
  * Once we have tests, we are empowered to keep our code and classes
    clean. We do this by incrementally refactoring the code. For each
    few lines of code we add, we pause and reflect on the new design. Did we
    just degrade it? If so, we clean it up and run out tests to demonstrate
    that we haven't broken anyting. *The fact taht we have these tests
    eliminate the fear of cleaning up the code will break it*
  * During this refactoring step, we can apply anything from the entire
    body of knowledge about good software design. We can increase
    cohesion, decrease coupling, separate concerns, modularize system
    concerns, shrink our functions and classes, choose better names, and so
    on. This is also where we apply the finall three rules of simple design:
    Eliminate duplication, ensure expressiveness, and minimize the number of
    classes and methods
* No Duplication
  * Duplication manifests itself in many forms. Lines of code that looks
    exactly alike are, of course, duplication. Lines of code that are
    similar can often be massaged to look even more alike so they can be
    more easily refactored. And duplication can exist in other forms such as
    duplication of implementation
  * As we extract commonality at this very tiny level, we start to
    recognize violations of SRP. So we might move a newly extracted
    method to another class. That elevates its visibility
  * Someone else on the team may recognize the opportunity to further
    abstract the new method and resuse it in a different context
  * This "reuse in the small" can cause system complexity to shrink
    dramatically. Understanding how to achieve reuse in the small is
    essential to achieving reuse the large
  * The `Template Method` pattern is a common technique for removing
    higher-level duplication
    * The subclasses fill in the "hole", supplying the only bits of
      information that are not duplicated
* Expressive
  * The majority of the cost of a software project is in long-term
    maintenance. In order to minimize the potential for defects as we
    introduce change, it's critical for us to be able to understand what a
    system does. As systems become more complex, they take more and more
    time for a developer to understand, and there is an ever greater
    opportunity for a misunderstanding. Therefore, code should clearly
    express the intent of its author. The clearer the author can make the
    code, the less time others will have to spend understanding it. This
    will reduce defects and shrink the cost of maintenance
  * You can express yourself by choosing good names. We want to be able
    to hear a class or function name and not be surprised when we
    discover its responsibilites
  * You can also express yourself by keeping your functions and classes
    small. Small classes and functions are usually easy to name, easy to
    write, and easy to understand
  * Well-written unit tests are also expressive. A primary goal of tests
    is to act as documentation by example. Someone reading our tests
    should be able to get a quick understanding of what a class is all
    about
  * The most important way to be expressive is to *try*. All too often
    we get our code working and them move on to the next problem w/o
    giving sufficient thought to making that code easy for the next person
    to read. Remember, the most likely next person to read the code will be
    you
* Minimal Classes and Methods
  * Even concepts as fundamental as elimination of duplication, code
    expressiveness, and the SRP can be taken too far. In an effort to
    make our classes and methods small, we might create too many classes and
    methods. So this rule suggests that we also keep our function and class
    counts low
  * High class and method counts are sometimes the result of pointless
    dogmatism
  * Our goal is to keep our overall system small while we are also
    keeping out functions and classes small. Remember, however, that
    this rule is the lowest priority of the four rules of Simple Design. So,
    although, it's important to keep class and function count low, it's more
    important to have tests, eliminate duplication, and express yourself
