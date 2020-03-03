Clean Code notes
================

Chapter 4 - Comments
--------------------
* The proper use of comments is to compensate for our failure to express
  ourself in code
* So when you find yourself in a position where you need to write a
  comment, think it through and see whether there isn't some way to turn
  the tables and epxress yourself in code
* Comments lie. Not always, and not intentionally, but too often. The
  older a comment is, and the farther away it is from the code it
  describes, the more likely it is to be just wrong. The reason is simple.
  Programmers can't realistically maintain them
* Programmers should be disciplined enough to keep the comments in a
  high state of repair, relevance, and accuracy. However, try to put
  that energy towards making the code so clear and expressive that it does
  not need the comments in the first place
* Inaccurate comments are far worse than no comments at all. They delude
  and mislead. They set expectations that will never be fulfilled. They
  lay down old rules that need not, or should not, be followed any longer
* Truth can only be found in one place: the code. Only the code can
  truly tell you what it does
* **Comments Do Not Make Up for Bad Code**
  * Clear and expressive code with few comments is far superior to
    cluttered and complex code with lots of comments. Rather than spend
    your time writing the comments that explain the mess you've made, spend
    it cleaning that mess
* **Good Comments**
  * Legal Comments
    * For example, copyright and authorship statements are necessary and
      reasonable things to put into a comment at the start of each
      source file
  * Informative Comments
    * It is sometimes useful to provide basic info with a comment. For
      example, explaining the return value of an abstract method
  * Explanation of Intent
    * Sometimes a comment goes beyond just useful info about the
      implementation and provides the intent behind a decision
  * Clarification
    * Sometimes it is just helpful to translate the meaning of some
      obscure argument or return value into something that's readable
  * Warning of Consequences
    * Sometimes it is useful to warn other programmers about certain
      consequences
  * TODO Comments
    * It is sometimes reasonable to leave "To do" notes in the form of
      `//TODO` comments
    * `TODOs` are jobs that the programmer thinks should be done, but for
      some reason can't do at the moment
    * Whatever the reason for the TODO might be, it is *not* an excuse
      to leave bad code in the system
  * Amplification
    * A comment may be used to amplify the importance of something that
      may otherwise seem inconsequential
* **Bad Comments**
  * Mumbling
    * Any comment that forces you to look in another module for the
      meaning of that comment has failed to communicate to you and is
      not worth the bits it consumes
  * Redundant Comments
  * Misleading Comments
  * Mandated Comments
  * Journal Comments
  * Noise Comments
  * Scary Noise
  * Don't use a comment when you can use a function or a variable
  * Position Markers
    * Think of it this way. A banner is a startling and obvious if you
      don't see banners very often. So use them very sparingly, and only
      when the benefit is significant. If you overuse banners, they'll fall
      into the background noise and be ignored
  * Closing Brace Comments
    * Although this might make sense for long functions with deeply
      nested structures, it serves only to clutter the kind of small and
      encapsulated functions that we prefer. So if you find yourself wanting
      to mark your closing braces, try to shorten your functions instead
  * Commented-Out Code
    * Others who see the commented-out code won't have the courage to
      delete it. They'll think it is there for a reason and is too
      important to delete
  * HTML Comments
    * HTML in source code comments is an abomination. It makes the
      comments hard to read in the one place where they should be easy
      to read-the editor/IDE
  * Nonlocal Information
    * If you must write a comment, then make sure it describes the code
      it appears near. Don't offer systemwide info in the context of a
      local comment
  * Too Much Information
  * Inobvious Connection
  * Function Headers

Chapter 5 - Fomatting
---------------------
* The Purpose of Formatting
  * Code formatting is about communication, and communication is the
    professional developer's first order of business
* The Newspaper Metaphor
  * We would like a source file to be like a newspaper article. The name
    should be simple but explanatory. The name, by itself, should be
    sufficient to tell us whether we are in the right module or not. The
    topmost parts of the source file should provide the high-level concepts
    and algorithms. Detail should increase as we move downward, until at the
    end we find the lowest level functions and details in the source file
* Vertical Openness Between Concepts
  * Nearly all code is read left to right and top to bottom. Each line
    represents an expression or a clause, and each group of lines
    represesnts a complete thought. Those thoughts should be separated from
    each other with blank lines
* Vertical Density
  * If openness separates concepts, then vertical density implies close
    associations. So lines of code that are tightly related should appear
    vertically dense
* Vertical Distance
  * Concepts that are closely related should be kept vertically close to
    each other. Clearly this rule doesn't work for concepts that belong
    in separate files. But then closely related concepts should not be
    separated into different files unless you have a very good reason
* Variable Declarations
  * Variables should be declared as close to their usage as possible.
    Because our functions are very short, local variables should appear
    at the top of each function
  * Instance variables should be declared at the top of the class. This
    should not increase the vertical distance of these variables,
    because in a well-designed class, they are used by many, if not all, of
    the methods of the class
* Dependent Functions
  * If one function calls another, they should be vertically close, and
    the caller should be above the callee, if at all possible. This
    gives the program a natural flow. If the convention is followed
    reliably, readers will be able to trust that function definations will
    follow shortly after their use
* Conceptual Affinity
  * Certain bits of code *want* to be near other bits. They have a
    ceratin conceptual affinity. The stronger that affinity, the less
    vertical distance there should be between them
* Vertical Ordering
  * In general we want function call dependencies to point in the
    downward direction. That is a function that is called should be
    below a function that does the calling. This creates a nice flow down
    the source code module from high level to low level
* Horizontal Formatting
  * We should strive to keep our lines short. The old Hollerith limit of
    80 is a bit arbitrary, but try not to have lines over 100 to 120
* Horizontal Openness and Density
  * We use horizontal white space to associate things that are strongly
    related and disassociate things that are more weakly related
* Horizontal Alignment
  * The alignment of variable names, or all the values in a set of
    assignment statements is not useful. The alignment seems to
    emphasize the wrong things and leads the eye away from the true intent
  * If you have long lists that need to be aligned, *the problem is the
    length of the lists*, not the lack of alignment. The length of the
    list of declarations can suggest that a class should be split up
* Breaking Indentation
  * You may be tempted to break an indentation rule for short `if`
    statements, short `while` loops, or short functions - but you may
    find yourself going back to put the indentation back in. So try to avoid
    collapsing scopes down to one line

Chapter 6 - Objects and Data Structures
---------------------------------------
* Data Abstraction
  * Hiding implementation is not just a matter of putting a layer of
    functions between the variables. Hiding implementation is about
    abstractions! A class does not simply push its variables out through
    getters and setters. Rather it exposes abstract interfaces that allow
    its users to manipulate the *essence* of the data, w/o having to know
    the implementation
  * We do not want to expose the details of our data. Rather we want to
    express our data in abstract terms. This is not merely accomplished
    by using interfaces and/or getters and setters. Serious thought needs to
    be put into the best way to represent the data that an object contains.
    The worst option is to blithely add getters and setters
* Data/Object Anti-Symmetry
  * Procedural code (code using data structures) makes it easy to add
    functions w/o changing the existing data structures. OO code, on the
    other hand, makes it easy to add new classes w/o changing existing
    function
  * Procedural code makes it hard to add new data structures because all
    the functions must change, OO code makes it hard to add new
    functions because all the classes must change
* The Law of Demeter
  * The Law of Demeter says that a method `f` of class `C` should only
    call the methods of these:
    * `C`
    * An object created by `f`
    * An object passed as an argument to `f`
    * An object held in an instance variable of `C`
  * The method should *not* invoke methods of objects that are returned
    by any of the allowed functions. In other words, talk to friends,
    not strangers
* Hybrids
  * This confusion sometimes leads to unfortunate hybrid structures that
    are half object and half data structure. They have functions that do
    significant things, and they also have either public variables or public
    accessors and mutator that, for all intents and purposes, make the
    private variables public, tempting other external functions to use those
    variables the way a procedural would use a data structure
  * Avoid creating them. They are indicative of a muddled design whose
    authors are unsure of - or worse, ignorant of - whether they need
    protection from functions or types
* Data Transfer Objects
  * The quintessential form of a data structure is a class w/ public
    variables and no functions. This is sometimes called a data transfer
    object, or DTO. DTOs are very uesful structures, especially when
    communicating w/ databases or parsing messages from sockets and so on.
    They often become the first in a series of translation stages that
    convert raw data in a database into objects in the application code
* Active Record
  * Active Record are special forms of DTOs. They are data structures
    w/ a public variables; but they typically have navigational methods
    like `save` and `find`. Typically these Active Records are direct
    translations from database tables, or other data sources.
  * Unfortunately we often find that developers try to treat these data
    structures as though they were objects by putting business rule
    methods in them. This is awkward because it created a hybrid between a
    data structure and an object
  * The solution, of course, is to treat Active Record as a data
    structure and to create separate objects that contain the business
    rules and that hide their internal data (which are probably just
    instances of the Active Record)
* Conclusion
  * Objects expose behavior and hide data. This makes it easy to add new
    kinds objects w/o changing existing behaviors. It also makes it hard
    to add new behaviors to existing objects.
  * Data structures expose data and have no significant behavior. This
    makes it easy to add new behaviors to existing data structures but
    makes it hard to add new data structures to existing functions
