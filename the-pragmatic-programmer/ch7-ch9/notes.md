The Pragmatic Programmer notes
==============================

Chapter 7 - While You Are Coding
--------------------------------
* Tips for dealing with the fear of the blank page while coding
  * Stop what you're doing. Give yourself a little time and space to let
    your brain organize itself. Stop thinking about the code, and do
    something that is fairly mindless for a while, away from a keyboard
  * If that's not working, try externalizing the issue. Make doodles
    about the code you're writing, or explain it to a coworker
    (preferably one who isn't a programmer) or to your rubber duck.
    Expose different parts of your brain to the issue and see if any of
    them have a better handle on the thing that's troubling you
  * Tell yourself you need to prototype something and do the following:
    1. Write "I'm prototyping" on a sticky note and stick it on the side
       of your screen
    2. Remind yourself that prototypes are meant to fail. And remind
       yourself that prototypes get thrown away, even if they don't
       fail. There is no downside to doing this
    3. In your empty editor buffer, create a comment describing in one
       sentence what oyu want to learn or do
    4. Start coding
  * With this, hopefully the nervousness is gone and you know what to
    do. Delete all the prototype code, throw away the sticky note, and
    fill that empty editor buffer with bright, shiny new code
* We should avoid programming by coincidence-relying on luck and
  accidental successes-in favor of *programming deliberately*
* Reasons to take a risk messing with something that's working:
  * It may no really be working-it might just look like it is
  * The boundary condition you rely on may be just an accident
  * Undocumented behavior may change with the next release of the
    library
  * Additional and unnecessary calls make your code slower
  * Additional calls increase the risk of introducing new bugs of their
    own
* How to program deliberately:
  * Always be aware of what you are doing
  * Can you explain the code, in detail, to a more junior programmer? If
    not, perhaps you are relying on coincidence
  * Don't code in the dark. Build an app you don't fully grasp, or use a
    technology you don't understand, and you'll likely be bitten by
    coincidences
  * Proceed from a plan, whatever the source may be
  * Rely only or reliable things. Don't depend on assumptions. If you
    can't tell if osmething is reliable, assume the worst
  * Document your assumptions - this can help clarify your assumptions
    in your own mind, as well as communicate to others
  * Don't just test your code, but test your assumptions as well
  * Prioritize your effort. Spend time on the important aspects; more
    than likely, these are the hard parts
  * Don't be a slave to history. Don't let existing code dictate future
    code. All code can be replaced if it is no longer appropriate
* Regarding algorithm speed, if the numbers depend on external factors
  (such as the number of records in an overnight batch run, or the
  number of names in a list of people), then you might want to stop and
  consider the effect that large values may have on your running time or
  memory consumption
* You also need to be pragmatic about choosing appropriate
  algorithms-the fastest one is not always the best for the job
* Also be wary of *premature optimization*. It's always a good idea to
  make sure an algorithm really is a bottleneck before investing oyur
  precious time trying to improve it
* Refactoring is not intended to be a special, high ceremony,
  once-in-a-while activity, refactoring is a day-to-day activity
* Instead of a free for all, wholesale rewrite of the codebase, it's a
  targeted, precision approach to help keep the code easy to change
* You refactor when you've learned something, when you understand
  something better than you did last year, yesterday, or even just ten
  minutes ago
* Things that qualify for refactoring:
  * Duplication
  * Nonorthogonal design
  * Outdated design
  * Usage
  * Performance
  * The Tests Pass
* How to refactor without doing more harm then good:
  * Don't try to refactor and add functionality at the same time
  * Make sure you have good tests before you begin refactoring and run
    the tests as often as possible
  * Take short, deliberate steps: move a field from one class to
    another, split a method, rename a variable
* The biggest benefit offered by testing: testing is vital feedback that
  guides your coding
* The basic TDD cycle:
  1. Decide on a small piece of functionality you want to add
  2. Write a test that will pass once that functionality is implemented
  3. Run all tests. Verify that the only failure is the one you wrote
  4. Write the smallest amount of code needed to get the test to pass,
     and verify that the tests now run cleanly
  5. Refactor your code: see if there is a way to improve on what you
     just wrote (the test of the function). Make sure tests still pass
* Don't become a slave to TDD
  * Spending too much time ensuring that you have 100% test coverage
  * Many redundant tests
* Build software incrementally. Build small pieces of end-to-end
  functionality, learning about the problem as you go
* With unit testing, we want to test taht the module delivers the
  functionality it promises, over a wide-range of test cases and
  boundary conditions
* Security basic principles:
  1. Minimize attack surface area
  2. Principle of least privilege
  3. Secure defaults
  4. Encrypt sensitive data
  5. Maintain security updates
* Things should be named according to the role they play in your code.
  This means that, whenever you create something, you need to pause and
  think, "what is my motivation to create this?"
* Be consistent when naming things and honor the culture

Chapter 8 - Before the Project
------------------------------
* No one knows exactly what they want
* Programmers help pepole understand what they want
* The Pragmatic Programmer looks at *all* of the project as a
  requirements gathering exercise. That's why you should prefer short
  iterations: onces that end with direct client feedback. That will keep
  you on track, and makes sure that if you do go in the wrong direction,
  the amount of time lost is minimized
* Work with a User to think like a User
* Policy is Metadata
* Create and maintain a *project glossary*-one place that defines all
  the specific terms and vocabulary used in a project. All participants
  in the project, from end users to support staff, should use the glassary
  to ensure consistency. This implies that the glossary needs to be widely
  accessible-a good argument for online documentation
* The key to solving puzzles is both to recognize the constraints placed
  on you and to recognize the degrees of freedom you *do* have, for in
  those you'll find your solution
* Sometimes you will find yourself working on a problem that seems much
  harder than you thought it should be. Maybe it feels like you're going
  down the wrong path-that there must be an easier way to than this
    * This is an ideal time to do something else for a while. Work on
      something different. Go walk the dog. Sleep on it
    * Your conscious brain is aware of the problem, but your conscious
      brain can be pretty dumb. So it's time to give your real brain,
      that amazing associative neural net that lurks below your consciousness,
      some space. You'll be amazed how often the answer will just pop into
      your head when you deliberately distract yourself
    * If you're still not willing to drop the problem for a while, the
      next best thing is probably finding someone to explain it to.
      Often, the distraction of simply talking about it will lead to
      enlightenment. Have them ask questions such as:
      * Why are you solving this problem?
      * What's the benefit of solving it?
      * Are the problems you're having related to edge cases? Can you
        eliminate them?
      * Is there a simpler, related problem you can solve?
* When it comes to observation, fortune favors the prepared mind, this
  is true for problem solving too
* In order to have those *eureka!* moments, your nonconscious brain
  needs to have plenty of raw material; prior experiences that can
  contribute to an answer
* A great way to feed your brain is to give it feedback on what works
  and what doesn't work as you do your daily job
* Tips for pair/mob programming:
  * Build the code, not your ego. It's not about who's brightest: we all
    have our moments, good and bad
  * Start small. Mob with only 4-5 people, or start with just a few
    pairs, in short sessions
  * Criticize the code, not the person
  * Listen and try to understand others' viewpoints. Different isn't
    wrong
  * Conduct frequent retrospectives to try and improve for next time
* But don't just jump in with a naive approach: there are rules,
  suggestions, and guidelines for each of these development styles. For
  instance, with mob programming, you swap out the typist every 5-10
  minutes
* Don't go into the code alone
* Agile is not a noun, agile is how you do things
* The Pragmatic Programmer manifesto:
  * **Individuals and interactions** over processes and tools
  * **Working software** over comprehensive documentation
  * **Customer collaboration** over contract negotiation
  * **Responding to change** over following a plan
* The recipe for working in an agile way:
  1. Work out where you are
  2. Make the smallest meaningful setep towards where you want to be
  3. Evaluate where you end up, and fix anything you broke
* Repeat these steps until you're done. And use them recursively, at
  every level of everything you do
