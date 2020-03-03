Clean Code notes
================

Chapter 7 - Error Handling
--------------------------
* The connection between error handling to clean code should be clear.
  Many code bases are completely dominated by error handling. It is
  nearly impossible to see what teh code does becaues of all the scattered
  error handling. Error handling is important, *but if it obsures logic,
  it's wrong*
* Write Your `Try-Catch-Finally` Statement First
  * In a way, `try` blocks are like transactions. Your `catch` has to
    leave your program in a consistent state, no matter what happens in
    the `try`. For this reason, it is good practice to start with a
    `try-catch-finally` statement when you are writing code that could throw
    exceptions. This helps you define what the user of that code should
    expect, no matter what goes wrong with the code that is executed in the
    `try`
  * Try to write tests that force exceptions, and then add behavior to
    your handler to satisfy your tests. This will cause you to build the
    transaction scope of the `try` block first and will help you maintain
    the transaction nature of that scope
* Provide Context with Exceptions
  * Each exception that your throw should provide enough context to
    determine the source and location of an error
  * Create informative error messages and pass them along with your
    exceptions. Mention the operation that failed and the type of
    failure. If you are logging in your app, pass along enough info to be
    able to log the error in your `catch`
* Define Exception Classes in Terms of a Caller's Needs
  * There are many ways to classify errors. We can classify them by
    their source or their type. However, when we define excpetion
    classes in an app, our most important concern should be *how they are
    caught*
  * Wrapping third-party APIs is a best practice. When you wrap a
    third-party API, you minimize your dependencies on it. You can
    choose to move to a different library in the future w/o much penalty.
    Wrapping also makes it easier to mock out third-party calls when you are
    testing you own code
  * One final advantage of wrapping is that you aren't tied to a
    particular vendor's API design choices. You can define an API that you
    feel comfortable with
* Don't Return Null
  * When we return `null`, we are essentially creating work for
    ourselves and foisting problems upon our callers. All it takes is
    one missing `null` check to send an app spinning out of control
  * If you are tempted to return `null` from a method, consider throwing
    an exception or returning a `SPECIAL CASE` object instead
* Don't Pass Null
  * Returning `null` from methods is bad, but passing `null` into
    methods is worse. Unless you are working with an API which expects
    you to pass `null`, you should avoid passing `null` in your code
    whenever possible

Chapter 8 - Boundaries
----------------------
* Exploring and Learning Boundaries
  * It's not our job to test the third-party code, but it may be in our
    best interest to write tests for the third-party code we use
  * Learning the third-party code is hard. Integrating the third-party
    code is hard too. Doing both at the same time is doubly hard. What
    if we took a diff approach? Instead of experimenting and trying out the
    new stuff in our production code, we could write some tests to explore
    our understanding of third-party code. Jim Newkirk calls such tests
    `learning tests`
  * In learning tests we call the third-party API, as we expect to use
    in our app. We're essentially doing controlled experiments that
    check our understanding of that API. The tests focus on what we want out
    of the API
* Learning Tests Are Better Than Free
  * The learning test end up cosing nothing. We had to learn the API
    anyway, and writing those tests was an easy and isolated way to get
    that knowledge
  * Not only are learning tests free, they have a positive ROI. When
    there are new releases of the third-party package, we run the
    learning tests to see whether there are behavioral differences
  * Whether you need the learning provided by the learning tests or not,
    a clean boundary should be supported by a set of outbound tests that
    exercise the interface the same way the porduction code does. W/o these
    *boundary tests* to ease the migration, we might be tempted to stay with
    the old version longer than we should
* Clean Boundaries
  * Code at the boundaries needs clear separation and tests that define
    expectations. We should avoid lettings too much of our code know
    about third-party particulars. It's better to depend on something *you*
    control than on something you don't control, lest it end up controlling
    you
  * We manage third-party boundaries by having very few places in the
    code that refer to them

Chapter 9 - Unit Tests
----------------------
* The There Laws of TDD
  * **First Law** - You may not write production code until you have
    written a failing unit test
  * **Second Law** - You may not write more of a unit test than is
    sufficient to fail, and not compiling is failing
  * **Third Law** - You may not write more production code than is
    sufficient to pass the currently failing test
* Keeping Tests Clean
  * *Test code is just as important as production code*. It requires
    thought, design, and care. It must be kept as clean as production
    code
* Tests Enable the -ilities
  * If you don't keep your tests clean, you will lose them. And w/o
    them, you lose the very thing that keeps your production code
    flexible
  * It is *unit tests* that keeps your code flexible, maintainable, and
    reusable
  * If you have tests, you do not fear making changes to the code
  * W/o tests, every change is a possible bug. No matter how flexible,
    your architecture is, no matter how nicely partitioned your design,
    w/o tests you will be reluctant to make changes because of the fear that
    you will introduce undetected bugs
* Clean Tests
  * Readability is the key to clean tests. Readability is perhaps even
    more important in unit tests than it is in production code
  * What makes tests readable? The same thing that makes all code
    readable: clarity, simplicity, and density of expression
  * In a test, you want to say a lot w/ as few expressions as possible
  * The `BUILD-OPERATE-CHECK` pattern is a way to structure your tests.
    Each tests is cleary split into three parts. The first parts builds
    up the tests data, the second part operations on that test data, and the
    third part checks that the operation yielded the expected results
* One Assert per Test
  * This is a useful guideline. But don't be afraid to put more than one
    assert in a test. The best thing to say is that the number of
    asserts in a test ought to be minimized
* Single Concept per Test
  * Perhaps a better rule is that we want to test a single concept in
    each test function. We don't want long test functions that go
    testing miscellaneous thing after another
  * So probably the best rule is that you should minimize the number of
    asserts per concept and test just one concept per test function
* F.I.R.S.T
  * Clean tests follow five other rules that form the above acronym:
  * **Fast** - Tests should be fast. Tests should run quickly. When
    tests run slow, you won't want to run them frequently. If you don't
    run them frequently, you won't find problems early enough to fix them
    easily. You won't feel as free to clean up the code
  * **Independent** - Tests should not depend on each other. One test
    should not set up the conditions for the next test. You should be
    able to run each test independently and run the tests in any order you
    like
  * **Repeatable** - Tests should be repeatable in any environment. You
    should be able to run the tests in the production environment, in
    the QA environment, and on your laptop while riding the subway w/o a
    network. If your tests aren't repeatable in any environment, then you'll
    always have an excuse for why they fail
  * **Self-Validating** - The tests should have a boolean output. Either
    they pass or fail. You should not have to read through a log file to
    tell whether the tests pass. If the tests are not self-validating, then
    failure can become subjective and running tests can require a long
    manual evaluation
  * **Timely** - The tests need to be written in a timely fashion. Unite
    tests should be written *just before* the production code that makes
    them pass. If you write tests after the production code, then you may
    find the production code to be hard to test. You may decide that some
    production code is too hard to test. You may not design the production
    code to be testable
