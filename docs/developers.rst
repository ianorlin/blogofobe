.. _ForDevelopers-section:

For Developers
==============

If you would like to contribute to the blogofobe project,
these instructions should help you get started.
Patches, documentation improvements, bug reports, and feature requests
are all welcome through the GitHub projects:

* `blogofobe on GitHub`_
* `blogofobe_blog on GitHub`_

Contributions in the form of patches or pull requests are easier to integrate
and will receive priority attention.

.. _blogofobe on GitHub: https://github.com/wxl/blogofobe
.. _blogofobe_blog on GitHub: https://github.com/wxl/blogofobe_blog


Python Versions
---------------

blogofobe is developed under Python_ 3.2
and tested with Python 2.6, 2.7, 3.2, and 3.3.

.. _Python: http://www.python.org/


.. _SettingUpADevelopmentSandbox-section:

Setting Up a Development Sandbox
--------------------------------

Using a Python virtualenv_ is strongly recommended to segregate
blogofobe and the packages it depends on from your system Python
installation.

.. _virtualenv: http://www.virtualenv.org/

Create a virtualenv and activate it::

  $ virtualenv blogofobe-dev
  $ source blogofobe-dev/bin/activate

Grab the blogofobe core,
and the blogofobe_blog reference plugin repos from GitHub::

  (blogofobe-dev)$ cd blogofobe-dev
  (blogofobe-dev)$ git clone git://github.com/wxl/blogofobe.git
  (blogofobe-dev)$ git clone git://github.com/wxl/blogofobe_blog.git

Install the packages for development,
and install the extra packages that are used to build the docs
and run the test suite::

  (blogofobe-dev)$ pip install -e blogofobe
  (blogofobe-dev)$ pip install -e blogofobe_blog
  (blogofobe-dev)$ pip install -r blogofobe/requirements/develop.txt


Building Documentation
----------------------

The blogofobe docs are written with reStructuredText_ markup
and built using Sphinx_.
Sphinx and its dependencies are installed  as part of the
`development sandbox setup <SettingUpADevelopmentSandbox-section>`_.

.. _reStructuredText: http://docutils.sourceforge.net/rst.html
.. _Sphinx: http://sphinx.pocoo.org/

The :file:`blogofobe/docs/` directory includes a :file:`Makefile` to help
build the docs::

  (blogofobe-dev)$ (cd blogofobe/docs && make html)
  sphinx-build -b html -d _build/doctrees  . _build/html
  Making output directory...
  Running Sphinx v1.1.3
  loading pickled environment... not yet created
  building [html]: targets for 12 source files that are out of date
  updating environment: 12 added, 0 changed, 0 removed
  reading sources... [100%] vcs_integration
  looking for now-outdated files... none found
  pickling environment... done
  checking consistency... done
  preparing documents... done
  writing output... [100%] vcs_integration
  writing additional files... genindex search
  copying static files... done
  dumping search index... done
  dumping object inventory... done
  build succeeded.

  Build finished. The HTML pages are in _build/html.

The output version of the docs ends up in :file:`blogofobe/docs/build/html`
in your development sandbox.


Running Tests
-------------

The test suites for blogofobe and blogofobe_blog use tox_.
Tox and its dependencies are installed as part of the
`development sandbox setup <SettingUpADevelopmentSandbox-section>`_.

.. _tox: http://tox.testrun.org/

To run the tests under Python 2.6, 2.7, and 3.2,
run :command:`tox` in the top level :file:`blogofobe/`
and :file:`blogofobe_blog/` directories.

To run tests under a single version of Python, specify the appropriate
environment when running tox::

  $ tox -e py27

Add new tests by modifying an existing file or adding a new one in the
:file:`blogofobe/tests/` and :file:`blogofobe_blog/tests/` directories.


Releases
--------

blogofobe and blogofobe_blog releases are hosted on PyPI and can be
downloaded from:

* http://pypi.python.org/pypi/blogofobe
* http://pypi.python.org/pypi/blogofobe_blog


Source Code
-----------

The source repositories are hosted on GitHub:

* https://github.com/wxl/blogofobe
* https://github.com/wxl/blogofobe_blog


Reporting Bugs
--------------

Please report bugs through the GitHub projects:

* https://github.com/wxl/blogofobe/issues
* https://github.com/wxl/blogofobe_blog/issues
