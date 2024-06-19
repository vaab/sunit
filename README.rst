=====
SUnit
=====

Shell Unit Test - Quick and Dirty


Feature
=======

- Quick way to write unit test in shell

- Fancy ANSI colors printings

- Carefull attention to profiling test (saving times of tests runs, comparisons)

- Dirty means there's no real limit to the tinkering you might want
  to introduce around the very few syntax token proposed by sunit.

- Slim because it has no dependencies to other project, one file, in bash

- Faint doctest feeling


Current Status
==============

Early Alpha:
- no documentation
- basic syntax/command line usage might change drastically in the future
- no test of the current testing system
- not completely happy with metrics and diffing, scales might change as
  some outputs.
- No proper github releases


Installation
============

No installation method provided, just copy the file in your path.


Usage
=====


QuickStart
----------

Create a directory to store test files::

    $ cat <<EOF > foo   ## First test file

    try 'echo -n "hello world"'
      noerror
      is out "hello world"

    EOF

Note that indentation is not required before ``noerror`` and ``is out``.

``noerror`` and ``is`` are bash functions. ``noerror`` a shortcut for
2 ``is`` commands: ``is errlvl 0`` and ``is err ""``.

All assertions are managed through the ``is`` bash functions. Basic
syntax of ``is`` function is::

    is {errlvl,err,out} [COMPARISON_METHOD] VALUE [OUTCOME_MODIFIERS...]

For instance, here::

    is out "hello world"

Checks if standard output of last ``try`` command was exactly ``hello
world``.

Let's run the test::

    $ sunit foo
    - foo_1                                    3 asserts         [  -.001 s ]
    3 assertions passed. Code took .003 s (-6.9 dB).


Command line
------------

TBD

Syntax token
------------


    try CODE [MESSAGE]
    is {errlvl,err,out} [COMPARISON_METHOD] VALUE [OUTCOME_MODIFIERS...]


Contributing
============

Any suggestions or issues are welcome. Push requests are very welcome,
please check out the guidelines.


Push Request Guidelines
-----------------------

You can send any code. I'll look at it and will integrate it myself in
the code base and leave you as the author. This process can take time and
it'll take less time if you follow the following guidelines:

- Try to stick to 80 columns wide.
- separate your commits per smallest concern.
- each commit should pass the tests (to allow easy bisect)
- each functionality/bugfix commit should contain the code, tests,
  and doc.
- prior minor commit with typographic or code cosmetic changes are
  very welcome. These should be tagged in their commit summary with
  ``!minor``.
- the commit message should follow gitchangelog rules (check the git
  log to get examples)
- if the commit fixes an issue or finished the implementation of a
  feature, please mention it in the summary.

If you have some questions about guidelines which is not answered here,
please check the current ``git log``, you might find previous commit that
shows you how to deal with your issue.


License
=======

Copyright (c) 2012-2019 Valentin Lab.

Licensed under the `BSD License`_.

.. _BSD License: http://raw.github.com/0k/sunit/master/LICENSE
