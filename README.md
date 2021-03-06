# Haml

[![Gem Version](http://img.shields.io/gem/v/haml.svg)](http://rubygems.org/gems/haml)
[![Build Status](http://img.shields.io/travis/haml/haml.svg)](http://travis-ci.org/haml/haml)
[![Code Climate](http://img.shields.io/codeclimate/github/haml/haml.svg)](https://codeclimate.com/github/haml/haml)
[![Coverage Status](http://img.shields.io/coveralls/haml/haml.svg)](https://coveralls.io/r/haml/haml)
[![Inline docs](http://inch-pages.github.io/github/haml/haml.png)](http://inch-pages.github.io/github/haml/haml)

Haml is a templating engine for HTML. It's designed to make it both easier and
more pleasant to write HTML documents, by eliminating redundancy, reflecting the
underlying structure that the document represents, and providing an elegant syntax
that's both powerful and easy to understand.

## Basic Usage

Haml can be used from the command line or as part of a Ruby web framework. The
first step is to install the gem:

~~~sh
gem install haml
~~~

After you write some Haml, you can run

~~~sh
haml document.haml
~~~

to compile it to HTML. For more information on these commands, check out

~~~sh
haml --help
~~~

To use Haml programatically, check out the [YARD documentation](http://haml.info/docs/yardoc/).

## Using Haml with Rails

To use Haml with Rails, simply add Haml to your Gemfile and run `bundle`.

~~~ruby
gem 'haml'
~~~

Haml 4.1 requires an actively maintained version of Rails (version 3.2 or later).
If you are using Rails 3.0 or 3.1, you should use Haml version 4.0.x:

~~~ruby
gem 'haml', '~> 4.0.5'
~~~

If you'd like to replace Rails's Erb-based generators with Haml, add
[haml-rails](https://github.com/indirect/haml-rails) to your Gemfile as well.

## Formatting

The most basic element of Haml is a shorthand for creating HTML:

~~~haml
%tagname{:attr1 => 'value1', :attr2 => 'value2'} Contents
~~~

No end-tag is needed; Haml handles that automatically. If you prefer HTML-style
attributes, you can also use:

~~~haml
%tagname(attr1='value1' attr2='value2') Contents
~~~

Adding `class` and `id` attributes is even easier. Haml uses the same syntax as
the CSS that styles the document:

~~~haml
%tagname#id.class
~~~

In fact, when you're using the `<div>` tag, it becomes _even easier_. Because
`<div>` is such a common element, a tag without a name defaults to a div. So

~~~haml
#foo Hello!
~~~

becomes

~~~html
<div id='foo'>Hello!</div>
~~~

Haml uses indentation to bring the individual elements to represent the HTML
structure. A tag's children are indented beneath than the parent tag. Again, a
closing tag is automatically added. For example:

~~~haml
%ul
  %li Salt
  %li Pepper
~~~

becomes:

~~~html
<ul>
  <li>Salt</li>
  <li>Pepper</li>
</ul>
~~~

You can also put plain text as a child of an element:

~~~haml
%p
  Hello,
  World!
~~~

It's also possible to embed Ruby code into Haml documents. An equals sign, `=`,
will output the result of the code. A hyphen, `-`, will run the code but not
output the result. You can even use control statements like `if` and `while`:

~~~haml
%p
  Date/Time:
  - now = DateTime.now
  %strong= now
  - if now > DateTime.parse("December 31, 2006")
    = "Happy new " + "year!"
~~~

Haml provides far more tools than those presented here. Check out the [reference
documentation](http://haml.info/docs/yardoc/file.REFERENCE.html)
for full details.

### Indentation

Haml's indentation can be made up of one or more tabs or spaces. However,
indentation must be consistent within a given document. Hard tabs and spaces
can't be mixed, and the same number of tabs or spaces must be used throughout.

## Contributing

Contributions are welcomed, but before you get started please read the
[guidelines](http://haml.info/development.html#contributing).

After forking and then cloning the repo locally, install Bundler and then use it
to install the development gem dependencies:
~~~sh
gem install bundler
bundle install
~~~

Once this is complete, you should be able to run the test suite:
~~~sh
rake
~~~

You'll get a warning that you need to install haml-spec, so run this:

~~~sh
git submodule update --init
~~~

At this point `rake` should run without error or warning and you are ready to
start working on your patch!

Note that you can also run just one test out of the test suite if you're working
on a specific area:

~~~sh
ruby -Itest test/helper_test.rb -n test_buffer_access
~~~

Haml supports Ruby 1.9.2 and higher, so please make sure your changes run on
both 1.9 and 2.0.

## Team

### Current Maintainers

* [Norman Clarke](http://github.com/norman)
* [Matt Wildig](http://github.com/mattwildig)
* [Akira Matsuda](https://github.com/amatsuda)
* [Tee Parham](https://github.com/teeparham)

### Alumni

Haml was created by [Hampton Catlin](http://hamptoncatlin.com), the author of
the original implementation. Hampton is no longer involved in day-to-day coding,
but still consults on language issues.

[Nathan Weizenbaum](http://nex-3.com) was for many years the primary developer
and architect of the "modern" Ruby implementation of Haml.

## License

Some of Nathan's work on Haml was supported by Unspace Interactive.

Beyond that, the implementation is licensed under the MIT License.

Copyright (c) 2006-2013 Hampton Catlin, Nathan Weizenbaum and the Haml team

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
