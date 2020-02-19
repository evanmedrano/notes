The Pragmatic Programmer notes
==============================

Chapter 1 - A Pragmatic Philosophy
----------------------------------
* Instead of excuses, provide options. Don't say it can't be done;
  explain what *can* be done to salvage the situation
* When you find yourself saying, "I don't know", be sure to follow it up
  with-"but I'll find out". A solid way to admit what you don't know,
but then take responsibility like a pro
* Don't leave "broken windows" (bad designs, wrong decisions, or poor
  code). Fix each one as soon as it's discovered. Take *some* action to
prevent further damage and to show that you're on top of the situation
* You can discipline yourself to write software that's good enough--good
  enough for your users, for future maintainers, for your own peace of
mind. You'll find that you are more productive and your users are
happier
* The phrase "good enough" does not imply sloppy or poorly produced
  code. All systems must meet their users' requirements to be
successful, and meet basic performance, privacy, and security standards
* Surprisingly, many users would rather use software with some rough
  edgers today than wait a year for the shiny, bells-and-whistles
version
* Great software today is often preferable to the fantasy of perfect
  software tomorrow. If you give your users something to play with
early, their feedback will often lead you to a better eventual solution
* Managing a knowledge portfolio is very similar to managing a financial
  portfolio
  1. Serious investors invest regularly - as a habit
  2. Diversification is the key to long-term success
  3. Smart investors balance their portfolios between conservative and
     high-risk, high-reward investments
  4. Investors try to buy low and sell high for maximum return
  5. Portfolios should be reviewed and rebalanced periodically
* To be successful in your career, you must invest in your knowledge
  portfolio using the same guidelines
* Goals for investing in your knowledge portfolio
  1. Learn at least one new language every year
  2. Read a technical book each month
  3. Read nontechnical books too
  4. Take classes
  5. Participate in local user groups and meetups
  6. Experiment with different environments
  7. Stay current
* The last important point is to think *critically* about what your read
  and hear. You need to ensure that the knowledge in your portfolio is
accurate and unswayed by either vendor or media hype
* Tips for communication
  1. Know what you want to say
  2. Know your audience
  3. Choose your moment
  4. Choose a style
  5. Make it look good
  6. Involve your audience
  7. Be a listener
  8. Get back to people
  9. Keep code and documentation together

Chapter 2 - A Pragmatic Approach
--------------------------------
* A thing is well designed if it adapts to the people who use it. For
  code, that means it must adapt by changing. Believe in the ETC
principle: *Easier to Change*
* ETC is a value, not a rule - ETC is a guide, helping you choose
  between paths. Justl ike all your other values, it should be floating
just behind your conscious thought, subtly nudging you in the right
direction
* There's an implicit premise in ETC. It assumes that a person can tell
  which of many paths will be easier to change in the future
* Sometimes you won't have a clue, when that's the case you may be able
  to do two things
  1. First, given that you're not sure what form change will take, you
     can always fall back on the ultimate "easy to change" path: try to
     make what your write replaceable. That way, whatever happens in the
     future, this chunk of code won't be a roadblock
  2. Second, treat this as a way to develop instincts. Note the
     situation in your engineering day book: the choices you have, and
     some guesses about change. Leave a tag in the source. Then later, when
     this code has to change, you'll be able to look back and give yourself
     feedback. It might help the next time you reach a similar fork in the
     road
* *Every piece of knowledge must have a single, unambiguous,
  authoritative representation within a system*
* Don't repeat yourself (DRY) - DRY is about the duplication of
  *knowledge*, of *intent*. It's about expressing the same thing in two
different places, possibly in two totally different ways (doesn't only
mean not to copy-and-paste lines of source code)
* Not all code duplication is knowledge duplication - The code can
  sometimes be the same, but the knowledge they represent is different
* Whenever a module exposes a data structure, you're coupling all the
  code that uses that structure to the implementation of that module.
Where possible, always use accessor functions to read and write the
attributes of objects. It will make it easier to add functionality in
the future
* "Orthogonality" is a term borrowed from geometry - in computing, the
  term has come to signify a kind of independence or decoupling. Two or
more things are orthogonal if changes in one do not affect any of the
others
* In a well-designed system, the database code will be orthogonal to the
  user interface: you can change the interface without affecting the
database, and swap databases without changing the interface
* We want to design components that are self-contained: independent, and
  with a single, well-defined purpose
* When components are isolated from one another, you know that you can
  change one without having to worry about the rest
* You get two major benefits if you write orthogonal systems: increased
  productivity and reduced risk
* Systems should be composed of a set of cooperating modules, each of
  which implements functionality independent of others
* There is an easy test for orthogonal design: Once you have your
  components mapped out, ask yourself: *If I dramatically change the
requirements behind a particular function, how many modules are
affected?* -- In an orthogonal system, the answer should be "one"
* Ask yourself how decoupled your design is from changes in the real
  world - *Don't rely on the properties of things you can't control*
* Several techniques to maintain orthogonality
  1. Keep your code decoupled - if you need to change an object's state,
     get the object to do it for you
  2. Avoid global data
  3. Avoid similar functions
* Don't only keep your code flexible, you also need to think about
  maintaining flexibility in the areas of architecture, deployment, and
vendor integration
* Look for the important requirements, the ones that define the system.
  Look for the areas where you have doubts, and where you see the
biggest risks. Then prioritize your development so that these are the
first areas you code
* We build software prototypes to analyze and expose risk, and to offer
  chances for correction at a greatly reduced cost
* Things to prototype
  1. Anything that carries risk
  2. Anything that hasn't been tried before, or that is absolutely
     critical to the final system
  3. Anything unproven, experimental, or doubtful - anything you aren't
     comfortable with
* You can prototype:
  1. Architecture
  2. New functionality in an existing system
  3. Structure or contents of external data
  4. Third-party tools or components
  5. Performance issues
  6. User interface design
* Prototyping is a learning experience. It's value lies not in the code
  produced, but in the lessons learned
* When building a prototype, you can choose to ignore:
  1. Correctness
  2. Completeness
  3. Robustness
  4. Style
* Some things to consider when prototyping architecture:
  1. Are the responsibilities of the major areas well defined and
     appropriate?
  2. Are the collaborations between major components well defined?
  3. Is coupling minimized?
  4. Can you identify potential sources of duplication?
  5. Are interface definitions and constraints acceptable?
  6. Does every module have an access path to the data it needs during
     execution? Does it have that access *when* it needs it?
* What to say when asked for an estimate? *I'll get back to you*
* Iterate the estimation schedule with the code - help management
  understand that the team, their productivity, and the environment will
determine the schedule. By formalizing this, and refining the schedule
as part of each iteration, you'll be giving the, the most accurate
scheduling estimates you can
