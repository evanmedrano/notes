Rails notes
===========

2020-02-11
----------
* Utilize PORO and Service objects within my code, don't need to rely only on the controllers and models that are associated with Active Record objects
* Stick with RESTful routes if possible
* Be smart with Active Record callbacks (avoid triggering methods that don't need to be triggered)
* Think about making a Signup object in place of using nested_attributes_for (include ActiveModel::Model) -- by using the module,
  we get access to validations and adhere to form objects need to have a model name (need to create your own uniqueness validator with
  this approach and error message placement can be an issue. But pros outweigh the cons

2020-02-12
----------
* Have a bin setup script (job is to get a Rails app up and running)
* Create a rake task for development seed data
* Watch out for comments (don't comment out code and avoid using TODO comments)
* Prefer the exception raising varience over silent failing (such as save!)
* Don't use instance variables in partials
