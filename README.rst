.. image:: https://github.com/agronholm/typeguard/actions/workflows/test.yml/badge.svg
  :target: https://github.com/agronholm/typeguard/actions/workflows/test.yml
  :alt: Build Status
.. image:: https://coveralls.io/repos/agronholm/typeguard/badge.svg?branch=master&service=github
  :target: https://coveralls.io/github/agronholm/typeguard?branch=master
  :alt: Code Coverage
.. image:: https://readthedocs.org/projects/typeguard/badge/?version=latest
  :target: https://typeguard.readthedocs.io/en/latest/?badge=latest
  :alt: Documentation

This library provides run-time type checking for functions defined with
`PEP 484 <https://www.python.org/dev/peps/pep-0484/>`_ argument (and return) type
annotations, and any arbitrary objects. It can be used together with static type
checkers as an additional layer of type safety, to catch type violations that could only
be detected at run time.

Four principal ways to do type checking are provided, each with its pros and cons:

#. The ``check_type`` function:

   * like ``isinstance()``, but supports arbitrary type annotations (within limits)
   * can be used as a ``cast()`` replacement, but with actual checking of the value
#. the ``check_argument_types()`` and ``check_return_type()`` functions:

   * debugger friendly (except when running with the pydev debugger with the C extension installed)
   * does not work reliably with dynamically defined type hints (e.g. in nested functions)
#. the ``@typechecked`` decorator:

   * automatically type checks yields and sends of returned generators (regular and async)
   * adds an extra frame to the call stack for every call to a decorated function
#. the import hook (``typeguard.importhook.install_import_hook()``):

   * automatically annotates classes and functions with ``@typechecked`` on import
   * no code changes required in target modules
   * requires imports of modules you need to check to be deferred until after the import hook has
     been installed
   * may clash with other import hooks

See the documentation_ for further information.

.. _documentation: https://typeguard.readthedocs.io/en/latest/
