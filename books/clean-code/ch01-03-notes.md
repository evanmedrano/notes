Clean Code notes
================

Chapter 1 - Clean Code
----------------------
* **The Primal Conundrum**
  * Programmers face a conundrum of basic values. All developers with
    more than a few years of experience know that previous messes slow
    them down. And yet all developers feel the pressure to make messes in
    order to meet deadlines. In short, they don't take the time to go fast!
  * True professionals know that the second part of the conundrum is
    wrong. You will *not* make the deadline by making the mess. Indeed,
    the mess will slow you down instantly, and will force you to miss the
    deadline. The *only* way to make the deadline-the only way to go fast-is
    to keep the code as clean as possible at all times
* **The Art of Clean Code?**
  * A programmer who writes clean code is an artist who can take a blank
    screen through a series of transformations until it is an elegantly
    coded system
* **What Is Clean Code?**
  * Clean code is *pleasing* to read
  * Bad code tries to do too much, it has muddled intent and ambiguity
    of purpose. Clean code is *focused*. Each function, each class, each
    module exposes a single-minded attitude that remains entirely
    undistracted, and unpolluted, by surrounding details
  * Clean code shuld read like well-written prose
  * Our code should be matter-of-fact as opposed to speculative. It
    should contain only what is necessary
  * Clean code makes it easy for *other* people to enhance it
  * Clean code is code that has been taken care of
  * Simple code:
    * Runs all the tests
    * Contains no duplication
    * Expresses all the design ideas that are in the system
    * Minimizes the number of entities such as classes, methods,
      functions, and the like
  * When you read clean code, you won't be surpised at all
* **We Are Authors**
  * The ratio of time spend readign vs. writing is well over 10:1. We
    are *constantly* reading old code as part of the effort to write new
    code
  * We want the reading of code to be easy, even if it makes the writing
    harder. Of course there's no way to write code without reading it,
    so *making it easy to read actually makes it easier to write*
  * You cannot write code if you cannot read the surrounding code. The
    code you are trying to write today will be hard or easy to write
    depending on how hard or easy the surrounding code is to read. So if you
    want to go fast, if you want to get done quickly, if you want your code
    to be easy to write, make it easy to read

Chapter 2 - Meaningful Names
----------------------------
* **Use Intention-Revealing Names**
  * Choosing good names takes time but saves more than it takes. So take
    care with your names and change them when you find better ones
  * The name of a variables, function, or class, should answer all the
    big questions. It should tell you why it exists, what it does, and
    how it is used. if a name requires a comment, then the name does not
    reveal its intent
* **Avoid Disinformation**
  * Programmers must avoid leaving false clues that obscure the meaning
    of code. We should avoid words whose entrenched meanings vary from
    our intended meaning
* **Make Meaningful Distinctions**
  * Programmers create problems for themselves when they write code
    solely to satisfy a compiler or interpreter. It is not sufficient to
    add number series of noise words, even though the compiler is satisfied.
    If names must be different, then they should also mean something
    different
  * Distinguish names in such a way that the rader knows what the
    differences offer
* **Use Pronounceable Names**
  * A significant part of our brains is dedicated to the concept of
    words. And words are, by definition, pronounceable. It would be a
    shame not to take advantage of that huge portion of our brains that has
    evolved to deal with spoken language. So make your names pronounceable
* **Use Searchable Names**
  * Single-letter naems and numeric constants have a particular problem
    in that they are not easy to locate across a body of text
  * Longer names trump short names, and any searchable name trumps a
    constant in code
  * Single-letter names can ONLY be used as local variables inside short
    methods. *The length of a name should correspond to the size of its
    scope*
  * If a variable or constant might be seen or used in multiple places
    in a body of code, it is imperative to give it a search-friendly
    name
* **Avoid Mental Mapping**
  * Readers shouldn't have to mentally translate your names into other
    names they already know
  * One difference between a smart programmer and a professional
    programmer is that the professional understands that *clarity is
    king*. Professionals use their powers for good and write code that
    others can understand
* **Class Names**
  * Classes and objects should have noun or noun phrase names. Avoid
    words like `Manager`, `Data`, or `Info` in the name of a class. A
    class name should not be a verb
* **Method Names**
  * Methods should have verb or verb phrase names like `postPayment` or
    `save`. Accessors, mutators, and predicates should be named for
    their value and prefixed with `get`, `set`, and `is`
* **Don't Be Cute**
  * If names are too clever, they will be memorable only to people who
    share the author's senes of humor, and only as long as these people
    remember the joke
* **Pick One Word per Concept**
  * Pick one word for one abstract concept and stick with it. For
    instance, it's confusing to have `fetch`, `retrieve`, and `get` as
    equivalent methods of different classes
  * A consistent lexicon is a great boon to programmers who must use
    your code
* **Don't Pun**
  * Avoid using the same word for two purposes. Using the same term for
    two different ideas is essentially a pun
  * Our goal, as authors, is to maek our code as easy as possible to
    understand. We want our code to be a quick skim, not an intense
    study
* **Use Solution Domain Names**
  * Remember that the people who read your code will be programmers. So
    go ahead an use CS terms, algorithm names, pattern names, math
    terms, and so forth
  * There are lots of technical thing that programmers have to do.
    Choosing technical names for those things is usually the most
    appropriate course
* **Add Meaningful Context**
  * There are a few names which are meaningful in and of themselves-most
    are not. Instead, you need to place names in context for your reader
    by enclosing them in well-named classes, functions, or namespaces. When
    all else fails, then prefixing the name may be necessary as a last
    resort
* **Don't Add Gratuitous Context**
  * Shorter names are generally better than longer ones, so long as they
    are clear. Add no moer context to a name than is necessary

Chapter 3 - Functions
---------------------
* **Small!**
  * The first rule of functions is that they should be small. The second
    rule of functions is that *they should be smaller than that*
* **Block and Indenting**
  * This implies that the blocks within `if` statements, `else`
    statements, `while` statements, and so on should be one line long.
    Probably that line should be a function call. Not only does this keep
    the enclosing function small, but it also adds documentary value because
    the function called within the block can have a nicely descriptive name
  * This also implies that functions should not be large enough to hold
    nested structures. Therefore, the indent level of a function should
    not be greater than one or two. This, of course, makes the functions
    easier to read and understand
* **Do One Thing**
 * **FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD
   DO IT ONLY**
  * If a function does only those steps that are one level below the
    state name of the function, then the function is doing one thing.
    After all, the reason we write functions is to decompose a larger
    concept into a set of steps at the next level of abstraction
  * Another way to know that a function is doing more than "one thing"
    is if you can extract another function from it with a name that is
    not merely a restatement of its implementation
* **One Level of Abstraction per Function**
  * In order to make sure our functions are doing "one thing", we need
    to make sure that the statements within our function are all at the
    same level of abstraction
  * Mixing levels of abstraction within a function is always confusing.
    Readers may not be able to tell whether a particular expression is
    an essential concept or a detail
* **Reading Code from Top to Bottom: _The Stepdown Rule_**
  * We want the code to read like a top-down narrative. We want every
    function to be followed by those at the next level of abstraction so
    that we can read the program, descending one level of abstraction at a
    time as we read down the list of function
  * It turns out to be very difficult for programmers to learn to follow
    this rule and write functions that stay at a single level of
    abstraction. But learning this trick is also very important. It is the
    key to keeping functions short and making sure they do "one thing".
    Making the code read like a top-down set of *TO* paragraphs is an
    effective technique for keeping the abstraction level consistent
* **Switch Statements**
  * The general rule for `switch` statements is that they can be
    tolerated if they appear only once, are used to create polymorphic
    objects, and are hidden behind an inheritance relationship so that the
    rest of the system can't see them. Of course every circumstance is
    unique, and there are time when one or more parts of this rule is
    violated
* **Use Descriptive Names**
  * The smaller and more focused a function is, the easier it is to
    chooes a descriptive name
  * Don't be afraid to make a name long. A long descriptive name is
    better than a short enigmatic name. A long descriptive name is
    better than a long descriptive comment. Use a name convention that
    allows multiple words to be easily read in the function names, and then
    make use of those multiple words to give the function a name that says
    what it does
  * Be consistent in your names. Use the same phrases, nouns, and verbs
    in the function names you choose for your modules
* **Function Arguments**
  * The ideal number of arguments for a function is zero (niladic). Next
    comes one (monadic), followed closely by two (dyadic). Three
    arguments (triadic) should be avoided where possible. More than three
    (polyadic) requires very special justification-and then shouldn't be
    used anyway
* **Common Monadic Forms**
  * There are two very common reasons to pass a single argument into a
    function. You may be asking a question about that argument or you
    may be operating on that argument, transforming it into something else
    and *returning* it
  * A somewhat less common, but still useful form is an *event*. In this
    form there is an input argument but no output argument. The overall
    program is mean to interpret the function call as an event and use the
    argument to alter the state of the system
  * Try to avoid any monadic functions that don't follow these forms.
    Using an output argument instead of a return value for a
    transformation is confusing
* **Flag Arguments**
  * Flag arguments are ugly. Passing a boolean into a function is a
    truly terrible practice. It immediately complicates the signature of
    the method, loudly proclaiming that theis function does more than one
    thing. It does one thing if the flag is true and another if the flag is
    false
* **Dyadic Functions**
  * Dyads aren't evil, and you certainly will have to write them.
    However, you should be aware that they come at a cost and should take
    advantage of what mechanisms may be available to you to convert them to
    monads
* **Argument Objects**
  * When a function seems to need more than two or three arguments, it
    is likely that some of those arguments ought to be wrapped into a
    class of their own
* **Verbs and Keywords**
  * Choosing good names for a function can go a long way toward explaing
    the intent of the function and the order and intent of the
    arguments. In the case of a monad, the function and argument should form
    a very nice verb/noun pair
  * The *keyword* form of a function name, encodes the names of the
    arguments into the function name, example:
    `assertExpectedEqualsActual(expected, actual)`
* **Have No Side Effects**
  * Side effects are lies. Your function promises to do one thing, but
    it also does other *hidden* things. Sometimes it will make
    unexpected changes to the variables of its own class. Sometimes it will
    make them to parameters passed into the function or to system globals.
    In either case they are devious and damaging mistruths that often result
    in strange temporal couplings and other dependencies
  * In general output arguments should be avoided. If your function must
    change the state of something, have it change the state of its
    owning object
* **Command Query Separation**
  * Functions should either do something or answer something, but not
    both. Either your function should change the state of an object, or
    it should return some information about that object
* **Prefer Exceptions to Returning Error Codes**
  * Returning error codes from command functions is a subtle violation
    of command query separation. It promotes commands being used as
    expressions in the predicates of `if` statements
* **Extract Try/Catch Blocks**
  * `Try/catch` blocks are ugly in their own right. They confuse the
    structure of the code and mix error processing with normal
    processing. So it is better to extract the bodies of the `try` and
    `catch` blocks out into functions of their own
* **Error Handling Is One Thing**
  * Functions should do one things. Error handling is one thing. Thus, a
    function that handles errors should do nothing else. This implies
    that if the keyword `try` exists in the function, it should be the very
    first word in the function and that there should be nothing after the
    `catch/finally` blocks
* **Don't Repeat Yourself**
  * Duplication may be the root of all evil in software. Many principles
    and practices have been created for the purpose of controlling or
    eliminating it
* **How Do You Write Functions Like This?** (Uncle Bob's technique)
  * When I write functions, they come out long and complicated. They
    have lots of indenting and nested loops. They have long argument
    lists. The names are arbitrary, and there is duplicated code. But I also
    have a suite of unit tests that cover every one of those clumsly lines
    of code
  * I massage and refine that code, splitting out functions, changing
    names, eliminating duplication. I shrink the methods and reorder
    them. Sometimes I break out whole classes, all the while keeping the
    tests passing
  * In the end, I wind up with functions that follow the rules I've laid
    down in this chapter. I don't write them that way to start. I don't
    think anyone could
