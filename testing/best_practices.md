Testing Best Practices
======================
* Avoid any_instance in rspec-mocks and mocha. Prefer dependency injection.
* Avoid its, specify, and before in RSpec.
* Avoid let (or let!) in RSpec. Prefer extracting helper methods, but do not re-implement the functionality of let.
* Avoid using subject explicitly inside of an RSpec it block.
* Avoid using instance variables in tests.
* Disable real HTTP requests to external services with WebMock.disable_net_connect!.
* Don't test private methods.
* Test background jobs with a Delayed::Job matcher.
* Use stubs and spies (not mocks) in isolated tests.
* Use a single level of abstraction within scenarios.
* Use an it example or test method for each execution path through the method.
* Use assertions about state for incoming messages.
* Use stubs and spies to assert you sent outgoing messages.
* Use a Fake to stub requests to external services.
* Use integration tests to execute the entire app.
* Use non-SUT methods in expectations when possible.
