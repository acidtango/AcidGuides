Class Vs ID
===========

What do we use them for?

- ID:
  - Javascript selectable elements.
  - Navigable sections (anchors)
- Class:
  - Styling

Important: `Don't use ID's for style!`.

Reference:
[Why class over id?]

[Why class over id?]: http://screwlewse.com/2010/07/dont-use-id-selectors-in-css/

Assets folder structure
=======================

/app/assets/stylesheets

- name_of_the_web/
  - name_of_layout/ -> As many folders as needed per layout
    - \_base-scss -> Each layout has a base styles file (if needed)
    - \_some_section_styles.scss -> Styles for a specific section or part
      of the web
  - configuration/
    - \_config_partial.scss -> Configuration partials such as
      \_breakpoints.scss, \_typography.scss...
  - \_common_base.scss
  - \_partial.scss -> Basic common partials such as \_notifications.scss,
    \_print.scss...
- lib/ -> acid tango libraries
- vendor/ -> External css files
- \_base_imports.scss
- application.scss

CSS file structure
==================

Initial comment
---------------

// -------------------------------------------------------  
//  
// This file is ... and ...  
//  
// -------------------------------------------------------  
Imports
-------
Variables
---------
Base HTML styles (h1, body...)
------------------------------
Global styles (.container-main)
-------------------------------
Rest of styles (.msg-alert)
---------------------------

All the logical sections should be separated by a comment like so:

// -------------------------------------------------------  

* Use the HTML structure for choosing the spot where to put the selectors. Don't
  just put styles at the bottom of the file.
* Files should not be longer than 100-150 lines.

Selector structure
==================

Follow this order:
* `@extends` and `@includes`.
* Attributes. The order should resemble (as a general guideline):
selector {  
  POSITIONING LINE [position,top,left,clear, ETC]  
  BOX MODEL LINE [display,margin,border,padding,width, ETC]  
  TYPOGRAPHY LINE [font,text-indent,font-style, ETC]  
  PREFIXED PROPERTIES [-moz-,-webkit-, ETC]  
}  
* Media queries.
* Pseudo elements.
* States and concatenated classes.
* Nested HTML selectors.
* Nested classes.

Comments
========

* Add an initial comment to describe the file and what it is for.
* Use `//` for comment blocks not `/* */`.

General
=======

* Use **SCSS** (not SASS) syntax.
* Use **rem** as the default unit. px is allowed when specific sizes are
  required.
* Separate selectors with a single line.
* Don't add more than one attribute per line, and always start the attribute
  definition in the line below the selector line. An exception can be made when
  there is only one attribute, in which case the selector +  attribute can be
  written in one line.
* Use double quotation marks.
* Use one space between property and value (width: 20px not width:20px).
* Don't add unit after 0 values (width: 0, not width: 0px).
* Use one space between selector and {.
* Use a leading zero in decimal numbers (0.5 not .5).
* Use space around operands ($variable * 1.5, not $variable*1.5)
* Avoid the extra amount of values when writing attributes in compact
  form (padding: 1rem 0 0; instead of padding: 1rem 0 0 0;)
* Use parentheses when including operations in attributes ( padding:
  ($variable * 1.5) ($variable * 2) ).
* When testing or doing some refactoring, add the new elements with no
  indentation. Indent them when it's clear that it's valid and should belong
  to the selector.
selector {  
  test-attribute: value;  
  regular-attribute: value;  
}  

Naming
======

- Use **meaningful names** ($visual-grid-color not $color or $vslgrd-clr).
- Abbreviations can only be used in these cases:
  - msg (message)
  - btn (button)
  - col (column)
- Try to be concise but write names as long as necessary.
- Don't use HTML tag names or too specific attributes in the class
  name (section.news not section.news-section or section.news-blue-background).
- All names in **lowercase**.
- Separate names using hyphens for mixins, extends, classes and
  functions: container-main (not container_main or containerMain).
- Use underscore \_ for variable names: $blue_color instead of $blue-color.

Efficiency and structure
========================

* Avoid using the direct descendant selector >.
* Avoid nesting more than 4 selectors deep.
* Don't nest more than 6 selectors deep.
* Avoid nesting within a media query.
* Avoid using HTML tags on classes for generic markup (.widgets not div.widgets).

External Libraries
==================

* Instead of a reset file, we use [Normalize]
* Use [Bourbon] for a Sass library.
* Use [Neat] for a grid framework.

[Normalize]: https://github.com/necolas/normalize.css
[Bourbon]:http://bourbon.io/
[Neat]: http://neat.bourbon.io/

Example
=======

// -------------------------------------------------------  
//  
// Base styles for the admin section  
//  
// -------------------------------------------------------  

@import import_file;  

// HTML base styles  
// -------------------------------------------------------  

body {  
  attribute: value;  
}  

// -------------------------------------------------------  

container-main {  
  @extend %extend;  
  @include mixin;  
  attribute: value;  

  @include media(...) {  
    attribute: value;  
  }  

  &:hover {  
    attribute: value;  
  }  

  &::before {  
    content: '<';  
  }  

  &::after {  
    content: '>';  
  }  

  &.additional-selector {  
    attribute: value;  
  }  

  &.open { attribute: value; }  

  .nested-class {  
    attribute: value;  
    attribute: ($variable * 1.5) 2em;  

    article {  
      attribute: value;  

      p { attribute: value; }  
    }  
  }  
}  
