General formatting
==================

* Lines should be no longer than 80 characters.
* Use 2 spaces for indentation, no tabs (see [Sublime text 2 indentation options]).

[Sublime text 2 indentation]: https://www.sublimetext.com/docs/2/indentation.html

Spacing
-------

* There should be no trailing whitespaces.
* Don't include spaces after (, [ or before ], ).
* Include spaces around { and before }.
* Space between two methods should be an empty line.
* Space should be used after a comma, after colons and semicolons.

Naming
------

* Be as clear and semantic as possible. Reveal intent.
* Tend not to abbreviate.
* Don't use object types in names (user_array, password_hash...).
* Acronyms are treated as regular words, not written in uppercase
  (XmlHttpRequest instead of XMLHTTPRequest).

Development
===========

Ruby
----

* We'll follow the general [Ruby style guidelines]
* When breaking a chain of method calls, leave the dot at the end of the line.

   very_long_method.
    another_long_method.
    last_one

* Indent private methods equal to public methods.
* Caller methods should be earlier in the file than the methods they call.
* Write methods as close as possible to other methods they call.

[Ruby style guidelines]: https://github.com/bbatsov/ruby-style-guide

Rails
-----

...

Git
---

* Prefix feature branch names with your initials. This is specially useful when
  using utilities such as [Gitsh] autocomplete.
* Squash multiple trivial commits into a single commit.
* Commit message should resemble:

[Gitsh]: https://github.com/thoughtbot/gitsh

Example:

Capitalized, short (50 chars or less) summary

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Write your commit message in the imperative: `"`Fix bug`"` and not `"`Fixed bug`"`
or `"`Fixes bug.`"`. This convention matches up with commit messages generated
by commands like git merge and git revert.

Further paragraphs come after blank lines.

- Bullet points are okay, too
- Typically a hyphen or asterisk is used for the bullet, followed by a
  single space, with blank lines in between, but conventions vary here
- Use a hanging indent

Taken from [here].

[here]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html

Javascript
----------
...

SQL
---

* Write SQL key words in upper case and names in lower case. &lt;code&gt;UPDATE my_table SET a = 5;&lt;/code&gt;

Design
======

Sass
----

[Sass style guide]

[Sass style guide]: https://github.com/acidtango/acid_guides/best-practices/sass/

HTML
----
* Use double quotes
* Use Slim
