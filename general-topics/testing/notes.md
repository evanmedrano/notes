Testing notes
=============

2020-02-11
----------
* Use Component/Page/Experience objects for testing (helps DRY up code, and places logic in a more appropriate place)

2020-02-12
----------
* Use instance_doubles in testing to create a fake Active Record model in cases where I'm testing another class
* Watch out for view conditionals in testing (may be better off using a view spec)
* Use webmock gem to avoid hitting external services (like a webpage) or use something like [fake_stripe](https://github.com/thoughtbot/fake_stripe)
* Follow four-phase pattern: Setup, Exercise, Verify, Teardown (use a new line between phases)
* Make sure your test errors are clear (try mapping over arrays with an attribute for clear errors)
* Make the relationship between created fixtures in setup and the verification results clear (avoid mystery guest smell)
* Don't test private methods (Consider moving private methods into a new class w/ public interface for testing bugs)
* Don't include extraneous info in specs

2020-02-18
----------
* Getting good value from tests requires clarity of intention and knowing what, when, and how to test
* One simple way to get better value from tests is to write few of them. The safest way to accomplish this is to test everything just once
and in the proper place
* The design principles you are enforcing in your application apply to tests as well. Each test is merely another application object that
needs to use an existing class. The moer the test gets coupled to that class, the more entangled the two become and the more vulnerable the
test is to unnecessarily being forec to change
* Not only should you limit couplings, but the few you allow, should be stable things. The most stable thing about any object is its public
interface; which means that the tests you write should be for messages that are defined in public interfaces
* Tests should concentrate on teh incoming or outgoing messages that cross and object's boundaries
* Incoming messages make up the public interface of the receiving object
* The outgoing messages, are incoming into other objects and so are part of some other object's interface
* Tests that make assertions about the values that messages return are tests of *state*. Such tests commonly assert that the results
returned by a message equal an expected value
* The general rule is that objects should make assertions about state *only* for messages in their own public interfaces
* The fact that you don't need to test outgoing messages for state does not mean outgoing messages need no tests at all
* Some outgoing messages have no side effects and only matter to their senders. The sender cares about the result it gets back, but no other
part of the app cares if the message gets sent. Outgoing messages like this are know as *queries*
* Query do not need to be tested by the sending object. Query messages are part of the public interface of their receiver,
which already implements every necessary test of state
* Outgoing messages that do have side effects (a database record is saved) upon which your app depends are called *commands*
* It is the responsibility of the sending object to prove that they are  properly sent. Proving that a message gets sent is a test
of behavior, not state, and involves assertions about the number of times, and with what arguments, the message is sent
* Incoming messages should be tested for the state they return. Outgoing command messages should be tested to ensure they get sent.
Outgoing query messages should not be tested
* When testing, it's useful to think of your app's objects as divided into two major categories: the first contains the object you're testing,
the *object under test* and the second is everything else
* Your tests must know things about the first category, but remain as ignorant as possible about the second
* Pretend that the only information available during the test is that which can be gained from looking at the object under test
* It's better for tests to assume a viewpoint that sights along the edges of the object under  test, where they can know only about
messages that come and go
* Incoming messages out to have dependents. Some object *other than the original implementer* depends on each of these messages
* Do not test an incoming message that has no dependents; delete it. Your app is improved by ruthlessly eliminating code that is not actively being used
* The responsibility for testing a message's return value lies with its receiver. Doing so anywhere else duplicates tests and raises costs
* Mocks are tests of behavior. Instead of making assertions about what a message returns, mocks define an expectation that a message will get sent
* Mocks are meant to prove messages get sent, they return results only when necessary to get tests to run
