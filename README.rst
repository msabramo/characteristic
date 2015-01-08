characteristic: Python attributes without boilerplate.
======================================================

.. image:: https://pypip.in/version/characteristic/badge.svg
   :target: https://pypi.python.org/pypi/characteristic/
   :alt: Latest Version

.. image:: https://travis-ci.org/hynek/characteristic.svg
   :target: https://travis-ci.org/hynek/characteristic
   :alt: CI status

.. image:: https://coveralls.io/repos/hynek/characteristic/badge.png?branch=master
   :target: https://coveralls.io/r/hynek/characteristic?branch=master
   :alt: Current coverage


Teaser
------

.. code-block:: pycon

   >>> from characteristic import Attribute, attributes
   >>> @attributes(["a", "b"])
   ... class AClass(object):
   ...     pass
   >>> @attributes(["a", Attribute("b", default_value="abc", instance_of=str)])
   ... class AnotherClass(object):
   ...     pass
   >>> obj1 = AClass(a=1, b="abc")
   >>> obj2 = AnotherClass(a=1, b="abc")
   >>> obj3 = AnotherClass(a=1)
   >>> AnotherClass(a=1, b=42)
   Traceback (most recent call last):
    ...
   TypeError: Attribute 'b' must be an instance of 'str'.
   >>> print obj1, obj2, obj3
   <AClass(a=1, b='abc')> <AnotherClass(a=1, b='abc')> <AnotherClass(a=1, b='abc')>
   >>> obj1 == obj2
   False
   >>> obj2 == obj3
   True


.. begin


``characteristic`` is an `MIT <http://choosealicense.com/licenses/mit/>`_-licensed Python package with class decorators that ease the chores of implementing the most common attribute-related object protocols.

You just specify the attributes to work with and ``characteristic`` gives you any or all of:

- a nice human-readable ``__repr__``,
- a complete set of comparison methods,
- immutability for attributes,
- and a kwargs-based initializer (that cooperates with your existing one and optionally even checks the types of the arguments)

*without* writing dull boilerplate code again and again.

This gives you the power to use actual classes with actual types in your code instead of confusing ``tuple``\ s or confusingly behaving ``namedtuple``\ s.

So put down that type-less data structures and welcome some class into your life!

``characteristic``\ ’s documentation lives at `Read the Docs <https://characteristic.readthedocs.org/>`_, the code on `GitHub <https://github.com/hynek/characteristic>`_.
It’s rigorously tested on Python 2.6, 2.7, 3.3+, and PyPy.
