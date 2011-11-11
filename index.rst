.. include:: <s5defs.txt>

==============================
JavaScript, the Functional Way
==============================

:Author:  Andrew Montalenti
:Date:    $Date: 2011-10-23 09:00:00 -0500 (Tues, 23 Oct) $

.. This document is copyright Andrew Montalenti and Parsely, Inc.

.. container:: handout

    **How this was made**

    This document was created using Docutils_/reStructuredText_ and S5_.

    This presentation has been used as an introduction to JavaScript for existing
    programmers, but is also an exploration of what makes the JavaScript language
    good and not so good. I have used it to bring skilled backend programmers (Python,
    Java, C) up-to-speed on the latest thinking in the JS community. It also includes
    some materials about Node.JS, since Node has provided a great environment for writing
    production-quality JavaScript code in a non-browser context.

    Simplicity begets elegance.

.. _Docutils: http://docutils.sourceforge.net/
.. _reStructuredText: http://docutils.sourceforge.net/rst.html
.. _S5: http://meyerweb.com/eric/tools/s5/

Meta Information
----------------

**Me**: I've been using JavaScript for 10 years. I primarily use Python and JavaScript full-time, and have for the last 3 years. I'm the founder/principal at `Aleph Point`_, an agile software engineering consulting and training firm. I'm co-founder/CTO of Parse.ly_, a tech startup in the digital media space.

**E-mail me**: andrew@parsely.com

**Follow me on Twitter**: amontalenti_

**Connect on LinkedIn**: http://linkedin.com/in/andrewmontalenti

.. _Aleph Point: http://alephpoint.com
.. _Parse.ly: http://parsely.com
.. _amontalenti: http://twitter.com/amontalenti

Baby Turtles
------------

Use your powers wisely, and always remember...

.. image:: img/babyturtles.png
    :align: center

Magic Turtles!
--------------

It's turtles all the way down!

.. image:: img/magicturtle.jpg
    :align: center

Writing Real Programs... with JavaScript!?
------------------------------------------

This was the original name of this talk.

The "!?" was because, when I was starting out in programming, no one considered JavaScript
a "real" programming language. The truth is, though, that people had the same feelings
toward Python back then, and how wrong they were.

I have come to realize in the last 2 years that JavaScript is, quite simply, the most
important programming language to know right now. Ignore and deride it at your own peril.

The Beast with Two Backs
------------------------

JS is a cool programming language!

.. class:: incremental

        * Functional
        * Weakly and dynamically typed
        * Function scope and closure
        * Has a >99% desktop install base (no kidding!)

JS is not a real programming language!

.. class:: incremental

        * No compilation units, modules and namespaces
        * No classes or object-orientation built-in
        * No standard library (no kidding!)
        * Incoherent implementation standard

JS boring details in one slide
------------------------------

.. class:: incremental

        Number: double-precision 64-bit IEEE 754, e.g. 0 or 0.5
        String: stream of 16-bit Unicode characters, e.g. “hello, world!”
        Boolean: true or false
        object: {a: b} - like Python dictionary + attribute (dot notation) syntax
                Function: function() {}
                Array: [a, b] – implemented as hash, includes length property
                Date: supports basic date/time representation and parsing from strings
                RegExp: created using /regex/ syntax; efficient RegEx impl
        Null: null - deliberate non-value
        Undefined: undefined  - uninitialized value

.. class:: small

        no I/O – object literals – common C-style if, for, switch/case, while statements – uncommon C-style do/while, tertiary statement, and short-circuiting – var keyword – string concatenation and splicing – prototype chain – toString – type coercion – truthy and falsy – triple-equals (===) vs. double-equals (==) – typeof (broken!)

What makes JavaScript cool?
---------------------------

Like Python, JavaScript is a small language. It fits in your head.

Like Python, JavaScript is multi-paradigm, but has even more support for functional
programming than Python.

JavaScript's functional core allows you to build powerful primitives easily, but unlike
Python, batteries are not included.

Our first example
-----------------

Our first example is a map/reduce implementation written with JS functions.

.. class:: incremental

        we build an iterator function called each which is found in most JS frameworks
        we implement map and reduce using each
        we implement a test function that maps pow2 function (x*x) to each element in a list, and then reduces it via addition.

End result is equivalent to the following Python: sum(x*x for x in items)

The iterator function: each
---------------------------

.. sourcecode:: javascript

        function each(items, fn) {
                for (var i = 0; i < items.length; i++) {
                        var item = items[i];
                        fn.apply(item, []);
                }
        };

