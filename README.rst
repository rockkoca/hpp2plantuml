hpp2plantuml - Convert C++ header files to PlantUML
===================================================

.. _sec-intro:

Motivation
----------

The purpose of this tool is to convert C++ header files to a UML representation
in `PlantUML <https://plantuml.com>`_ syntax that can be used to generate diagrams with PlantUML.

`PlantUML <https://plantuml.com>`_ is a program rendering UML diagrams from plain text inputs using an
expressive language.

This module generates the text input to PlantUML from C++ header files.  Its
ambition is limited but it should produce reasonable conversion for simple class
hierarchies.  It aims at supporting:

- class members with properties (``private``, ``method``, ``protected``), methods with
  basic qualifiers (``static``, abstract),

- inheritance relationships,

- aggregation relationships (very basic support).


.. _sec-module-usage:

Usage
-----

The ``hpp2plantuml`` package can be used from the command line or as a module in
other applications.

Command line
~~~~~~~~~~~~

The command line usage is (``hpp2plantuml --help``):


::

    usage: hpp2plantuml [-h] [-o FILE] -i HEADER-FILE

    hpp2plantuml tool.

    optional arguments:
      -h, --help            show this help message and exit
      -o FILE, --output-file FILE
                            Output file
      -i HEADER-FILE, --input-file HEADER-FILE
                            Input file (must be quoted when using wildcards)


Input files are added using the ``-i`` option.  Inputs can be file paths or
include wildcards.  Note that the double quotes are required when using
wildcards.  The output file is selected with the ``-o`` option.  The output is a
text file following the PlantUML syntax.

For instance, the following command will generate the input file for PlantUML
from several header files and store the output to the ``output.puml`` file.

.. code-block:: sh
    :name: usage-sh

    hpp2plantuml -i File_1.hpp -i "include/Helper_*.hpp" -o output.puml

Module
~~~~~~

To use as a module, simply ``import hpp2plantuml``.  The ``CreatePlantUMLFile`` can
then be used to create a PlantUML file from a set of input files.
Alternatively, the ``Diagram`` object can be used directly to build internal
objects (from files or strings).  The ``Diagram.render()`` method can be used to
produce a string output instead of writing to a text file.


The full documentation is located at:

- `Org-mode post <https://thibaultmarin.github.io/blog/posts/2016-11-30-hpp2plantuml_-_Convert_C++_header_files_to_PlantUML.html>`_
- `Read the docs <http://hpp2plantuml.readthedocs.io/en/latest/>`_
