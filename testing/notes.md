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
