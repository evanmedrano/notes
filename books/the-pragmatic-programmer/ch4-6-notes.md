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

Chapter 6 - Concurrency
-----------------------
* *Concurrency* is when the execution of two or more pieces of code act
  as if they run at the same time
  * To have concurrency, you need to run code in an environment that can
    switch between different parts of your code when it is running. Often
    implemented using things such as fibers, threads, and prrocesses
* *Parallelism* is when they *do* run at the same time
  * To have parallelism, you need hardware they can do two things at once.
    This might be multiple cores in a CPU, multiple CPUs in a computer, or
    mupltiple computers connected together
* When people sit down to design an architecture or write a program,
  things tend to be linear. That's the way people think-do *this* and
  then always do *that*. But thinking this way leads to *temporal
  coupling*, coupling in time. This approach is not very flexible and
  not very realistic
* We need to allow for concurrency and to think about decoupling any
  time or order dependencies. In doing so, we gain flexibility and
  reduce any time-based dependencies in many areas of development:
  workflow analysis, architecture, design, and deployment
* On many projects, we need to model and analyze the app workflows as
  part of the design. One way to do this is to capture workflow using
  a notation such as the *activity diagram*
  * An activity diagram consists of a set of actions drawn as rounded
    boxes. The arrow leaving an action leads to either another action
    (which can start once the first action completes) or a thick line
    called a *synchronization bar*. Once *all* the actions leading into
    a synchronization bar are complete, you can then proceeed along any
    arrows leaving the bar. An action with no arrows leading into it can
    be started at any time
* When designing for concurrency, we're hoping to find activities that
  take time, but not time in our code
* Concurrency in a shared resource environment is difficult, and
  managing it yourself is fraught with challenges
* Actors and processes offer interesting ways of implementing
  concurrency w/o the burden of synchronizing access to shared memory
* An *actor* is an independent virtual processor with its own local (and
  private) state
* A *process* is typically a more general-purpose virtual processor,
  often implemented by the operating system to facilitate concurrency
* Actors can only be concurrent - there's no single *thing* that's in
  control. Nothing schedules what happens next, or orchestrates the
  transfer of info from the raw data to the final output
  * The only state in the system is held in messages and in the local
    state of each actor
  * All messages are one way-there's no concept of replying
  * An actor processes each message to completion, and only processes
    one message at a time - as a result, actors execute concurrently,
    asynchronously, and share nothing
* The actor and/or blackboard and/or microservice approach to
  architecture removes a whole class of potential concurrency problems
  from your apps. But that benefit comes at a cost. These approaches are
  harder to reason about, because a lot of the action is indirect. You'll
  find it helps to keep a central repository of message formats and/or
  APIs, particuarly if the repository can generate the code and
  documentation for you. You'll also need good tooling to be able to trace
  messages and facts as they progress through the system. (A useful
  technique is to add a unique *trace id* when a particular business
  function is initiated and the propagate it to all the actors involved.
  You'll then be able to reconstruct what happens from the log files
