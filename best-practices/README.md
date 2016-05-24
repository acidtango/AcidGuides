Best Practices
==============

Here we present some guidelines that should be taken into consideration when
writing any piece of software in Acid Tango.

Most of these best practices are taken from [Thoughtbot's best practices]

[Thoughtbot's best practices]: https://github.com/thoughtbot/guides/tree/master/best-practices#best-practices


General
-------

* Don't duplicate the functionality of a built-in library.
* Keep the code simple.

Git
===

[Git methodology]

[Git methodology]: https://github.com/acidtango/acid_guides/tree/master/best-practices/git

Object-Oriented Design
======================

* Avoid global variables.
* Avoid long parameter lists.
* Limit collaborators of an object (entities an object depends on).
* Limit an object's dependencies (entities that depend on an object).
* Prefer composition over inheritance.
* Prefer small methods. Between one and five lines is best.
* Prefer small classes with a single, well-defined responsibility. When a class
  exceeds 100 lines, it may be doing too many things.
* Tell, don't ask.

Ruby
====

* Avoid optional parameters. Does the method do too much?
* Avoid monkey-patching.
* Generate necessary Bundler binstubs for the project, such as rake and rspec,
  and add them to version control.
* Prefer classes to modules when designing functionality that is shared by
  multiple models.
* Prefer `private` when indicating scope. Use `protected` only with comparison
  methods like `def ==(other)`, `def <(other)`, and `def >(other)`.

Exceptions
----------

* Exceptions should be exceptional.

Ruby Gems
---------

* Declare dependencies in the `<PROJECT_NAME>.gemspec` file.
* Reference the `gemspec` in the `Gemfile`.
* Use [Appraisal] to test the gem against multiple versions of gem dependencies
  (such as Rails in a Rails engine).
* Use [Travis CI] for Continuous Integration, indicators showing whether GitHub
  pull requests can be merged, and to test against multiple Ruby versions.

Rails
=====

General
-------

* Specify the Ruby version to be used on the project in the Gemfile.
* Generate necessary [Spring binstubs] for the project, such as `rake` and
  `rspec`, and add them to version control.
* Use the [`.ruby-version`] file convention to specify the Ruby version and
  patch level for a project.
* Use `_url` suffixes for named routes in mailer views and [redirects]. Use
  `_path` suffixes for named routes everywhere else.
* Use `db/seeds.rb` for data that is required in all environments.
* Use `db:populate` rake task for development environment seed data.
* Prefer `cookies.signed` over `cookies` to prevent tampering.
* Prefer `Time.current` over `Time.now`
* Prefer `Date.current` over `Date.today`
* Prefer `Time.zone.parse("2014-07-04 16:05:37")` over `Time.parse("2014-07-04 16:05:37")`
* Use `ENV.fetch` for environment variables instead of `ENV[]`so that unset
  environment variables are detected on deploy.

Models
------

* Avoid bypassing validations with methods like save(validate: false),
  update_attribute, and toggle.
* Avoid naming methods after database columns in the same class.
* Don't change a migration after it has been merged into master if the desired
  change can be solved with another migration.
* Keep `db/schema.rb` or `db/development_structure.sql` under version control.
* Don't return false from ActiveModel callbacks, but instead raise
  an exception.
* If there are default values, set them in migrations.
* Don't use SQL or SQL fragments (where('inviter_id IS NOT NULL')) outside
  of models.
* Use SQL, not ActiveRecord models, in migrations.
* Validate the associated belongs_to object (user), not the database
  column (user_id).

Controllers
-----------

* Avoid instantiating more than one object in controllers.

Views
-----

* Use only one instance variable in each view.
* Don't reference a model class directly from a view.
* Don't use instance variables in partials. Pass local variables to partials
  from view templates.

Testing
-------

* Avoid any_instance in rspec-mocks and mocha. Prefer dependency injection.
* Avoid its, let, let!, specify, and before in RSpec.
* Avoid using subject explicitly inside of an RSpec it block. Example.
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

Postgres
========

* Avoid multicolumn indexes in Postgres. It combines multiple indexes
  efficiently. Optimize later with a compound index if needed.
* Consider a partial index for queries on booleans.
* Constrain most columns as NOT NULL.
* Index foreign keys.

Background Jobs
===============

* Store IDs, not ActiveRecord objects for cleaner serialization, then re-find
  the ActiveRecord object in the perform method.

Email
=====

* Use SendGrid or Amazon SES to deliver email in staging and production
  environments.
* Use a tool like MailView to look at each created or updated mailer view
  before merging.

JavaScript
==========

* Use CoffeeScript.

General design guidelines
=========================

* We don't use Lorem Ipsum placeholder texts, in order to avoid confusion,
  lack of attention to the details and possible unwanted text upload to
  production. We'll provide some text that resembles the final content lengths
  and rythm, where real words can capture attention to the reader in the same
  way a real paragraph would do.

HTML
====

* Don't use a reset button for forms.
* Prefer cancel links to cancel buttons.
* Use `<button>` tags over `<a>` tags for actions.

Sass
====

* Prefer `overflow: auto` to `overflow: scroll`, because `scroll` will always
  display scrollbars outside of OS X, even when content fits in the container.
* Use `image-url` and `font-url`, not `url`.
* Avoid `@extend`.

Browsers
========

* Don't support clients without Javascript.
* Don't support IE6, IE7 or IE8.

Accessibility
=============

* Make sure everything works with a keyboard.
* Mark up forms semantically.
* Provide plenty of contrast.
* Ensure that screen readers know what your controls do.
* Test the websites on an actual screen reader.

[Why care?]

[Why care?]: http://www.smashingmagazine.com/2014/05/21/mobile-accessibility-why-care-what-can-you-do/
