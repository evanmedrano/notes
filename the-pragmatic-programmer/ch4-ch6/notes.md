The Pragmatic Programmer notes
==============================

Chapter 4 - Pragmatic Paranoia
------------------------------
* Design by Contract (concept developed by Bertrand Meyer) is a simple yet
  powerful technique that focuses on documenting (and agreeing to) the rights
  and responsibilities of software modules to ensure program correctness
* What is a correct program? One that does no more and no less than it
  claims to do
* Every function and method in a software system does something. Before
  it starts that something, the function may have some expectation of
  the state of the world, and it may be able to make a statement about the
  state of the world when it concludes
* These expectations and claims are as follows:
  * *Preconditions* - what must be true in order for the routine to be
    called: the routine's requirements. A routine should never get
    called when its precondtions would be violated
  * *Postcondtions* - What the routine is guaranteed to do; the state of
    the world when the routine is done
  * *Class invariants* - A class ensures that this condition is always
    true from the perspective of the caller
* If all the routine's precondtions are met by the caller, the routine
  shall guarantee that all postconditions and invariants will be true
  when it completes
* Whatever happens, make no mistake that failure to live up to the
  contract is a bug. It is not something that should ever happen,
  which is why preconditions should not be used to perform things such
  as validate user-input
* A better approach than simply checking your inputs, is to not call a
  function if your arguments are out of range
* Write "lazy" code, be strict in what you will accept before you begin,
  and promise as little as possible in return
* Simply enumerating what the input domain range is, what the boundary
  conditions are, and what the routine promises to deliver-or, more
  importantly what it *doesn't* promise to deliver-before you write the
  code is a huge leap forward in writing better software
* One of the benefits of detecting problems as soon as you can is that
  you can crash earlier, and crashing is often the best thing you can do
* When your code discovers that something that was supposed to be
  impossible just happened, your program is no longer viable-anything it
  does from this point foward becomes suspect-so terminate it as soon as
  possible
* A dead program normally does a lot less damage than a crippled one
* Whenever you find yourself thinking "but of course that could never
  happen", add code to check it. The easiest way to do this is with
  assertions
* These checks are invaluable, if a parameter or a result should never
  be `null`, then check it explicitly
* Don't use assertions in place of real error handling. Assertions check
  for things that should never happen
* The function or object that allocates a resource should be responsible
  for deallocating it
* When in doubt, it always pays to reduce scope
* The basic pattern for resource allocation can be extended for routines
  that need more than one resource at a time - these are two
  suggestions:
  * Deallocate resources in the opposite order to that in which you
    allocate them (LIFO). That way you won't orphan resources if one
    resource contains references to another
  * When allocating the same set of resources in different places in
    your code, always allocate them in the same order. This will
    reduce the possibility of a deadlock
* Always take small, deliberate steps, checking for feedback and
  adjusting before proceeding. Consider the rate of feedback as your
  speed limit. You never take on a step or a task that's "too big"
* What's a task that is too big? Any task that requires "fortune
  telling"
* Instead of wasting effort designing for an uncertain future, you can
  always fall back on designing your code to be replaceable

Chapter 5 - Bend, or Break
--------------------------
* Decoupled code is easier to change
* The principle of Tell, Don't Ask says that you shouldn't make
  decisions based on the internal state of an object and then update
  that object. Doing so totally destroys the benefits of encapsulation,
  and in doing so, spreads the knowledge of the implementation
  throughout the code
* The Law of Demeter says that a method defined in class C should only
  call:
  * Other instance methods in C
  * Its parameters
  * Methods in objects that it creates, both on the stack and in the
    heap
  * Global variables (shy away from following this suggestion)
* Try not to have more than one "." when you access something. And
  *access something* also covers cases when you use intermediate
  variables
* There's an exception to the one-dot rule: the rule doesn't apply if
  the things you are chaining are really unlikely to change. In
  practice:
  * Anything in your app should be considered likely to change
  * Anything in a third-party library should be considered volatile
  * Libraries that come with the language are probably pretty stable,
    and so method chaining is not a huge problem
* Any mutable external resource is global data. If your app uses a
  database, datastore, file system, service API, and so on, it risks
  falling into the globalization trap. The solution is to make sure
  you always wrap these resources behind code that you control
* Keeping your code shy: having it only deal with things it directly
  knows about, will help keep your apps decoupled, and that will make
  them more amendable to change
* An *event* represents the availability of information
* If we write apps that respond to events, and adjust what they do based
  on those events, those apps will work better in the real world. Their
  users will find them to be more interactive, and the apps themselves
  will make better use of resources
* Strategies that can help with writing code that responds to events
  are:
  1. Finite State Machines
  2. The Observer Pattern
  3. Publish/Subscribe
  4. Reactive Programming and Streams
* We need to get back to thinking of programs as being something that
  transforms inputs into outputs instead of focusing on just the code
* Thinking of code as a series of (nested) transformations can be a
  liberating approach to programming. It takes a while to get used to,
  but once you've developed the habit you'll find your code becomes
  cleaner, your functions shorter, and your desings flatter
* Some alternatives to using inheritance in code are:
  * Interfaces and protocols
  * Delegation
  * Mixins and traits
* Parameterize your app using external configuration
  * Basically, look for anything you know will have to change that you
    can express outside your main body of code, and slap it into some
    configuration bucket
* Configuration as a service has a number of benefits
  * Multiple apps can share configuration information, with
    authentication and access control limiting what each can see
  * Configuration changes can be made globally
  * The configuration data can be maintained via a specialized UI
  * The configuration data becomes dynamic
