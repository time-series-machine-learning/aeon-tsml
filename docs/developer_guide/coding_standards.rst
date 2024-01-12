.. _coding_standards:

================
Coding standards
================


Coding style
============

In coding, we follow:

*  the `PEP8 <https://pep8.org/>`__ and `aeon` specific coding guidelines. A good example can be found in .

* code formatting according to ``black``, ``flake8``, ``isort``, ``numpydoc``

Code formatting and linting
---------------------------

We adhere to the following code formatting standards:

* `black <https://black.readthedocs.io/en/stable/>`__ with default settings and a line length of 88 characters

* `flake8 <https://flake8.pycqa.org/en/latest/>`__ with default settings

* ``isort`` with default settings and a line length of 88 characters

* ``numpydoc`` to enforce numpy `docstring standard <https://numpydoc.readthedocs.io/en/latest/format.html#docstring-standard>`_

This is enforced through our CI/CD workflows via `pre-commit <https://pre-commit.com/>`_.



``aeon`` specific code formatting conventions
-----------------------------------------------

-  For naming conventions, use underscores to separate words in non-class names, e.g., ``n_instances`` rather than ``ninstances``. Exceptionally, capital letters like ``X``, ``Y``, ``Z``, are permissible as variable names or part of variable names, such as ``X_train``, if referring to data sets. Avoid multiple statements on one line and use absolute imports for references inside aeon.
-  Use underscores to separate words in non-class names: ``n_instances``
   rather than ``ninstances``.
-  exceptionally, capital letters ``X``, ``Y``, ``Z``, are permissible as variable names
   or part of variable names such as ``X_train`` if referring to data sets, in accordance
   with the PEP8 convention that such variable names are permissible if in prior use in an area
   Remove outdated or irrelevant information.
-  
   
-  
-  Don’t use ``import *`` in the source code. It is considered
   harmful by the official Python recommendations. It makes the code
   harder to read as the origin of symbols is no longer explicitly
   referenced, but most important, it prevents using a static analysis
   tool like pyflakes to automatically find bugs.

Setting up local code quality checks
------------------------------------

There are two options to set up local code quality checks:

* using ``pre-commit`` for automated code formatting
* setting up ``black``, ``flake8``, ``isort`` and/or ``numpydoc`` manually in a local dev IDE

Using pre-commit for automated code formatting to enforce code formatting and linting standards
^^^^^^^^^^^^^^^^

To set up pre-commit, follow these steps in a python environment
with the ``aeon`` ``dev`` dependencies installed.

Type the below in your python environment, and in the root of your local repository clone:

1. If not already done, ensure ``aeon`` with ``dev`` dependencies is installed, this includes ``pre-commit``:

.. code:: bash

   pip install -e .[dev]

2. Set up pre-commit:

.. code:: bash

   pre-commit install

Once installed, pre-commit will automatically run all ``aeon`` code quality
checks on the files you changed whenever you make a new commit.

You can find our pre-commit configuration in
`.pre-commit-config.yaml <https://github.com/aeon-toolkit/aeon/blob/main/.pre-commit-config.yaml>`_.
Additional configurations can be found in
`setup.cfg <https://github.com/aeon-toolkit/aeon/blob/main/setup.cfg>`_.

.. note::
   If you want to exclude some line of code from being checked, you can add a ``# noqa`` (no quality assurance) comment at the end of that line.

Integrating code formatting and linting standards with your local developer IDE
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Local developer IDEs will usually integrate with common code quality checks, but need setting them up in IDE specific ways.

For Visual Studio Code, ``black``, ``flake8``, ``isort`` and/or ``numpydoc`` will need to be activated individually in the preferences
(e.g., search for ``black`` and check the box). The packages ``black`` etc will need to be installed in the python environment used by the IDE,
this can be achieved by an install of ``aeon`` with ``dev`` dependencies.

Visual Studio Code preferences also allow setting of parameters such as ``max_line_length=88`` for ``flake8``.

In Visual Studio Code, we also recommend to add ``"editor.ruler": 88`` to your local ``settings.json`` to display the max line length.

API design: Feedback is welcome
============

The general design approach of aeon is described in the
paper `“Designing Machine Learning Toolboxes: Concepts, Principles and
Patterns” <https://arxiv.org/abs/2101.04938>`__.

.. note::

   Feedback and improvement suggestions are very welcome!
