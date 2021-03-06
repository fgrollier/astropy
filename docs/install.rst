************
Installation
************

Requirements
============

Astropy has the following strict requirements:

- `Python <http://www.python.org/>`_ 2.6, 2.7, 3.1 or 3.2

- `Numpy <http://www.numpy.org/>`_ 1.4 or later

Astropy also depends on other projects for optional features.

- `scipy <http://www.scipy.org/>`_: To power a variety of features.
- `xmllint <http://www.xmlsoft.org/>`_: To validate VOTABLE XML files.

.. TODO: Link to the planned dependency checker/installer tool.

Installing Astropy
==================

Using `pip`
-----------

To install Astropy with `pip`, simply run::

    pip install astropy

Binary installers
-----------------

No binary installers are available at this time.


Testing Astropy
---------------

The easiest way to test your installed version of astropy is running
correctly is to use the :func:`astropy.test` function::

    import astropy
    astropy.test()

The tests should run and print out any failures, which you can report at
the `Astropy issue tracker <http://github.com/astropy/astropy/issues>`_.


Building from source
====================

Prerequisites
-------------

You will need a compiler suite and the development headers for Python
and Numpy in order to build Astropy.  Using the package manager for
your platform will usually be the easiest route.

The `instructions for building Numpy from source
<http://docs.scipy.org/doc/numpy/user/install.html>`_ are also a good
resource for setting up your environment to build Python packages.

Obtaining the source packages
-----------------------------

Source packages
^^^^^^^^^^^^^^^

Source tarballs of past releases and the current development branch of
astropy can be downloaded from https://github.com/astropy/astropy/downloads

Development repository
^^^^^^^^^^^^^^^^^^^^^^

The latest development version of Astropy can be cloned from github
using this command::

   git clone git://github.com/astropy/astropy.git

.. note::

   If you wish to participate in the development of Astropy, see
   :ref:`developer-docs`.  This document covers only the basics
   necessary to install Astropy.

Building and Installing
-----------------------

Astropy uses the Python `distutils framework
<http://docs.python.org/install/index.html>`_ for building and
installing.

To build Astropy (from the root of the source tree)::

    python setup.py build

To install Astropy (from the root of the source tree)::

    python setup.py install

External C libraries
^^^^^^^^^^^^^^^^^^^^

The Astropy source ships with the C source code of a number of
libraries.  By default, these internal copies are used to build
Astropy.  However, if you wish to use the system-wide installation of
one of those libraries, you can pass one or more of the
`--use-system-X` flags to the `setup.py build` command.

For example, to build Astropy using the system `libexpat`, use::

    python setup.py build --use-system-expat

To build using all of the system libraries, use::

    python setup.py build --use-system-libraries

To see which system libraries Astropy knows how to build against, use::

    python setup.py build --help

As with all distutils commandline options, they may also be provided
in a `setup.cfg` in the same directory as `setup.py`.  For example, to
use the system `libexpat`, add the following to the `setup.cfg` file::

    [build]
    use_system_expat=1

.. _builddocs:

Building documentation
----------------------

.. note::
    Building the documentation is in general not necessary unless you
    are writing new documentation or do not have internet access, because
    the latest (and archive) versions of astropy's documentation should
    be available at `docs.astropy.org <http://docs.astropy.org>`_ .

Building the documentation requires the Astropy source code and some additional
packages:

    - `Sphinx <http://sphinx.pocoo.org>`_ (and its dependencies) 1.0 or later

    - `Graphviz <http://www.graphviz.org>`_

There are two ways to build the Astropy documentation. The most straightforward
way is to execute the command (from the astropy source directory)::

    python setup.py build_sphinx

The documentation will be built in the ``docs/_build/html`` directory, and can
be read by pointing a web browser to ``docs/_build/html/index.html``.

The above method builds the API documentation from the source code.
Alternatively, you can do::

    cd docs
    make html

And the documentation will be generated in the same location, but using the
*installed* version of Astropy.

Testing your Astropy build
--------------------------

The easiest way to test that your Astropy built correctly (without
installing astropy) is to run this from the root of the source tree::

    python setup.py test

There are also alternative methods of :ref:`running-tests`.
