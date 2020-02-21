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
