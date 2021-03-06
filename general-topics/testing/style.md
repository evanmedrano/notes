Testing Style Guide
===================
* Avoid the private keyword in specs.
* Avoid checking boolean equality directly. Instead, write predicate
  methods and use appropriate matchers.
* Prefer eq to == in RSpec.
* Separate setup, exercise, verification, and teardown phases with
  newlines.
* Use RSpec's expect syntax.
* Use RSpec's allow syntax for method stubs.
* Use not_to instead of to_not in RSpec expectations.
* Prefer the have_css matcher to the have_selector matcher in Capybara
  assertions.

Acceptance Tests
----------------
* Avoid scenario titles that add no information, such as "successfully."
* Avoid scenario titles that repeat the feature title.
* Place helper methods for feature specs directly in a top-level Features module.
* Use Capybara's feature/scenario DSL.
* Use names like ROLE_ACTION_spec.rb, such as user_changes_password_spec.rb, for feature spec file names.
* Use only one feature block per feature spec file.
* Use scenario titles that describe the success and failure paths.
* Use spec/features directory to store feature specs.
* Use spec/support/features for support code related to feature specs.

Unit Tests
----------
* Don't prefix it block descriptions with should. Use Imperative mood instead.
* Use subject blocks to define objects for use in one-line specs.
* Put one-liner specs at the beginning of the outer describe blocks.
* Use .method to describe class methods and #method to describe instance methods.
* Use context to describe testing preconditions.
* Use describe '#method_name' to group tests by method-under-test
* Use a single, top-level describe ClassName block.
* Order validation, association, and method tests in the same order that they appear in the class.

Factories
---------
* Order factories.rb contents: sequences, traits, factory definitions.
* Order factory attributes: implicit attributes, explicit attributes, child factory definitions. Each section's attributes are alphabetical.
* Order factory definitions alphabetically by factory name.
* Use one factories.rb file per project.
