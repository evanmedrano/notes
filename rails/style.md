Rails
=====
* Avoid member and collection routes.
* Use private instead of protected when defining controller methods.
* Name date columns with `_on` suffixes.
* Name datetime columns with `_at` suffixes.
* Name time columns (referring to a time of day with no date) with `_time` suffixes.
* Name initializers for their gem name.
* Order ActiveRecord associations alphabetically by association type, then attribute name.
* Order ActiveRecord validations alphabetically by attribute name.
* Order ActiveRecord associations above ActiveRecord validations.
* Order controller contents: filters, public methods, private methods.
* Order i18n translations alphabetically by key name.
* Order model contents: constants, macros, public methods, private methods.
* Put application-wide partials in the app/views/application directory.
* Use def self.method, not the scope :method DSL.
* Use the default render 'partial' syntax over render partial: 'partial'.
* Use link_to for GET requests, and button_to for other HTTP verbs.
* Use new-style validates :name, presence: true validations, and put all validations for a given column together.

Routes
------
* Avoid the :except option in routes.
* Order resourceful routes alphabetically by name.
* Use the :only option to explicitly state exposed routes.
